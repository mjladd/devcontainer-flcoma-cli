# Force x86-64 platform since FluCoMa CLI only provides Linux x64 binaries
FROM --platform=linux/amd64 ubuntu:24.04

# Avoid interactive prompts during package installation
ENV DEBIAN_FRONTEND=noninteractive

# Install dependencies
RUN apt-get update && apt-get install -y \
    curl \
    ca-certificates \
    libsndfile1 \
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
