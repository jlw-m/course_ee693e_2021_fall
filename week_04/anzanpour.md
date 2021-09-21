---
title: "02: Edge-Assisted Control for Healthcare Internet of Things: A Case Study on PPG-Based Early Warning Score
Arman Anzanpour, Delaram Amiri, Iman Azimi, Marco Levorato, Nikil Dutt, Pasi Liljeberg, and Amir M. Rahmani"
date: 2021-09-15
type: book
commentable: true
# Provide the name of the presenter
summary: "Presenter(s): Clyde James B Felix, Tasmia Tahmid, Saige J Dacuycuy"
# Provide other tags that describe the paper
tags:
- teaching
- ee693e
- Edge-Assisted
- PPG
---
***
## Paper Summary
Internet of Things (Iot)  are key techonologies to remote health monitoring application. In this application, sensor devices can measure patient vitals and wirelessly send its gathered data into a database. With the aim of preventing deterioation and death in chronic patients, certain challenges and tradeoffs are considered to improve the Quality of Experience (QoE) of the technology. One of the main tradeoffs mentioned is between measuring patient data accurately and the energy consumption of the sensor devices. This paper proposes an edge-assisted techonology that dynamically controls sensing quality and signal energy with respect to the patient's activity and health status. The proposed technology introduces an optmized way of saving energy while maintaining high signal quality. This paper also examines a case study on a Photoplethysmography (PPG) based early warning score (EWS) system.
***
## Presentation
{{< youtube REIuUV1U448 >}}
***
## Review
### Strengths
- Edge-assisted technology dynamically control sensor settings according to user's status
- Edge controller is energy effectve, capable of saving 49% of battery power
- Edge computing helps to implement author's idea without imposing computation overhead to the sensor layer while providing quick response at the edge layer. 
- The device, while undergoing hibernation, is effectively capable of recording all events from the user

### Weaknesses
- Data transfer bandwidth takes up a lot of energy consumption
- Temperature sensor may be affected by ambient temperature of the hand while the device is in the glove (e.g. prespiration)
- PPG signal is vulnerable to body movements

### Detailed Comments
The paper contributes in designing an edge-based remote health monitoring architecture in out-of-hospital settings with a reconfigurable sensor node for Early Warning Score (EWS) assessment. The Edge-assisted technology dynamically controls sensor settings according to the user's status and their activity. A real-time adaptation of the sensing parameters is made possible through a runtime control algorithm state machine residing at the edge layer. One of the major strengths of the proposed architecture is the optimization approach to reduce the energy consumption of a sensor node with target accuracy of extracted parameters. Choosing edge computing helped the authors to implement their idea without imposing computation overhead to the sensor layer while providing quick response at the edge layer which helps to implement an efficient IoT architecture. 

The proposed system is being tested in terms of accuracy and energy consumption where the user performs different physical activities during their routine. A Personalized Edge-Assisted Controller including a set of cognitive algorithms demands a lower sensing energy to provide the same level of sensing accuracy e.g., root mean squared error (RMSE). Thus, activity-based sensing control can save a considerable amount of energy. While on the other hand, the paper has certain weaknesses that we have identified during our review. The PPG signal used for  Early Warning Score (EWS) is vulnerable to body movements. Temperature sensor may be affected by ambient temperature of the hand while the device is in the glove (e.g. perspiration). Apart from mentioned weaknesses, the paper presents sufficient justification with case study results to prove that the edge controller is energy effective and capable of saving 49% of battery power.  

### Implementation
To implement 2FA-PP, there are two components: the smartphone application and the server. The smartphone application will act as the software token, and will communicate with the server to keep a set of tokens up to date. The smartphone application requires minimal permissions from the user, only needing Bluetooth access, which is used to communicate with the browser. As for the server, it will handle the registration of the 2FA device, or our smartphone application,  and each instance of a login which requires a 2FA.

Although these are the two main components to be implemented, there are also some intermediate steps that are taken. The client side, which would be the computer logging onto the server, needs Bluetooth functionality, and the ability to run JavaScript, the two of which are widely available on a majority of laptops and desktops.

