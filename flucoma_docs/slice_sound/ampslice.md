# AmpSlice

Relative value amplitude-based slicing
[Event Detection and Improvisation](/explore/hayes)[Get Started](/learn/getting-started)[Decomposition Overview](/learn/decomposition-overview)[AmpFeature](/reference/ampfeature)[AmpGate](/reference/ampgate)
AmpSlice determines when an amplitude onset has occurred by comparing two amplitude envelope followers on the same audio signal. One envelope follower is “fast” meaning that it responds quickly to changes in amplitude. The other is “slow” meaning that it responds more slowly to changes. AmpSlice compares the difference between the slow and fast envelopes to determine if there has been a relative spike in amplitude in the short term, when compared to the longer term trend. When the difference between the two envelopes goes above the onThreshold, it is identified as an onset.
*relative*`onThreshold`
If you are interested in absolute amplitude-based segmentation then check out AmpGate.
*absolute*[AmpGate](/reference/ampgate)
Both of these envelope followers are smoothed, meaning they don’t respond right away to changes in the signal that they’re following. Both the fast and slow envelope followers can be smoothed independently from one another in AmpSlice allowing you to define “how fast” and “how slow” each one should be. Additionally, each envelope can be smoothed in both directions: “up” (when the sound gets louder) and “down” when the sound gets quieter). The parameters for this are called: fastRampUp, fastRampDown, slowRampUp, and slowRampDown.
*smoothed*`fastRampUp``fastRampDown``slowRampUp``slowRampDown`
With no smoothing it would be essentially impossible to look for relative changes between the two because they are the same. Too much smoothing and the slow envelope will stop responding to changes in amplitude in a meaningful way, thus spoiling the comparison the algorithm makes. Ultimately, working with AmpSlice often comes down to fine-tuning the parameters that dictate the characteristics of the curves and how they respond to your input sound.

Below offers a close look at the two envelope followers (blue is “fast”, orange is “slow”):

![](image_001.jpg)

Drum Loop: 'Nicol-LoopE-M' (sample 352068 to 390016, which is 0.86 seconds), fastRampUp: 8820, fastRampDown: 4410, slowRampUp: 22050, slowRampDown: 26460; (these parameters are exaggerated-larger than they need to be–for visual clarity in the diagrams)

You can see that the curves created by these envelope followers lag behind the actual attack of these drum hits. This is because the envelope followers can’t look into the future to determine when a hit might happen, they can only respond to changes as they develop.

AmpSlice is concerned with the difference between these two envelope followers. The chart below shows a measurement of the difference at a few different moments during the first drum hit (indicated by the I bars).

![](image_002.jpg)

Measuring the difference between the two envelope followers at a few moments in time.

AmpSlice determines the difference between these two envelope curves by subtracting one from the other (fast minus slow) to create a “relative envelope” (the green curve below).

![](image_003.jpg)

Green = relative envelope (the difference between the two)

You can see that the difference between the two envelope followers is greater (the relative envelope is higher) at the beginning of an amplitude onset because the “fast” envelope follower has responded quickly, jumping up to a high amplitude value, while the “slow” envelope follower takes more time to rise up in response to the sudden change.

AmpSlice will indicate that an amplitude onset has occurred when this relative envelope goes above a threshold (indicated by the green horizontal line below). This parameter is called onThreshold.
`onThreshold`
![](image_004.jpg)

When the relative threshold goes above a user-defined threshold, an 'onset' is triggered.

Once an amplitude onset has been detected, AmpSlice must detect the “offset” of this musical moment before it can trigger another onset (a system like this is called a Schmitt Trigger). Similar to how it identifies an onset as when the relative envelope goes above a threshold, an “offset” identified when the relative threshold goes below another threshold (indicated by the red line below). This parameter is called offThreshold.
`offThreshold`
![](image_005.jpg)

Once the relative envelope goes below the 'offThreshold', and 'offset' is identified, allowing AmpSlice to trigger another onset.
