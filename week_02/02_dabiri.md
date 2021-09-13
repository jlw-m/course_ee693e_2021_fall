---
title: "02: A Telehealth Architecture for Networked Embedded Systems: A Case Study in In Vivo Health Monitoring
Dabiri, Massey, Member, Noshadi, Hagopian, Lin, Tan, Schmidt, and Sarrafzadeh"
date: 2021-09-02
type: book
commentable: true
# Provide the name of the presenter
summary: "Presenter(s): Clyde James Felix, Tasmia Tahmid, Jeanalyn Wadsack-Myers "
# Provide other tags that describe the paper
tags:
- teaching
- ee693e
- Telehealth
---
***
## Paper Summary
With the advances of wireless technology and embedded systems, it is possible to implement remote telemedicine and healthcare systems focusing to improve human physiological analysis. The paper aims to discreetly analyze through continuous monitoring how the patient's lifestyle affects their physiological conditions. This research proposed a hierarchical network architecture capable of collecting data from patients (On-Body Networks) wirelessly to a server. The focus of the network structure is to develop continuous, real-time systemic monitoring technology that is reconfigurable and flexible in the telemedicine field. The paper describes in detail the five major segments of active pressure monitoring systems i.e. pressure transducer, catheter design, power and communication, remote in vivo software configuration, and biocompatible packaging. The paper also discusses the benefits of the network system in telehealth applications. The paper presents a case study on in vivo pressure monitoring system to actively gather and distribute information on the pressure within the upper urinary tract in a manner that is extremely fault-tolerant. The case study helps to demonstrate the effectiveness of the network structure in an _in vivo_ pressure application. Experimental results of the case study explain how it can wirelessly transmit pressure readings measuring from 0 to 1.5 lbf/in<sup>2</sup> with an accuracy of 0.02 lbf/in<sup>2</sup>.
***
## Presentation
{{< youtube mjYajOtTV7A >}}
***
## Review
### Strengths
- Provides flexibility in terms of functionality and the type of applications that it supports.
- The network strucure is capable of expansion in the quality of sensor nodes in a body and the quality of bodies to be analyzed.
- Direct, continuous, and minimally invasive pressure measurements enabling the creation of therapeutic guidelines for the lower urinary track.
- The concept is supported and validated by a case study and experiments. 

### Weaknesses
- There are security risks in data transmission from sensor node to server. The _Man in the Middle_ attack is only of the common attacks that can view and edit data during the data transmission process.
- The major limitation of the case study is that the experiments presented in the paper are limited to only two trials because of the surgical procedure and thus the case study results can validate the concept only.
- The paper does not include aspects of cryptography protection to protect communications from malicious eavesdropping and tampering..  
- The telehealth architecture for a networked embedded system presented in the paper is an old-fashioned infrastructure. The latest research and development in this area show more updated infrastructure for similar network embedded systems. 
- Battery power is a limitation of the implemented design. The architecture uses a li-polymer battery as a power source to support the sensor bridge, signal conditioning circuit and wireless communication but the battery cannot be recharged or changed after it has been implanted.
- The paper lacks further guidelines to improve wireless network protocol in the future.

### Detailed Comments
The paper presents a novel hierarchical network architecture that enables real-time health monitoring including lightweight sensing wireless modules placed on the lower level of the body and the medical enterprise servers at a higher level. The network communication protocol presented in the paper contributes to improved diagnosis and monitoring in Telehealth applications with a dynamic architecture with tailorable OBNs for individuals. While on the other hand some limitations are also being identified during our review of this paper. As mentioned under the weaknesses, a li-polymer battery is being used as a power source to support the sensor systems and the wireless network but this battery cannot be recharged or changed after it has been implanted. The paper describes a power management strategy to compensate for the issue, but there was no detailed analysis of the total power consumption of the system and explanation about the process they have optimized the power consumption under Section V(C) to support their strategy quantitatively. The case study is kind of disconnected from the network implementation itself. The experiments done under the case study are limited to only two trials because of the surgical procedure and thus the case study results can only validate the concept.The paper also lacks a proper guideline for further research to improve wireless network protocol in the future.   

