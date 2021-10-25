---
title: "01: Enabling High-Quality Untethered Virtual Reality
Omid Abari, Dinesh Bharadia, Austin Duffield, and Dina Katabi"
date: 2021-10-13
type: book
commentable: true

# Provide the name of the presenter
summary: "Presenter(s): Clyde James Felix, Jeanalyn Wadsack-Myers, Saige Dacuycuy"

# Provide other tags that describe the paper
tags:
- teaching
- ee693e
- Virtual Reality

---

***
## Paper Summary
In a common Virtual Reality (VR) system, a user wears a headset which is connected to a PC, or a game console, via HDMI cable. The VR system requires a high data rate to get the complete experience of the device. There are major challenges to the VR systems. Having an HDMI wiring connectivity limits the user's mobility. A key approach to this problem is using a mmWave, which has an advantage of proving wireless high data rate. However, two major problems of mmWave are mobility problems and blockage problems. This paper tackles the two mmWave problems by proposing a VR system using a mmWave mirror and a tracker algorithm. This solution allows mmWave links to sustain high data rate without mobility and blockage problems.
***

## Presentation
{{< youtube 1Ng4JZSM5qc >}}

***

## Review
### Strengths
- Wireless communication between VR headsets and their game consoles. Users will be able to move freely away from the PC.
- MoVR’s mirror enables high data rate link between VR headset and PC even with blockage.
- Solves mobility problem.

### Weaknesses
- MoVR still fails in certain locations.
- SNR values are depedent on the number of MoVR mirrors.
- Current MoVR headset is powered by USB cable.

### Detailed Comments
Since mmWave provides high data rates for the VR system, it is a good approach to replace wired HDMI connectivity. However, there are two main problems when using mmWave. mmWave provides good data transmission only when the headset is in line of sight (LoS) to the PC, or Access Point (AP). A user's hand covering the LoS path will result in signal attenuation that will not provide good data communication for the VE system. Since the mmWave wavelength is very small, small movements from the user can disrupt the data transmission.

The paper proposes MoVR in which solves the blockage and mobility problems. The blockage problem is solved using a programmable mmWave mirror that is used to control the angles of indidence and reflection. The mobility problem is solved using a beam alignment algorithm to ensure connectivity in different cases. In the MoVR setup, the beam alignments from AP to the mirror, mirror to the headset, and AP to the headset are considered.

While the MoVR solved the main problems of mmWave, there were weaknesses. According to the experimentation, the MoVR does not provide the neccesary Signal to Noise Ratio (SNR) to provide the good data transmission in certain locations. Another weakness is the dependency of the number of mirrors to ensure good SNR values. Lastly, the headset in this system used a USB cable to deliver power that can possibly limit user mobility. 

### Implementation
The authors implemented mmWave wireless link system technology to deliver multi-Gbps communication between headset and console. This type of technology has applications in high data rate wireless communication in fixed systems; however, applying mmWave technology to VR headsets has its challenges. The two main problems the authors sought to address in this paper are blockage and mobility issues. 

A wireless, untethered, and high-quality system called MoVR was proposed to face these challenges. There are two modes MoVR switches between: direct path and MoVR mirror signal transmission. In terms of blockage, MoVR introduces a novel solution using a self-configurable mmWave mirror that detects incoming signals and reconfigures itself towards the headset receiver regardless of its direction. The analog signal is received by the mirror and deflected without any decoding. However, leakage does occur between mirror receiver and transmitter, so an attenuator is added to intercept the leakage and prevent amplifier saturation which is managed via Bluetooth communication between AP and mirror.

Mobility issues are resolved with a tracker algorithm which also takes advantage of the built-in VR headset tracking functions. It is crucial that the best beam alignment is found quickly and accurately to ensure that significant delay does not occur. The VR headset is known to already track the location of the headset via laser tracker. By co-locating the console at the laser location, the authors were able to exploit the information along with RF-based localization to use in their novel algorithm that decides whether to steer the beam in a direct path to the headset or to the MoVR mirror in under a few microseconds. The algorithm considers three types of beam alignments including between the AP and the mirror, between the AP and the headset, and between the mirror and the headset.

### Experimentation
{{< figure src="https://github.com/gustybear-teaching/course_ee693e_2021_fall/raw/main/week_08/images/Abari_Fig1.png" title="Fig. 1: Blockage Duration" width="320" >}}

By calculating the equation of the line between the headset and the base station, any intersection of the user’s hand and the line, i.e. the controller between the LoS path, causes blockage. This figure reflects the scenario of the AP’s line-of-sight to the headset being blocked 20 times during a 5-minute period of the game. This figure shows the cumulative distribution function (CDF), or the cumulative probability over a given blockage duration. 


{{< figure src="https://github.com/gustybear-teaching/course_ee693e_2021_fall/raw/main/week_08/images/Abari_Fig2.png" title="Fig. 2: MoVR’s Mirror Performance" width="320" >}}

Another criteria were given to see how effective MoVR is at dealing with the blockage problem. In this case, the AP is placed on one side of the room while the mirror is placed on an adjacent side. By changing the location of the headset while also changing orientation, three scenarios were performed: no blockage between the AP and headset; blockage between the LoS path; and blockage while using the MoVR mirror.


{{< figure src="https://github.com/gustybear-teaching/course_ee693e_2021_fall/raw/main/week_08/images/Abari_Fig3.png" title="Fig. 3: AP to Mirror Beam Alignment Accuracy" width="320" >}}

