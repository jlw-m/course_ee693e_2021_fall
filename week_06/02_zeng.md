---
title: "02: FullBreathe: Full Human Respiration Detection Exploiting Complementarity of CSI Phase and Amplitude of WiFi Signals
Y. ZENG, D. WU, R. GAO, T. GU, D. ZHANG,"
date: 2021-09-29
type: book
commentable: true
# Provide the name of the presenter
summary: "Presenter(s): Clyde James Felix, Jeanalyn Wadsack-Myers, Nguyen Banh"
# Provide other tags that describe the paper
tags:
- teaching
- ee693e
- WiFi
- Respiration sensing
---
***
## Paper Summary
Wireless human respiration detection using WiFi signals has a great potential in the telemedicine field. This research tackles the wireless sensing problem by investigating the properties of amplitude and phase information on WiFi signals. The discovery of the phase and amplitude complementarity property is used to solve the blind spot problem. This paper also evaluates the complementarity in the respiration sensing application. The result of the experimentations shows that the complementarity property still holds in different factors such as environmental changes, and transceiver distance. 
***
## Presentation
{{< youtube zNiE1SjCCWM >}}
***
## Review
### Strengths
- Can detect wireless measurements in undetectable regions.
- Accurate measurements in different environments.

### Weaknesses
- This application is only for one subject.
- This application might not be accurate when the subject is moving.
- Subject must be facing the transceivers for accurate measurements.

### Detailed Comments
Respiratory diseases are responsible for 7% of all deaths worldwide (4.2 million deaths). Device-free respiration monitoring eliminates the need for the user to wear any device. This method typically employs camera, acoustic, and radio frequency (RF) devices to detect respiration in a contactless manner. The Fresnel zone (FZ) theory is being used to reveal radio wave propagation in WiFi. This theoretical model perfectly explains the performance fluctuation in existing systems and demonstrates that human respiration cannot be effectively sensed when one remains in WiFi blindspot locations.

This is the first study to use WiFi devices to achieve this goal. They demonstrate how to use the complementarity property to detect respiration in full-coverage WiFi devices that are not synchronized. The paper also discusses the most recent work in RF respiration sensing. WiFi-based approaches can be classified into two types. These systems are primarily based on signal pattern periodicity. They are still baffled as to why human respiration would result in different, even irregular, Doppler radar waveforms.

To overcome this problem, use multiple transceiver pairs to improve the ability to capture human respiration and overlapped Fresnel zones. In an indoor environment, the received signal strength is the superposition of all path components.

The superposition of components from all the paths a radio wave takes is referred to as CSI. They investigate how to combine CSI phase and amplitude information to detect complete respiration. The CSI phase is primarily determined by sin, and the CSI phase waveform is sinusoidal-like.

The metal plate moves 5mm back and forth regularly, recording the CSI data. A waveform is considered detectable for respiration if it is a (co)sinusoidal-like waveform with clear periodic patterns that correspond to the ground truth. As long as they can obtain accurate CSI, the CSI phase and amplitude complementarity can be used to build a respiration detection system. MIMO technology is used to extend the complementarity property to standard WiFi. Extend the Complementarity to the WiFi Commodity.

The time-varying random phase offsets on a WiFi card are the same across all antennas. They recover them by performing conjugate multiplication (CM) of CSI between two antennas to remove time-varying random phase offsets. Because the two nearby antennas have a similar reflection path, the change in reflection path length can be seen as the same during respiration.

The raw CSI data collected via WiFi is not time-synchronized. To obtain smooth and precise input data, data denoising is required. To smooth the data, they employ the Savitzky-Golay filter. The amplitude of CM is chosen using our selection algorithm. The peak identification method is sensitive to unsmoothed waveforms, and its performance suffers significantly if fake peaks are included in the peak-to-peak time interval calculation.

A peak is deemed fake if it does not have the highest value compared to all of its neighbor samples within a 1.5-second verification window. They use the artificial peak removal algorithm to remove all of the false peaks from the peak candidates.

FullBreathe necessitates the use of one WiFi transmitter and one receiver. As transceivers, they use GIGABYTE mini-PCs outfitted with off-the-shelf Intel 5300 wireless NIC cards. The WiFi is set to operate at a frequency of 5.745 GHz. The antennas are attached to the tripods and moved. They conduct a series of experiments at each location to ensure that the phase and amplitude complement each other for full respiration sensing.

