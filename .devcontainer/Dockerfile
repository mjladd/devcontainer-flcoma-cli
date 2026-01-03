# Force x86-64 platform since FluCoMa CLI only provides Linux x64 binaries
FROM --platform=linux/amd64 ubuntu:24.04

# Avoid interactive prompts during package installation
ENV DEBIAN_FRONTEND=noninteractive

# Install dependencies, zsh, and git
RUN apt-get update && apt-get install -y \
    curl \
    ca-certificates \
    libsndfile1 \
    zsh \
    git \
    && rm -rf /var/lib/apt/lists/*

# Download and install FluCoMa CLI
RUN curl -L https://github.com/flucoma/flucoma-cli/releases/download/1.0.9/FluCoMa-CLI-Linux-x64.tar.gz -o /tmp/flucoma-cli.tar.gz \
    && mkdir -p /tmp/flucoma-extract \
    && tar -xzf /tmp/flucoma-cli.tar.gz -C /tmp/flucoma-extract \
    && mkdir -p /usr/local/bin/flucoma-cli \
    && mv /tmp/flucoma-extract/*/* /usr/local/bin/flucoma-cli/ 2>/dev/null \
    || mv /tmp/flucoma-extract/* /usr/local/bin/flucoma-cli/ \
    && rm -rf /tmp/flucoma-cli.tar.gz /tmp/flucoma-extract \
    && chmod +x /usr/local/bin/flucoma-cli/*

# Add FluCoMa CLI to PATH
ENV PATH="/usr/local/bin/flucoma-cli/bin:${PATH}"

# Create workspace directory for mounted files
RUN mkdir -p /workspace

WORKDIR /workspace

# Install Oh My Zsh (OMZ) unattended for root user and configure plugins
ENV SHELL=/usr/bin/zsh
ENV ZSH=/root/.oh-my-zsh
RUN sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)" --unattended \
    && git clone --depth=1 https://github.com/zsh-users/zsh-syntax-highlighting.git $ZSH/custom/plugins/zsh-syntax-highlighting \
    && sed -i 's/^plugins=.*/plugins=(git zsh-syntax-highlighting)/' /root/.zshrc \
    && echo '\n# Ensure syntax highlighting loads last' >> /root/.zshrc \
    && echo 'source $ZSH/custom/plugins/zsh-syntax-highlighting/zsh-syntax-highlighting.zsh' >> /root/.zshrc