This figure reflects how accurate is the beam alignment between the AP and the MoVR mirror. It took 100 runs to measure the best beam alignment while changing the mirror location and orientation each time. Afterwards, an angle was estimated to provide best beam alignment between the mirror and AP.


{{< figure src="https://github.com/gustybear-teaching/course_ee693e_2021_fall/raw/main/week_08/images/Abari_Fig4.png" title="Fig. 4: MoVR Beam Alignment Accuracy" width="320" >}}

This figure shows how accurate is beam alignment for the entire system. Another experiment was performed to see how the MoVR finds the best beam alignment to the headset, which is either from the AP or from the mirror. The headset was placed randomly 40 times and the best signal-to-noise ratio was measured. SNR values were computed for two different scenarios: (1) using the MoVR’s beam alignment algorithm, and (2) the exhaustive search, which gives all combinations for highest SNR.


{{< figure src="https://github.com/gustybear-teaching/course_ee693e_2021_fall/raw/main/week_08/images/Abari_Fig5.png" title="Fig. 5: SNR Values vs Location" width="320" >}}
   

Finally, an experiment was performed such that the MoVR system accounts for the player moving around the room. The headset is moved around the room, but this time, the direct path between the headset and AP is intentionally blocked with the user’s hand. Afterwards, the SNR is calculated and shown in the figures above for three different scenarios: (a)No MoVR mirror, which gives the exhaustive search; a fixed gain mirror, where there is a fixed amplification gain in the setup; and the inclusion of the MoVR. 

### Discussion

When evaluating the blockage between the AP’s line-of-sight to the headset during an actual game, the experiment showed that the line-of-sight was blocked 20 times during a 5-minute game. When looking at Fig. 1 under the Experimentation section, from the 20 times that blockage occurred, the median blockage duration is 245-ms whereas the VR frame rate is only 10-ms. This confirms that blockage occurs very often, and the duration is long enough to affect the VR experience.

In terms of the MoVR’s capabilities to address the blockage problem, we can look at Fig. 2 under the Experimentation section. Fig. 2 shows that without the MoVR mirror, blockage drops the SNR gain by as much as 27 dB, with an average of 17 dB. Thus, relying on indirect reflections in the environment to counter blockage is ineffective.

As for the SNR using the MoVR mirror, in most cases, it showed higher SNR gain over the direct line-of-sight path with no blockage. This means that the AP’s distance to the mirror is shorter than its distance to the headset’s receiver. Thus, the mirror along the path amplifies the signal and counters SNR reduction to the longer distances of the headset. The SNR provided from the MoVR mirror can go as high as 30 dB, which is more than the maximum data rate. Thus, the experiment shows that the MoVR’s mirror gives high data rate link between the VR headset and PC even with blockage on the line-of-sight path.


In Fig. 3 under the Experimentation section, the experiment showed that the MoVR estimates the angle of best beam alignment to within 2 degrees of the actual angle. The authors also reported that such a small error in estimating the angles results in negligible loss in SNR. As for Fig. 4 under the Experimentation section, it is expected that the MoVR performs better than the exhaustive search for best SNR values. For some cases, the experiment showed worst SNR for the MoVR regime, but the SNR value still meets the requirement for the VR headset. The reason exhaustive search is not utilized as much is because this method tries all beam alignments and introduces much latency and overhead. Regarding the beam alignment latency of the MoVR system, it was shown that the total delay between tracking, the beam alignment algorithm, and reconfiguring of the beam takes around 1 millisecond. This delay is low enough to support the VR frame rate.

Finally, it is expected for the SNR to be worse for the case without the mirror since it relies on indirect reflections (Fig. 5(a)). However in Fig. 5(b), which uses the fixed gain mirror, shows that the mirror improves the SNR over relying on these indirect reflections but there are some spots that are below the required 20 dB for the headset. The MoVR mirror, which uses the automatic gain control algorithm, allowed high-quality, untethered virtual reality by providing SNR values higher than 20 dB (Fig. 5(c)).

## Audience Questions

1. Does the environment reflection affect SNR in the mirror? Like having a brick vs wood wall?

Based on prior individual research, since the authors are using millimeter wave or a wave at 24 GHz, there is a limited number of objects/environmental conditions that can create multipaths or reflections. So, whether the environment has a brick or wooden wall, there is little to no environmental reflection that affects the SNR in the mirror.


2. What is the bare minimum number of mirrors needed for the system to completely cover the room?

The number of mirrors needed for the system was not mentioned in the paper, but we can make some assumptions. As the number of mirrors increase, then there is more lenient calibration between the headset and the AP. Depending on the SNR threshold, the AP finds more mirrors to meet the threshold requirement. 

	
3. Do you believe that having multiple receivers on the headset eliminates the need for mirrors?

We believe that having multiple receivers would not solve the blockage problem between the AP and headset’s line-of-sight. It is recommended by the authors that the headset should have multiple antennas. However, if any body parts come between the headset and the AP, then all headset antennas are blocked. Thus, the use of the MoVR mirror is necessary.


4. They conducted the experiment in a 5-m x 5-m room. Do you think it would impact the blockage problems if the room size were different (bigger/smaller)?

The dimensions of the room contribute to how the blockage problem is affected. If we have a room smaller than the experiment, then the MoVR still retains the required SNR values regardless of the headset’s location. If we consider the larger case, a 50-m x 50-m room, then it is possible for the signal to be picked up from the AP and the headset, since mmWave can travel to about one mile. There may be a considerable amount of blockage if the large environment contains more objects than the experiment, which then leads to lower SNR values obtained from the headset. 