They present the experimental results using the detectability ratio metric rather than the detailed waveforms for brevity. The detectability ratio is NdetectableNal l, where NDetectable is the number of CSI measurements collected, and Nall is the total number of CSI measurements collected. In 24% of CSI measurements, the amplitude of one antenna fails to extract the respiration rate.

However, if both the phase and amplitude of CM are used, all CSI measurements are detectable. The detectability ratio of phase/amplitude varies by Los. In the previous experiment, they investigated the impact of environmental changes on the complementarity property with WiFi by moving static objects in the environment. Our method outperforms existing WiFi-based methods that use either the amplitude of one antenna or the phase difference between two RX antennas, and it has excellent real-world deployment potential. The sensing range of a WiFi-based respiration system is determined by various factors, including transmitting power, the gain of a transmitter and receiver antenna, and the subject orientation.

They can identify the two streams to determine subjects by leveraging the WiFi CSI phase and amplitude nature. During respiration detection, the system requires the issue to remain still. FullBreathe fails to detect respiration from WiFi signals because significant body movement affects chest movement the most. The limitation is caused by multipath effects caused by other body parts.

### Implementation
There were two cases of Fresnel zones tested for respiration sensing in order to verify complementarity: near region and far region. The setup consisted of the two transceivers with 150cm separation, the use of a WARP platform as a programmable wireless platform, and a metal plate mounted onto a high precision THK programmable linear motion slider meant to mimic chest displacement. Each artificial breath corresponded to a 5 mm displacement of the metal plate. For both cases, many data points were taken in 0.5 mm increments throughout a set moving range.
The observations from this experimental setup were as expected and displayed alternating detectable and undetectable regions. The only difference between cases was the size of the detectable/undetectable regions due to the nature of Fresnel zones becoming smaller as the distance from the transceivers increases. In each position, amplitude, phase, or both signals were detectable at any given moment.


### Experimentation
 {{< figure src="https://github.com/gustybear-teaching/course_ee693e_2021_fall/week_06/images/zeng-experiment1.jpg" title="Experiment Setup." width="300" >}}
 {{< figure src="https://github.com/gustybear-teaching/course_ee693e_2021_fall/week_06/images/zeng-experiment2.jpg" title="Experiment Positions to test." width="300" >}}
 {{< figure src="https://github.com/gustybear-teaching/course_ee693e_2021_fall/week_06/images/zeng-UI.jpg" title="FullBreathe Web UI." width="300" >}}
 {{< figure src="https://github.com/gustybear-teaching/course_ee693e_2021_fall/week_06/images/zeng-results.jpg" title="Amplitude and Phase signals in different antenna positions." width="300" >}}
 {{< figure src="https://github.com/gustybear-teaching/course_ee693e_2021_fall/week_06/images/zeng-LoSresults.jpg" title="Impact of different Line of Sight between tranceivers." width="300" >}}
 {{< figure src="https://github.com/gustybear-teaching/course_ee693e_2021_fall/week_06/images/zeng-envresults.jpg" title="Impact of different environments." width="300" >}}
 {{< figure src="https://github.com/gustybear-teaching/course_ee693e_2021_fall/week_06/images/zeng-fridgeresults.jpg" title="Impact of different environmental changes." width="300" >}}

### Dicussions
Based on the FullBreathe research results, the complementarity property between the phase and the amplitude still holds when the tranceiver LoS is varied, the rooms are changed, and there was an environmental changes. This indicates that any of these factors is not a problem when detecting respiration measurements. However, several limitations are discussed on the paper. Since this proposal is for one subject, it is likely to not work for multiple subjects. But, there are possible solutions to tackle this problem, which is out of the scope of this paper. Another limitation is the subject orientation when detecting the measurements. This expirement only worked accurately when the subject is facing forward. One possible solutions to this problem is to add another tranceiver to the room in order so sense the person's respisrations in different angles. 


### Questions
(1) Can you elaborate the reason why subject location and environmental changes does not affect the complimentary of CSI phase and amplitude?

A subject's location affects both the magnitude and phase of the dynamic component so as long as the subject is within sensing range, the magnitude will be larger than zero and detectable. As for the antenna displacement and room layout, they affect the distribution of the multi-paths, which change the static component. Both changes of static and dynamic components only affect the selection between phase and amplitude for respiration sensing but not their complementarity.
 
(2) Is there any possible way to increase/improve the respiratory sensing range? 

The respiratory sensing rage is very accurate if the subject is facing in front of the tranceivers, staying still, and in the detectable sensing range.

(3) Is there a limit on the number of subjects that can use this application at a time?

The papers states that the research is only for one subject only. Although, there are possible ways to make this work for multiple subjects.
