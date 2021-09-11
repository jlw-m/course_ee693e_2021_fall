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
With the advances of wireless technology and embedded systems, it is possible for this to be implemented in the telemedicine field to improve human physiology analysis. This research proposed a hierarchcial network architecture capable of collecting data from patients (On-Body Networks) wirelessly to a server. The focus of the network structure is to develop continuous, real-time systemic monitoring technology that is reconfigurable and flexible in the telemedicine field. The paper discusses the benefits of the network system in telehealth applications. The paper also presents a case study that demonstrates the effectiveness of the network structure in an _in vivo_ pressure application. Experimental results of the case study explains how it can wirelessly transmit pressure readings measuring from 0 to 1.5 lbf/in<sup>2</sup> with an accuracy of 0.02 lbf/in<sup>2</sup>.
***
## Presentation
{{< youtube mjYajOtTV7A >}}
***
## Review
### Strengths
- Provides flexibility in terms of functionality and the type of applications that it supports.
- The network strucure is capable of expansion in the quality of sensor nodes in a body and the quality of bodies to be analyzed.

### Weaknesses
- There are security risks in data transmission from sensor node to server. The _Man in the Middle_ attack is only of the common attacks that can view and edit data during the data transmission process.
- The paper does not include aspects about cryptography protection.  
- The telehealth architecture for a networked embedded system presented in the paper is an old fashioned infrastructure. The latest research and development in this area shows more updated infrastructure for similar network embedded systems. 
- Battery power is a limitation of the implemented design. The architecture uses a li-polymer battery as a power source to support sensor bridge, signal conditioning circuit
and wireless communication but the battery cannot be recharged or changed after it has been implanted.
- The paper lacks the futher guidelines to improve wireless network protocol in future. 

### Detailed Comments
<!-- 2FA-PP is a novel 2FA scheme which helps mitigate phishing attacks. Although it has a poor time preventing phishing attacks on the same network, with an attacker success rate having a worse case scenario of 35% success rate if not tuned correctly, it is more than likely that the phishing attack will occur from a proxy server, moving its location far from the user, meaning it would be able to prevent a majority of phishing attacks. Since 2FA-PP only requires the user to set up an application and the server to set up a database to handle interactions with the application, it is a user friendly scheme which is easy to implement into existing structures, using current generation browser APIs to communicate with the phone’s BLE, which is readily available to a majority of users who use 2FA. Some worries for 2FA-PP stems from the use of the browser’s API to communicate with BLE, as this can be a vector for attack by the phishing user where they can take over communication and report a real domain as opposed to the phishing domain, but this is circumvented by the use of obfuscation techniques, such that the report of the domain will be unobfuscated in a certain way, preventing a phishing user from figuring out and using this obfuscation technique within the given time frame. -->

### Implementation
A case study is being conducted to develop and implement an In Vivo active pressure monitoring. Localized obstructions between the kidney and the urethra cause elevated pressures in both the upper urinary tract and lower urinary tract, which often leads to increased risk of infection, kidney stones, bladder and various kidney diseases. An elevated pressure in the urinary tract is one of the major symptoms of urinary blockage. Therefore, if this change in pressure can be detected effectively, diagnosis of urinary tract diseases will be possible at an early stage. To address the problem of localized pressure monitoring, an implantable active pressure sensor has been developed and implemented for the continuous measurement of elevated pelvic and urethral renal pressures. The Active pressure monitoring system has five major segments namely, pressure transducer, catheter design, power and communication, remote in vivo software configuration, biocompatible packaging. The overall goal of the in vivo pressure monitoring system is to actively gather and distribute information on the pressure within the upper urinary tract in a manner that is extremely fault tolerant. Then the collected data is transmitted to a PDA (personal digital assistant) that uploads the data to an online database for further research. 

Although these are the two main components to be implemented, there are also some intermediate steps that are taken. The client side, which would be the computer logging onto the server, needs Bluetooth functionality, and the ability to run JavaScript, the two of which are widely available on a majority of laptops and desktops.

Once the smartphone application is registered as a 2FA device, the flow of authentication is as follows. When a client logs into the server, the server will request the 2FA device, or smartphone in our case, a token. To get this token, a challenge is sent in a form of a JavaScript file, which is encrypted with a key which only the server and smartphone have. The smartphone knows the answer to this JavaScript file, which is used to verify the URL. Once the smartphone sends the decryption key to the client, it will start a timer, where the browser will execute the JavaScript file to unobfuscate the ciphertext it contains. The obfuscation process contains references to the legitimate URL, which is obtained through the browser’s reference to the URL, window.location, which cannot be modified by a phishing user. Once the challenge is completed, the answer is sent to the smartphone for verification. If correct and within the timing threshold, the smartphone will send the token to verify the login. -->

### Experimentation
<!-- {{< figure src="https://github.com/gustybear-teaching/course_ee693e_2021_fall/raw/main/week_02/images/responsetime.jpg" title="Response Time" width="300" >}}

{{< figure src="https://github.com/gustybear-teaching/course_ee693e_2021_fall/raw/main/week_02/images/successrate.jpg" title="Success Rate with One Round" width="300" >}}

{{< figure src="https://github.com/gustybear-teaching/course_ee693e_2021_fall/raw/main/week_02/images/multipleattempts.jpg" title="Success Rate with Multiple Rounds" width="300" >}} -->

### Discussion
<!-- As we can see from the first figure, we can see all of the variations in timings that 2FA-PP observes, whether it being a normal login, to a phishing attack which modifies the obfuscated code. Although phishing attacks are able to successfully modify the obfuscated code, the round trip and modification takes a considerable amount of time, where we can set our threshold to contain the vast majority of our baseline timing, while preventing a majority of phishing attacks.

As from the second figure, by setting the threshold accordingly, we see that attackers within a different locality as the user have a difficult time successfully attacking 2FA-PP. However, if they are in the same locality, such as the same Wi-Fi or Hotspot, the success rate is significantly higher. We could reduce the success rate by tightening our threshold, but this is at the cost of false positives, where legitimate logins are deemed suspicious.

For the third figure, as this is a scalable implementation, we can send multiple challenges to the client. This lessens the chance for an attacker to successfully complete all of the challenges within the given time frame, therefore securing the login from phishing attacks. We find that at about 5 challenges, gives the best chance of preventing phishing attacks, even with local adversaries. -->

### Questions
(1) How much empahsize is given to the security of the central server once all the data is collected and stored?

This paper does not provide any content on security for the proposed network architecture on the server. Possible solutions to provide security is to use cloud technology, or a role-based access control on the server.

(2) Do you think this type of technology can adapt to abnormal conditons, e.g. pregnant woman, whose urinary flow is proportional to the growth of the baby?

It is possible to use different types of sensor nodes that handle abnormal conditions. However, there are concerns from the experiments. While the experimental results on a pressure system case study shows small innacuracies, it is likely that other applications will have the same problem. The reason of this is possibly from the experiments not being experimented enough.

(3) What vulnerabilities are you aware of in an ad hoc network? What are the drawbacks of their open-ended communication protocol?

The major two levels of attack in the ad hoc network could be attacks against the security mechanisms and attacks against the basic mechanisms. Ad hoc networks use wireless links for communications, employing their own routing strategies, and  the operation functions  in a distributed manner. Therefore, mobile ad hoc networks are highly susceptible to routing attacks because of their dynamic topology and lack of any infrastructure. Security issues are great concerns for ad hoc networks as well. The attacks in the telemedicine application can be targeted to alter health data. By taking advantage of security vulnerabilities or weaknesses, an attacker could take control of  the central system which can lead to compications with in the health sector in large scale.  
