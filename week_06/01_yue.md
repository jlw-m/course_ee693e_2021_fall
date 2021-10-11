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
RF signals have been used to track a person’s respiration allowing us to track the sleep quality and stages of a subject and monitor sleep apnea and other sleep disordered breathing without any body contact. However, this approach as is cannot be easily integrated into people’s daily lives because it does not work when other people are present in the vicinity of the subject (which is almost all the time). In this paper, a solution is presented where the multiple RF signal interference is modeled, and independent component analysis (ICA) is used to recover individual signals. The proposed method can attribute each signal to the source subject with very high accuracy and precision, and the distance and position of the subjects does not affect the data quality.
***

## Presentation
{{< youtube SUjzoFbPyME >}}

***

## Review
### Strengths
- Accuracy does not decrease with the number of people.
- System design can apply to different applications beside respiration monitoring.

### Weaknesses
- Cannot model objects in motion.

### Detailed Comments
The paper provides an explanation into how the authors separate the mixtures of RF breathing signals. The concept of Independent Component Analysis (ICA) helps us recognize signals from multiple sources, analyze the mixture, and split the signals apart. The goal of ICA is to recover the sources and the mixing matrix given only the observations. In simplicity, the RF signals reflect off people's bodies add up linearly over the wireless medium. However, there is a fundamental challenge when using this technique, and it's due to the fact that the mixing matrix is not the same at every time instance. 

The problem that the author's have is that the RF signals are reflected off each person's torso. The mixtures of the reflections are recieved by the antennas and the mixing coefficients is dependent on the wireless channels of the torso of each person to each antenna. There is a sensitive matter. Once a person breathes, their torso moves and the channels change and the mixing coefficients are no longer constant. This means that the mixing matrix is pretty much dependent on time, which is very difficult to determine from your observations.

### Implementation

So the RF reflections are analyzed via a Frequency-Modulated Carrier Waves (FMCW) radio. FMCW transmits a sequence of sweeps, and during each sweep, the frequency of the transmitted signal changes linearly with time. As shown below, the linear change of the transmitted signal is shown in red. Once the signal is reflected off the human body, it is given as a time-shifted blue signal. In this case, it also compares the frequency difference between the transmitted signal and received signal.

{{< figure src="https://github.com/gustybear-teaching/course_ee693e_2021_fall/raw/main/week_06/images/FMCW.png" title="" width="300" >}}

To alleviate the problems from before, the authors considered small linear motions involved with the breathing and substract the mean across time for each frequency, then they recover the individual breathing motions of all the sources. 

The authors used Deepbreath, which is the first RF-based full night breathing reconstruction system that can accurately monitor multiple people even when they are in the same bed. Deepbreath runs on top of an FMCW radio with an antenna and captures the reflected signals of each person throughout an entire night observation. It does so by a three-step process:

1) Motion Detection: The motion detection components takes in input observations, identifies motion intervals, and splits the observations in a series of stable periods. The idea is to detect the motion of a single individual and ignore other motions.

2) Breathing Separation: This module processes the observations during each stable period to disentangle the breathing signals of different people. It outputs the reconstructed breathing signals during that period. After motion detection, ICA is applied to each periond and the breathing reconstructions is obtained. To make this work, the authors allowed multiple paths for the signal since it is related linearly to the breathing motion, and they considered the short periodicity of human breathing.

3) Identity Matching: The breathing sepearation module is not aware who each reconstructed signal belongs to. So the authors compare ICA components from each period and go through consistency metric to see which ICA components corresponds to which person. The goal is to have an ICA component having the same order in all stable periods such that it gives the breathing of the same person. 

### Experimentation

{{< figure src="https://github.com/gustybear-teaching/course_ee693e_2021_fall/raw/main/week_02/images/ClicktokTable1.png" title="Table 1: Passive Detection" width="320" >}}
In their experimentation, they consider *stealthy* attackers to be under 5 clicks a day per device, *sparse* to be 5-15 clicks, and *firehose* to be over 15 clicks. From Table 1, it can be seen that Clicktok with a passive defense is effective in identifying click fraud. With a longer ad network duration, leads to better inference, especially against stealth attacks.

