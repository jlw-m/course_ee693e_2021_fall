---
title: "01: Low-Power Wearable ECG Monitoring System for Multiple-Patient Remote Monitoring
Elisa Spanò,Stefano Di Pascoli, and Giuseppe Iannaccone"
date: 2021-09-13
type: book
commentable: true

# Provide the name of the presenter
summary: "Presenter(s): Nguyen Banh, Beemnet Alemayehu, Jeanalyn Wadsack-Myers"

# Provide other tags that describe the paper
tags:
- teaching
- ee693e
- ECG
- IoT
- ZigBee

---

***
## Paper Summary
The paper introduces a wearable ECG monitoring devices that is dedicated to non-technical users and is integrated into the broader IoT infrastructure. A prototype with integrated front end and off-the-shelf components was introduced with multiple advantages with respect to the state of the art. These advantages include record-low energy per effective number of quantized levels, an architecture providing low marginal cost per added sensor, and seamless integration with other smart home systems using a single IoT infrastructure. This ECG wearable can encourage users to develop a healthy lifestyle and also decrease medical costs by allowing them to get ahead of their conditions. 
***

## Presentation
{{< youtube C2LOWF_K-FM >}}

***

## Review
### Strengths
-	Does not require deep technical knowledge to use or implement
-	Less power consumption and high signal quality
-	Easy to integrate with other biomedical devices 
-	Can monitor up to six patients 
-	Easily available data visualizations
-	Detailed explanation of the setup


### Weaknesses
-	Signal quality testing on humans not thorough
-	Movement and respiration induced baseline drift
-	Prone to magnetic interference

### Detailed Comments
By detecting the timing characteristics of click traffic feed received at ad networks, one can detect fraudulent clicks that attempt to be stealthy by sending a low amount of clicks. This is useful as farming clicks is becoming more economical with advances in technology, meaning that more attackers can have the luxury of sending a low amount of fraudulent clicks in an attempt to not be flagged as fake. Then even with a wide range of rates which an attacker can send fake clicks, whether the adversary decides to imitate previous user clicks or generate random clicks, Clicktok is able to identify repeating patterns of the imitation clicks, or the randomness of the clicks as not being attributed to real clicks.

As for the potential weakness in Clicktok, a more advanced click randomization/generation scheme may make detecting fraudulent clicks from real organic clicks difficult. If an attacker is able to uncover how Clicktok determines fraudulent clicks, they may be able to generate a workaround towards Clicktok's defenses. Then addressing the IP aggregation and churn, as some networks may aggregate IPs, it makes identifying individual user's clicks all the more difficult which would result in a lower efficacy when identifying false clicks.

### Implementation
The paper provides an explanation into how they implemented their algorithm of Clicktok, as well as how they collected the data they used to train their model. The way they collected their data was by setting up traffic monitors on backbone routers of a university campus network. They collected a total of 217,334,190 unique clicks, between June 2015 and November 2017. The data was collected after obtaining ethical approval, and all stored data is encrypted. As for how they implemented their algorithm, they took the click traffic of each user (click stream), and attempted to decompose the click streams of each user into basic patterns by using a non-negative matrix factorization algorithm. This decomposes the click traces into pattern matrices, and weight matrices as to how often each pattern occurs.

{{< figure src="https://github.com/gustybear-teaching/course_ee693e_2021_fall/raw/main/week_02/images/ClicktokSystemArchitecture.png" title="System Architecture" width="320" >}}

They then use a moving window function to reduce sensitivity to synchronization errors from timing misalignments.

{{< figure src="https://github.com/gustybear-teaching/course_ee693e_2021_fall/raw/main/week_02/images/ClicktokSystemPartitioning.png" title="Traffic Partitioning" width="300" >}}

Afterwards by examining the weight matrix, they can determine which patterns are repeated and are potentially fraudulent clicks, as patterns matrices that are repeated can be attributed to organic click spam (fake clicks imitating user inputs). They cluster the closely related patterns matrices, to then determine inorganic click spam by finding clusters with a higher entropy, characteristic of clicks generated from a randomized/constant time offsets. The remaining clicks can then be attributed to real users.

Another technique Clicktok applies is bait clicks (active defense), where ad networks inject bait clicks, so any malicious users that may try to imitate these bait clicks are identified with Clicktok's algorithm and flagged as fraudulent.

### Experimentation
In order to evaluate Clicktok, the authors of the paper, used the click traffic obtained, filtered it and exposed it to a testbed with malicious apps and click malware. Through this they were able to get a click traffic that contained both legitimate and fake clicks.

{{< figure src="https://github.com/gustybear-teaching/course_ee693e_2021_fall/raw/main/week_02/images/ClicktokTable1.png" title="Table 1: Passive Detection" width="320" >}}
In their experimentation, they consider *stealthy* attackers to be under 5 clicks a day per device, *sparse* to be 5-15 clicks, and *firehose* to be over 15 clicks. From Table 1, it can be seen that Clicktok with a passive defense is effective in identifying click fraud. With a longer ad network duration, leads to better inference, especially against stealth attacks.

{{< figure src="https://github.com/gustybear-teaching/course_ee693e_2021_fall/raw/main/week_02/images/ClicktokTable2.png" title="Table 2: Detection Across Multiple Clickstreams" width="320" >}}
They also categorized and analyzed different click categories, where sponsored are advertisements displayed by search engines, contextual are ads displayed on a webpage based on keywords present in the webpage, and mobile are ads exclusively present on mobile devices. From the results in Table 2, it is shown that the Clicktok is able to identify fraudulent clicks across the ad categories at a high true positive rate of ~90%, and a low false positive rate at around ~0.004%.

{{< figure src="https://github.com/gustybear-teaching/course_ee693e_2021_fall/raw/main/week_02/images/ClicktokTable3.png" title="Table 3: Active Defense" width="320" >}}
When applying the active defense with bait clicks, it can be seen in Table 3, that it improves detection rates. With both the increase in true positive rates, and decrease in false positive rates, show that an active defense may be important in identifying fake clicks.

{{< figure src="https://github.com/gustybear-teaching/course_ee693e_2021_fall/raw/main/week_02/images/ClicktokTable4.png" title="Table 4: Comparation of Clicktok" width="320" >}}
Lastly, Clicktok gives an comparation between their implementation compared to other defenses, with Clicktok providing vastly lower false positive rates comparatively, and similar or better true positive rates.

### Audience Questions
1. While using the device, does a patient's physical activity (e.g. running, standing still, etc.) affect the magnitude of the ECG signal (i.e. mV to V)?
The patient’s physical activity does affect the signal reading, but not in terms of changing order of magnitudes. The paper states that the peak-to-peak amplitude is approximately around 1 mV but can reach up to 3 mV. So, an amplitude reading in V magnitude does not look like a possibility.

2. Can this wearable ECG monitoring system detect "Arrythmias (problem in heart rythm/missing or irregular heartbeat)"?
There was no official testing done to see how this device performs in Arrythmias detection, but based on the information provided we can make an educated guess. The ECG signal provides a clearly identifiable reading of the QRS Complex, the P and T waves, and the ST segment. These are all important information used in identifying Arrythmias, the only requirement would be to collect the data over enough amount of time. 

3. What do you think should be improved in the system/experiment?
The limitations of threshold based approaches is that with how economical setting up click farms is now, adversaries can now attack with sending clicks under the threshold and still be able to profit.

-	More thorough signal quality and range testing 
-	Evaluate security of data server 
