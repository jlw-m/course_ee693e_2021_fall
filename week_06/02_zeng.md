---
title: "02: FullBreathe: Full Human Respiration Detection Exploiting Complementarity of CSI Phase and Amplitude of WiFi Signals
Y. ZENG, D. WU, R. GAO, T. GU, D. ZHANG,"
date: 2021-09-29
type: book
commentable: true
# Provide the name of the presenter
summary: "Presenter(s): Clyde James Felix, Jeanalyn Wadsack-Myers, Banh Nguyen"
# Provide other tags that describe the paper
tags:
- teaching
- ee693e
- WiFi
- Respiration sensing
---
***
## Paper Summary
Wireless human respiration decection using WiFi signals has a great potential in the teledemedicince field. This research tackles the wireless sensing problem by investigating the properties of amplitude and phase information on WiFi signals. The discovery of the phase and amplitude complementarity property is used to solve the blind spot problem. This paper also evaluates the complementarity in the respiration sensing application. The result of the experimentations shows that the complementarity property still holds in different factors such as environmental changes, and tranceivers distance. 
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
<!-- 2FA-PP is a novel 2FA scheme which helps mitigate phishing attacks. Although it has a poor time preventing phishing attacks on the same network, with an attacker success rate having a worse case scenario of 35% success rate if not tuned correctly, it is more than likely that the phishing attack will occur from a proxy server, moving its location far from the user, meaning it would be able to prevent a majority of phishing attacks. Since 2FA-PP only requires the user to set up an application and the server to set up a database to handle interactions with the application, it is a user friendly scheme which is easy to implement into existing structures, using current generation browser APIs to communicate with the phone’s BLE, which is readily available to a majority of users who use 2FA. Some worries for 2FA-PP stems from the use of the browser’s API to communicate with BLE, as this can be a vector for attack by the phishing user where they can take over communication and report a real domain as opposed to the phishing domain, but this is circumvented by the use of obfuscation techniques, such that the report of the domain will be unobfuscated in a certain way, preventing a phishing user from figuring out and using this obfuscation technique within the given time frame. -->

### Implementation
<!-- To implement 2FA-PP, there are two components: the smartphone application and the server. The smartphone application will act as the software token, and will communicate with the server to keep a set of tokens up to date. The smartphone application requires minimal permissions from the user, only needing Bluetooth access, which is used to communicate with the browser. As for the server, it will handle the registration of the 2FA device, or our smartphone application,  and each instance of a login which requires a 2FA.

Although these are the two main components to be implemented, there are also some intermediate steps that are taken. The client side, which would be the computer logging onto the server, needs Bluetooth functionality, and the ability to run JavaScript, the two of which are widely available on a majority of laptops and desktops.

Once the smartphone application is registered as a 2FA device, the flow of authentication is as follows. When a client logs into the server, the server will request the 2FA device, or smartphone in our case, a token. To get this token, a challenge is sent in a form of a JavaScript file, which is encrypted with a key which only the server and smartphone have. The smartphone knows the answer to this JavaScript file, which is used to verify the URL. Once the smartphone sends the decryption key to the client, it will start a timer, where the browser will execute the JavaScript file to unobfuscate the ciphertext it contains. The obfuscation process contains references to the legitimate URL, which is obtained through the browser’s reference to the URL, window.location, which cannot be modified by a phishing user. Once the challenge is completed, the answer is sent to the smartphone for verification. If correct and within the timing threshold, the smartphone will send the token to verify the login. -->


### Experimentation
{{< figure src="https://github.com/gustybear-teaching/course_ee693e_2021_fall/week_06/images/zeng-experiment1.jpg" title="Experiment Setup." width="300" >}}
{{< figure src="https://github.com/gustybear-teaching/course_ee693e_2021_fall/week_06/images/zeng-experiment2.jpg" title="Experiment Positions to test." width="300" >}}
{{< figure src="https://github.com/gustybear-teaching/course_ee693e_2021_fall/week_06/images/zeng-UI.jpg" title="FullBreathe Web UI." width="300" >}}
{{< figure src="https://github.com/gustybear-teaching/course_ee693e_2021_fall/week_06/images/zeng-results.jpg" title="Amplitude and Phase signals in different antenna positions." width="300" >}}
{{< figure src="https://github.com/gustybear-teaching/course_ee693e_2021_fall/week_06/images/zeng-LoSresults.jpg" title="Impact of different Line of Sight between tranceivers." width="300" >}}
{{< figure src="https://github.com/gustybear-teaching/course_ee693e_2021_fall/week_06/images/zeng-envresults.jpg" title="Impact of different environments." width="300" >}}
{{< figure src="https://github.com/gustybear-teaching/course_ee693e_2021_fall/week_06/images/zeng-fridgeresults.jpg" title="Impact of different environmental changes." width="300" >}}

### Discussion
<!-- As we can see from the first figure, we can see all of the variations in timings that 2FA-PP observes, whether it being a normal login, to a phishing attack which modifies the obfuscated code. Although phishing attacks are able to successfully modify the obfuscated code, the round trip and modification takes a considerable amount of time, where we can set our threshold to contain the vast majority of our baseline timing, while preventing a majority of phishing attacks.

As from the second figure, by setting the threshold accordingly, we see that attackers within a different locality as the user have a difficult time successfully attacking 2FA-PP. However, if they are in the same locality, such as the same Wi-Fi or Hotspot, the success rate is significantly higher. We could reduce the success rate by tightening our threshold, but this is at the cost of false positives, where legitimate logins are deemed suspicious.

For the third figure, as this is a scalable implementation, we can send multiple challenges to the client. This lessens the chance for an attacker to successfully complete all of the challenges within the given time frame, therefore securing the login from phishing attacks. We find that at about 5 challenges, gives the best chance of preventing phishing attacks, even with local adversaries. -->

### Questions
(1) Can you elaborate the reason why subject location and environmental changes does not affect the complimentary of CSI phase and amplitude?

(2) Is there any possible way to increase/improve the respiratory sensing range? 

The respiratory sensing rage is very accurate if the subject is facing in front of the tranceivers, staying still, and in the detectable sensing range.

(3) Is there a limit on the number of subjects that can use this application at a time?

The papers states that the research is only for one subject only. Although, there are possible ways to make this work for multiple subjects.