{{< figure src="https://github.com/gustybear-teaching/course_ee693e_2021_fall/raw/main/week_02/images/ClicktokTable2.png" title="Table 2: Detection Across Multiple Clickstreams" width="320" >}}
They also categorized and analyzed different click categories, where sponsored are advertisements displayed by search engines, contextual are ads displayed on a webpage based on keywords present in the webpage, and mobile are ads exclusively present on mobile devices. From the results in Table 2, it is shown that the Clicktok is able to identify fraudulent clicks across the ad categories at a high true positive rate of ~90%, and a low false positive rate at around ~0.004%.

{{< figure src="https://github.com/gustybear-teaching/course_ee693e_2021_fall/raw/main/week_02/images/ClicktokTable3.png" title="Table 3: Active Defense" width="320" >}}
When applying the active defense with bait clicks, it can be seen in Table 3, that it improves detection rates. With both the increase in true positive rates, and decrease in false positive rates, show that an active defense may be important in identifying fake clicks.

{{< figure src="https://github.com/gustybear-teaching/course_ee693e_2021_fall/raw/main/week_02/images/ClicktokTable4.png" title="Table 4: Comparation of Clicktok" width="320" >}}
Lastly, Clicktok gives an comparation between their implementation compared to other defenses, with Clicktok providing vastly lower false positive rates comparatively, and similar or better true positive rates.

### Discussion
Ground truth measurement is established by strapping a belt around the chest and using the change in chest volume to get breathing signal. This ground truth will serve as the standard in which we compare DeepBreath’s performance against. To establish a contextual understanding of this comparison, a belt strapped to the diaphragm was compared to a belt strapped to the chest. In an ideal world the correlation would have been one (as we would expect DeepBreath’s correlation to be as well), but the data showed a correlation of 0.915. This sets the standard for DeepBreath to match. 
Thirteen couples participated in the study. Each couple were assigned near subject and far subject identification based on their distance from the sensor. To measure the ground truth, everyone wore a chest belt. During the data collection, the motion detector was used to remove periods of motion and only operated on stable periods. Data analysis showed, on average, 11% of a night exhibits motion which agrees with medical literature.
Data collected over 21 nights to measure the identity matching of DeepBreath has an average accuracy of 99.1% and all subjects had an accuracy of above 95%. The breathing separation of multiple people with minimum distance between them was measure using five people sitting on a couch shoulder-to-shoulder. There were 8 different people who participated in different combinations of five subjects. Each trial lasted five minutes and the correlation between DeepBreath’s signal and the ground truth had an average of 0.922. 

### Audience Questions
1.	Can multiple reflections be made to reach the person without too much noise?

For wireless settings, the multiple reflections caused by different angles matters. We believe that manipulating the environment can create artificial reflections. In previous presentation(s), there was a manipulation of moving metal plates to simulate chest displacement, so we assume that the multiple paths can be made. 

2.	Are there any security risks in gathering data from this technology?

The source data (subject’s breathing) is available in the open out there without any privacy. So, any party with an antenna can pick up these breathing signals and use the similar model to get the information. However, we are not sure if this lies under privacy issue or security because the weak point here is before the data collection. This vulnerability exists before the system is used or even implemented.
	
3.	What is the cost of the FMCW system in comparison to a WIFI system?

It depends on the application and implementation, but in regards to radar systems, WIFI has a relatively narrow bandwidth compared to the tailor-made transmissions in FMCW. So right now, WIFI can still be cheaper. However, we believe that with the recent advances in low-cost FMCW technology, it is possible that FMCW can be cheaper than WIFI in the application of multipath reflections.

4.	 What is the system's performance when dealing with moving objects?

Moving objects are hard to model. ICA, which is the main method this system is based on cannot separate and identify the signals off an object in motion.

5. 	There was an experiment with 5 individuals and DeepBreath could reconstruct the breathing of each subject. Do you believe the system could function effectively with a fan near the subject?

Yes, the fan can be considered like another subject. The system handles interference really well, so having an additional source of signal should not be a problem for the analysis.

