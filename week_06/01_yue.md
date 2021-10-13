---
title: "01: Extracting Multi-Person Respiration from Entagnled RF Signals
Shichao Yue, Hao He, Hao Wang, Hariharan Rahul, Dina Katabi"
date: 2021-09-27
type: book
commentable: true

# Provide the name of the presenter
summary: "Presenter(s): Saige Dacuycuy, Tasmia Tahmid, Beemnet Alemayehu"

# Provide other tags that describe the paper
tags:
- teaching
- ee693e

---

***
## Paper Summary
This paper presents a novel RF-based respiration monitoring system named “DeepBreath” capable of recovering the breathing signals of multiple individuals positioned with zero distance. Past works were not able to recover breathing signals when individuals are very close to each other. With DeepBreath, respiration monitoring during sleep can be useful to diagnose sleep disorders, sleep disturbed breathing (SDB), cardiac arrest, sleep apnea etc. RF signals have been used to track a person’s respiration allowing to track the sleep quality and stages of a subject and monitor sleep apnea and other sleep disordered breathing without any body contact.  The design of DeepBreath combines three components: (a) Breathing  Separation, (b) Motion Detection and (c) Identity Matching. A breathing separation module is being used in DeepBreath to reconstruct the correct breathing signals of multiple co-located individuals. The reliability of the motion detection is ensured through a convolutional neural network trained to identify movements of the monitored persons. The paper reported an average precision of 0.933 for motion detection. This approach of extracting Multi-Person Respiration from entangled RF signal can attribute each signal to the source subject with very high accuracy and precision, and the distance and position of the subjects does not affect the data quality.

***

## Presentation
{{< youtube SUjzoFbPyME >}}

***

## Review
### Strengths
- All previous studies demonstrate accurate monitoring of a single person’s breathing but this paper focuses on multiple persons breathing with sucessful experimentation results. 
- Average error in breating rate detection is very small (0.140 breaths per minute). 
- DeepBreath can be scaled for more than two people and the accuracy does not decrease with the number of people.
- System design can apply to different applications beside respiration monitoring.

### Weaknesses
- The illustrative example used in the paper generates a false positive result as the Fourier transform is applied over a finite window it creats a sinc in the frequency domain and causes nearby signals to mix with each other due to the sinc tail. 
- The current system cannot model objects in motion for example typing or the simultaneous motion of two hands.
- The mixing matrix is pretty much dependent on time, which is very difficult to determine from visual observations.
- Breathing separation trial was done for 5 mins. No further study is being conducted to verify that the system/setup would give same results if the trial lasted longer than 5 minutes. 

### Detailed Comments
The paper provides an explanation into how the authors separate the mixtures of RF breathing signals and focuses on multiple persons breathing with sucessful experimentation results. The concept of Independent Component Analysis (ICA) helps us recognize signals from multiple sources, analyze the mixture, and split the signals apart. The goal of ICA is to recover the sources and the mixing matrix given only the observations. The proposed "DeepBreath" has some novel features like it can be scaled for more than two people and the accuracy does not decrease with the number of people. The average error in breating rate detection is 0.140 breaths per minute which is quite small. The system design can be applied to different applications beside respiration monitoring.

In simplicity, the RF signals reflect off people's bodies add up linearly over the wireless medium. However, there is a fundamental challenge when using this technique, and it's due to the fact that the mixing matrix is not the same at every time instance. The problem that the authors faced is that the RF signals are reflected off each person's torso. The mixtures of the reflections are received by the antennas and the mixing coefficients is dependent on the wireless channels of the torso of each person to each antenna. This could be sensitive because as a person breathes, their torso moves and the channels change and the mixing coefficients are no longer constant. This means that the mixing matrix is pretty much dependent on time, which is very difficult to determine from visual observations. Likewise, the illustrative example used in the paper generated a false positive result as the fourier transform is applied over a finite window created a sinc in the frequency domain and caused nearby signals to mix with each other due to the sinc tail. With some pros and cons the paper opens the door for further research on contactless multi-person sleep studies. 

### Implementation

The RF reflections are analyzed via a Frequency-Modulated Carrier Waves (FMCW) radio. FMCW transmits a sequence of sweeps. The transmitted signal changes linearly with time during each sweep. As shown in the first figure under experimentation section, the linear change of the transmitted signal is shown in red. Once the signal is reflected off the human body, it is given as a time-shifted blue signal. In this case, it also compares the frequency difference between the transmitted signal and received signal.

To alleviate the problems from before, the authors considered small linear motions involved with the breathing and substract the mean across time for each frequency, then they recover the individual breathing motions of all the sources. The authors used a full night breathing reconstruction system called Deepbreath, that can accurately monitor multiple people even when they are in the same bed. Deepbreath runs on top of an FMCW radio with an antenna and captures the reflected signals of each person throughout an entire night observation. It does so by a three-step process:

a) Motion Detection: The motion detection components takes in input observations, identifies motion intervals, and splits the observations in a series of stable periods. The idea is to detect the motion of a single individual and ignore other motions.

b) Breathing Separation: The breathing signals of different people during is stable period is distangled using this module and during that period it generates the output containing the reconstructed breathing signals. After motion detection, ICA is applied to each period and the breathing reconstructions is obtained. To make this work, the authors allowed multiple paths for the signal since it is related linearly to the breathing motion, and they considered the short periodicity of human breathing.

c) Identity Matching: Identity matching is required as the breathing separation module is not aware or capable of automatically recognize who each reconstructed signal belongs to. So the authors compare ICA components from each period and go through consistency metric to see which ICA components corresponds to which person. The goal is to have an ICA component having the same order in all stable periods such that it gives the breathing of the same person.