Once the smartphone application is registered as a 2FA device, the flow of authentication is as follows. When a client logs into the server, the server will request the 2FA device, or smartphone in our case, a token. To get this token, a challenge is sent in a form of a JavaScript file, which is encrypted with a key which only the server and smartphone have. The smartphone knows the answer to this JavaScript file, which is used to verify the URL. Once the smartphone sends the decryption key to the client, it will start a timer, where the browser will execute the JavaScript file to unobfuscate the ciphertext it contains. The obfuscation process contains references to the legitimate URL, which is obtained through the browser’s reference to the URL, window.location, which cannot be modified by a phishing user. Once the challenge is completed, the answer is sent to the smartphone for verification. If correct and within the timing threshold, the smartphone will send the token to verify the login.

### Experimentation
{{< figure src="https://github.com/gustybear-teaching/course_ee693e_2021_fall/raw/main/week_04/images/Anzanpour_Fig18a.png" title="The Effect of Activity Type on Total RMSE" width="300" >}}

{{< figure src="https://github.com/gustybear-teaching/course_ee693e_2021_fall/raw/main/week_04/images/Anzanpour_Fig18b.png" title="The Average of Total RMSE in Different Activites" width="300" >}}

{{< figure src="https://github.com/gustybear-teaching/course_ee693e_2021_fall/raw/main/week_04/images/Anzanpour_Tabl3.png" title="Total Monitoring Time, Average Power Consumption, and Missing Event Due to Different Scenarios for Sensing Device Hibernation Duration" width="300" >}}

{{< figure src="https://github.com/gustybear-teaching/course_ee693e_2021_fall/raw/main/week_04/images/Anzanpour_Fig19.png" title="24-hour Health Monitoring of a Person" width="300" >}}

### Discussion
As we can see from the first figure, we can see the uncertainty increasing for activities that require more physical effort. The probable reason for variation in the RMSE is due to the oscillating nature for heart rate, oxygen saturation, and respiration rate of each individual when undergoing each activity. Although each individual is healthy, it is more likely that each individual reacts differently to a certain activity.

From the second figure, by setting the driving current of the LEDs higher, we see that there is less variation in the RMSE. This is due to the notion that a higher driving current in an LED results in higher intensities of light in the LED; therefore, the detection of the PPG signals are more accurate. From this figure, the authors were able to show that setting the current at 3.5 mA gives acceptable RMSE because of the variation in any physical activity. This is especially true with sleeping, sitting and walking. 

For the table, from implementing different time settings for hibernation time, we can see its effect on the total recording time, the percentage of missed events, and the average power consumption. To get the most effecctive use of the proposed device, it must be capable of recording 100% of an individual's event. This is where scenario 4 showed the most effective use of hibernation time while saving approximately 49% of power consumption from the baseline.

As for the third figure, this shows a 24-hour health moinitoring of a healthy person. By extracting the activity level and calculating the EWS, the RMSE threshold values are determined and the readjustment algorithm is executed. The three parameters: oxygen saturation; respiratory rate; and heart rate; play contributing factors on calculating RMSE. Each parameter has different trade-off rates in regards to sensitivity and being susceptible to noise. The edge layer then chooses the lowest sensor's current level to satisfy the RMSE threhold.

The lowest RMSE values is given for high-level physical activity, where "running" and "jogging" states are 2.931 and 1.431, respectively. Even if the maximum current level is used, it can't improve the accuracy of the sensor over a certain threshold. While implementing scenario 4 for hibernation timing, high-level activity and/or a high EWS resets the hibernating time of the sensor to zero, and the lower-level activities and/or normal EWS prolonged the hibernation duration. In addition, based on the performance of the edge controller, the sensor was able to save 49% of the battery power for the case study.

### Questions
(1) The transferring process consumes the most electricity, as seen in Table 2. In order to reduce this power usage, what suggestions do you have?

The authors mentions that they plan optimize the data transfer bandwidth. Since this is in relation to the reducing of power consumption, it would be best to consider a different selection of sensors as well as compacting the sampling size with respect to the patient's conditions. A potential problem in the sensor that the author uses is that the two LEDs emit red light and infrared, which is a very small difference in wavelength as compared to other PPG devices that uses green light LEDs. Therefore, the tunability in sensing energy is not as high.

(2) Would there be a case where energy efficiency is not given as much consideration to increase the accuracy of measurement depending on the patient?

Yes, it is possible when a patient is mostly bedridden. In this case, the sensor devices does not need to be adjusted to save energy.

(3) Do you think the perspiration during physical activities is a factor that affects the error in the sensors?

It is possible that perspirations can affect sensor measurements. Further research will have to be conducted on whether perspiration plays a great factor in the error.

