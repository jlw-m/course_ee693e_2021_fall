---
title: "01: They Can Hear Your Heartbeats: Non-Invasive Security for
Implantable Medical Devices
Shyamnath Gollakota, Haitham Hassanieh,
Benjamin Ransford, Dina Katabi, Kevin Fu"
date: 2021-10-25
type: book
commentable: true

# Provide the name of the presenter
summary: "Presenter(s): Saige Dacuycuy, Tasmia Tahmid, Beemnet Alemayehu"

# Provide other tags that describe the paper
tags:
- teaching
- ee693e
- Full-duplex
- Implanted Medical Devices

---

***
## Paper Summary
Implantable medical devices are widespread and have been helping patients for decades. However, the recent works have shown that IMDs are vulnerable to attack. The biggest challenge arises from the difficulty of modifying an already implanted devices for security enhancements. The paper proposes to the use of a physical device called the shield, in which the security of the IMD is delegated to. The shield uses a novel radio design that can act as a jammer-cum-receiver. This design allows it to jam the IMD’s messages, preventing others from decoding them while being able to decode them itself. This design was evaluated using a software radio and was able to effectively provide confidentiality and protection from outside attacks.
***

## Presentation
{{< youtube h7mzwFhR_M0 >}}

***

## Review
### Strengths
- Provide protection for existing IMD with any modifications	
- Can coexist with other devices
- First to use full duplex radio


### Weaknesses
- High turn-around time
- Low practicality of jammer-cum-receiver, especially when translating signal from analog to digital domain
- Shield has a transmission power limit, which is dependent on the position of the adversary

### Detailed Comments
By detecting the timing characteristics of click traffic feed received at ad networks, one can detect fraudulent clicks that attempt to be stealthy by sending a low amount of clicks. This is useful as farming clicks is becoming more economical with advances in technology, meaning that more attackers can have the luxury of sending a low amount of fraudulent clicks in an attempt to not be flagged as fake. Then even with a wide range of rates which an attacker can send fake clicks, whether the adversary decides to imitate previous user clicks or generate random clicks, Clicktok is able to identify repeating patterns of the imitation clicks, or the randomness of the clicks as not being attributed to real clicks.

As for the potential weakness in Clicktok, a more advanced click randomization/generation scheme may make detecting fraudulent clicks from real organic clicks difficult. If an attacker is able to uncover how Clicktok determines fraudulent clicks, they may be able to generate a workaround towards Clicktok's defenses. Then addressing the IP aggregation and churn, as some networks may aggregate IPs, it makes identifying individual user's clicks all the more difficult which would result in a lower efficacy when identifying false clicks.

### Discussion
The authors had to calibrate the shield parameters to set the component bench marks. The shield was doing two tasks, send a random signal to the jammer and an antidote to the receiver antenna. The antenna calibration evaluates the performance of the antidote signal at the receiver. To evaluate this, the shield transmitted 100 Kb without the antidote followed by 100 Kb with the antidote. The difference in the power received at the receiver shows how much the antidote was able to block. This value averaged at 32 dB. The shield needs to balance how much to jam the eavesdropper and how much error to tolerate when decoding the IMD signal. 

To evaluate the shield protection against adversaries, the authors did two measurements. The first one was against passive adversaries where eavesdroppers try to intercept messages, and the second one is against active adversaries where they try to issue unauthorized commands to the IMD. The shield repeatedly triggers the IMD to transmit the same 1000 packets to evaluate shield’s jamming against passive adversaries. All the adversary locations had nearly 50% BER showing the effectiveness of the shield. 

Active adversaries were further divided into two based on the equipment they use. Those that use off-the-shelf IMD programmer and those that use custom hardware that transmits with higher power. The location distances varied from 20 cm to 30 m from the shield. Each adversary ran the same command 100 times with both the shield on and shield off. The shield was able to block all the attacks by the off-the-shelf IMD programmers, but the sophisticated IMD programmers that were closer than 5m were able to get a response from the IMD. Without the shield IMD programmers up to 27 m away was able to elicit a response. This shows the shield offers valuable protection to the IMD. An additional feature of the shield is to raise an alarm when an attempt is made regardless of the success/failure of the attacker.


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

1.	Is there some power loss that we need to consider for this system? Power delivered to an attacker from the IMD-shield combo? 
      Distance and RF environments do play a role here. In the experiment, not all the adversaries were able to send their commands to the IMD. For example, off-the-shelf IMD programmers who were placed further than 14m were not able to get any response even without the shield, and the custom hardware adversaries further than 27m were similarly unsuccessful.

2.	There is always a cost-benefit analysis when it comes to security and convenience. What is the cost of this system?

3.	What are the limitations for this experiment?