The authors solved the signal blockage problem using a well-known phenomenon called multipath. To filter the noisy observations a term Long term Breathing-to-Noise Ratio (l-BNR) is defined and identified. If the l-BNR value is low, it indicates the possibility of the observation containing useful breathing information is low and hence it is not necessary to exclude such observations in recovering breathing signals.

### Experimentation

{{< figure src="https://github.com/gustybear-teaching/course_ee693e_2021_fall/raw/main/week_06/images/FMCW.png" title="" width="300" >}}

{{< figure src="https://github.com/gustybear-teaching/course_ee693e_2021_fall/raw/main/week_06/images/Fig11_Yue.png" title="Performance comparison between DeepBreath and an oracle-based baseline" width="320" >}}
The authors compare the performance of DeepBreath with a baseline that uses an oracle to iterate over all voxels in the bed area. For each person, the oracle zooms in on the voxel that results in more accurate breathing signals. 

{{< figure src="https://github.com/gustybear-teaching/course_ee693e_2021_fall/raw/main/week_06/images/Fig12_Yue.png" title="Examples of recovered breathing signals and the original ground truth signals from the breathing belt" width="320" >}}
In this figure, DeepBreath is capable of separating respiration signals from couples even when the breathing patterns look similar. 

{{< figure src="https://github.com/gustybear-teaching/course_ee693e_2021_fall/raw/main/week_06/images/Fig15_Yue.png" title="Obersvations of five subjects and a comparison between reconstructed signals and ground truth" width="320" >}}
The authors shows DeepBreath's performance by observing the voxels centered on each of the five subjects. Each observation is a different mixture of the breathing signals. The authors also do a comparison of DeepBreath's reconstructed signal and compare it to the ground truth, showing the system's degree of accuracy.


### Discussion

Ground truth measurement is established by strapping a belt around the chest and using the change in chest volume to get breathing signal. This ground truth will serve as the standard in which we compare DeepBreath’s performance against. To establish a contextual understanding of this comparison, a belt strapped to the diaphragm was compared to a belt strapped to the chest. In an ideal world the correlation would have been one (as we would expect DeepBreath’s correlation to be as well), but the data showed a correlation of 0.915. This sets the standard for DeepBreath to match. 

Thirteen couples participated in the study. Each couple were assigned near subject and far subject identification based on their distance from the sensor. To measure the ground truth, everyone wore a chest belt. During the data collection, the motion detector was used to remove periods of motion and only operated on stable periods. Data analysis showed, on average, 11% of a night exhibits motion which agrees with medical literature.

Data collected over 21 nights to measure the identity matching of DeepBreath has an average accuracy of 99.1% and all subjects had an accuracy of above 95%. The breathing separation of multiple people with minimum distance between them was measured using five people sitting on a couch shoulder-to-shoulder. There were 8 different people who participated in different combinations of five subjects. Each trial lasted five minutes and the correlation between DeepBreath’s signal and the ground truth had an average of 0.922. 

The evaluation results show that DeepBreath recover the breathing of each individual correctly when in close proximity/sharing the same bed. The Evaluation of Identity Matching confirms the robustness of their identity matching algorithm  as the total averaged accuracy is 99.1% . The Evaluation of Motion Detection with a precision of 0.933 confirms that their motion detector can successfully detect motion. In case of Breathing Rate Separation, they achieved 0.922 correlation with 0.034 breathing rate error with respect to the ground truth breathing signals demonstrating that DeepBreath can reconstruct the breathing of at least 5 people even when there is no distance between them.

### Audience Questions

1. Can multiple reflections be made to reach the person without too much noise?

For wireless settings, the multiple reflections caused by different angles matters. We believe that manipulating the environment can create artificial reflections. In previous presentation(s), there was a manipulation of moving metal plates to simulate chest displacement, so we assume that the multiple paths can be made. 

2. Are there any security risks in gathering data from this technology?

The source data (subject’s breathing) is available in the open out there without any privacy. So, any party with an antenna can pick up these breathing signals and use the similar model to get the information. However, we are not sure if this lies under privacy issue or security because the weak point here is before the data collection. This vulnerability exists before the system is used or even implemented.
	
3. What is the cost of the FMCW system in comparison to a WIFI system?

The cost of such systems would be somewhere between $100 - $1000. It depends on the application and implementation, but in regards to radar systems, WIFI has a relatively narrow bandwidth compared to the tailor-made transmissions in FMCW. So right now, WIFI can still be cheaper. However, we believe that with the recent advances in low-cost FMCW technology for example Software Defined Radio, it is possible that FMCW can be cheaper than WIFI in the application of multipath reflections.

4. What is the system's performance when dealing with moving objects?

The authors futher research proposes to disentangle other types of motion, e.g., typing, or the simultaneous motion of two hands etc. apart from breathing separation. The current system is designed focusing on separating mixure of signals positioned in zero distance and thus moving objects might are hard to model in the existing system. The Inddependent Component Analysis (ICA) cannot separate and identify the signals off an object in motion.

5. There was an experiment with 5 individuals and DeepBreath could reconstruct the breathing of each subject. Do you believe the system could function effectively with a fan near the subject?

Yes, the systems could effectively fuctioned with a fan near the subject because DeepBreath uses a convolutional neural network to detect motion reliably  and the system is capable of identifing movements of the monitored people and ignore all irrelevant motion of a fan or the HVAC for example.