### Implementation
A case study is being conducted to develop and implement an In Vivo active pressure monitoring. Localized obstructions between the kidney and the urethra cause elevated pressures in both the upper urinary tract and lower urinary tract, which often leads to increased risk of infection, kidney stones, bladder and various kidney diseases. An elevated pressure in the urinary tract is one of the major symptoms of urinary blockage. Therefore, if this change in pressure can be detected effectively, diagnosis of urinary tract diseases will be possible at an early stage. To address the problem of localized pressure monitoring, an implantable active pressure sensor has been developed and implemented for the continuous measurement of elevated pelvic and urethral renal pressures. The Active pressure monitoring system has five major segments namely, pressure transducer, catheter design, power and communication, remote in vivo software configuration, biocompatible packaging. The overall goal of the in vivo pressure monitoring system is to actively gather and distribute information on the pressure within the upper urinary tract in a manner that is extremely fault tolerant. Then the collected data is transmitted to a PDA (personal digital assistant) that uploads the data to an online database for further research. 

### Experimentation
<!-- {{< figure src="https://github.com/gustybear-teaching/course_ee693e_2021_fall/raw/main/week_02/images/responsetime.jpg" title="Response Time" width="300" >}}

{{< figure src="https://github.com/gustybear-teaching/course_ee693e_2021_fall/raw/main/week_02/images/successrate.jpg" title="Success Rate with One Round" width="300" >}}

{{< figure src="https://github.com/gustybear-teaching/course_ee693e_2021_fall/raw/main/week_02/images/multipleattempts.jpg" title="Success Rate with Multiple Rounds" width="300" >}} -->

### Discussion
From the table, we can see the results of one of the dry-lab experiments to explore which frequency and duty cycle combination would minimize the drift that was found in the signal during the pressure sensor characterization tests. It was found that a frequency of 50k along with a duty cycle of 20 gave the best results with a drift rate which was able to last 800+ hours before reaching 10% drift.

The second figure shows the results of the experiment in vivo using a porcine (pig) model. One sensor was implanted into the bladder and the other in the peritoneal cavity. The results show pressure measurements of a pig’s bladder voiding profile.

The third figure shows the detrusor pressure measurements derived from subtracting the peritoneal cavity pressure from the bladder pressure. The detrusor is a muscle layer that forms on the bladder wall which gives a more accurate reading of bladder activity since it is unaffected by factors such as abdominal straining, gas and abdominal contents. 

### Questions
(1) How much empahsize is given to the security of the central server once all the data is collected and stored?

This paper does not provide any content on security for the proposed network architecture on the server. Possible solutions to provide security is to use cloud technology, or a role-based access control on the server.

(2) Do you think this type of technology can adapt to abnormal conditons, e.g. pregnant woman, whose urinary flow is proportional to the growth of the baby?

It is possible to use different types of sensor nodes that handle abnormal conditions. However, there are concerns from the experiments. While the experimental results on a pressure system case study shows small innacuracies, it is likely that other applications will have the same problem. The reason of this is possibly from the experiments not being experimented enough.

(3) What vulnerabilities are you aware of in an ad hoc network? What are the drawbacks of their open-ended communication protocol?

The major two levels of attack in the ad hoc network could be attacks against the security mechanisms and attacks against the basic mechanisms. Ad hoc networks use wireless links for communications, employing their own routing strategies, and  the operation functions  in a distributed manner. Therefore, mobile ad hoc networks are highly susceptible to routing attacks because of their dynamic topology and lack of any infrastructure. Security issues are great concerns for ad hoc networks as well. The attacks in the telemedicine application can be targeted to alter health data. By taking advantage of security vulnerabilities or weaknesses, an attacker could take control of  the central system which can lead to compications with in the health sector in large scale.  
