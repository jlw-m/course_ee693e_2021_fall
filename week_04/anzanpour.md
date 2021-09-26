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

The system architecture proposed in this paper consists of three layers: (a) Sensing layer, (b) Edge layer and (c) Cloud layer. 

As presented in the first figure under Experimentation Section, the microcontroller (i.e. reconfigurable sensing devices) collect a patient's activity and medical data and send them to the gateway device in the edge layer. The gateway in response sends a new configuration instruction to the cloud server for storage . The cloud stores the transmitted patient information in a database for long-term evaluations. The proposed system has two unique aspects i.e. (1) Reconfigurable Sensor Node and (2) Personalized Edge-Assisted Controller. In this paper the authors propose a reconfigurable sensor node whose sensing fidelity and hibernate duration can be changed at runtime.  The local control feature provided by the edge layer (i.e. edge processor) periodically determines the lowest sensor’s current level). In the proposed design, the sensor node containing PPG sensors, accelerometer and temperature sensors is a data recorder for wireless activity and medical vital signs. A PPG sensor is used for recording the light reflection intensities from the fingertip, a temperature sensor is used for measuring the skin temperature, and a 3D accelerometer is chosen for recording the patient’s activities. The reconfigurable sensor node is a remotely programmable data collector and in every iteration it receives a command from the smart gateway regarding its new task . 

The sensor service functions flow chart presented in the second figure (refer to Expermebtation section above), shows the chronological functionalities among different layers. A micro-controller communicates with these sensors and records collected data to a flash memory. After recording, the sensor node connects to the gateway using a low-power WiFi module, transmits the recorded data to the edge layer, asks in reply for a new configuration command, and then goes to the hibernate mode for a time interval specified in the configuration. After hibernation duration, the sensor node wakes up and starts recording again according to the latest instruction. 

The third figure under Experimentation Section presents a Personalized Edge-Assisted Controller including a set of cognitive algorithms demands a lower sensing energy to provide the same level of sensing accuracy e.g., root mean squared error (RMSE). Thus, activity-based sensing control can save a considerable amount of energy. 

The system design-time block diagram presented in fourth figure, shows the total RMSE calculation approach consisting of two system cognition phases, during which the edge determines the sensing fidelity design time and sensing fidelity runtime. Related work examples presented in this paper shows that 5 minutes is a reasonable interval to capture changes in one’s activity. Therefore, the authors set the sensing duration to 5 minutes with five different durations for hibernation. Turning off the radio communication during data recording and microcontroller hibernation helps to change the power consumption states of the sensor node. 

The performance of the proposed system  and evaluation results in terms of accuracy is further explained under the Discussion Section below. 

### Experimentation

{{< figure src="https://github.com/gustybear-teaching/course_ee693e_2021_fall/raw/main/week_04/images/Anzanpour_Fig.9.JPG" title="The three-layer architecture of the proposed system" width="300" >}}

{{< figure src="https://github.com/gustybear-teaching/course_ee693e_2021_fall/raw/main/week_04/images/Anzanpour_Fig.10.JPG" title="Sensor device functions flowchart" width="300" >}}

{{< figure src="https://github.com/gustybear-teaching/course_ee693e_2021_fall/raw/main/week_04/images/Anzanpour_Fig.11.JPG" title="High-level edge-assisted control architecture" width="300" >}}

{{< figure src="https://github.com/gustybear-teaching/course_ee693e_2021_fall/raw/main/week_04/images/Anzanpour_Fig.12.JPG" title="System design-time block diagram" width="300" >}}

{{< figure src="https://github.com/gustybear-teaching/course_ee693e_2021_fall/raw/main/week_04/images/Anzanpour_Fig18a.png" title="The effect of activity type on total RMSE" width="300" >}}

{{< figure src="https://github.com/gustybear-teaching/course_ee693e_2021_fall/raw/main/week_04/images/Anzanpour_Fig18b.png" title="The average of total RMSE in different activites" width="300" >}}

{{< figure src="https://github.com/gustybear-teaching/course_ee693e_2021_fall/raw/main/week_04/images/Anzanpour_Fig19.png" title="24-hour health monitoring of a person" width="300" >}}

{{< figure src="https://github.com/gustybear-teaching/course_ee693e_2021_fall/raw/main/week_04/images/Anzanpour_Table3.png" title="Outputs due to different scenarios for sensing device hibernation duration" width="300" >}}

### Discussion
As we can see from 5th figure under experimentation section, we can see the uncertainty increasing for activities that require more physical effort. The probable reason for variation in the RMSE is due to the oscillating nature for heart rate, oxygen saturation, and respiration rate of each individual when undergoing each activity. Although each individual is healthy, it is more likely that each individual reacts differently to a certain activity.

From the 6th under experimentation section, by setting the driving current of the LEDs higher, we see that there is less variation in the RMSE. This is due to the notion that a higher driving current in an LED results in higher intensities of light in the LED; therefore, the detection of the PPG signals are more accurate. From this figure, the authors were able to show that setting the current at 3.5 mA gives acceptable RMSE because of the variation in any physical activity. This is especially true with sleeping, sitting and walking. 

As for the 7th figure, this shows a 24-hour health moinitoring of a healthy person. By extracting the activity level and calculating the EWS, the RMSE threshold values are determined and the readjustment algorithm is executed. The three parameters: oxygen saturation; respiratory rate; and heart rate; play contributing factors on calculating RMSE. Each parameter has different trade-off rates in regards to sensitivity and being susceptible to noise. The edge layer then chooses the lowest sensor's current level to satisfy the RMSE threhold.

For the table under experimentation section, from implementing different time settings for hibernation time, we can see its effect on the total recording time, the percentage of missed events, and the average power consumption. To get the most effecctive use of the proposed device, it must be capable of recording 100% of an individual's event. This is where scenario 4 showed the most effective use of hibernation time while saving approximately 49% of power consumption from the baseline.

The lowest RMSE values is given for high-level physical activity, where "running" and "jogging" states are 2.931 and 1.431, respectively. Even if the maximum current level is used, it can't improve the accuracy of the sensor over a certain threshold. While implementing scenario 4 for hibernation timing, high-level activity and/or a high EWS resets the hibernating time of the sensor to zero, and the lower-level activities and/or normal EWS prolonged the hibernation duration. In addition, based on the performance of the edge controller, the sensor was able to save 49% of the battery power for the case study.

### Questions
(1) The transferring process consumes the most electricity, as seen in Table 2. In order to reduce this power usage, what suggestions do you have?

The authors mentions that they plan optimize the data transfer bandwidth. Since this is in relation to the reducing of power consumption, it would be best to consider a different selection of sensors as well as compacting the sampling size with respect to the patient's conditions. A potential problem in the sensor that the author uses is that the two LEDs emit red light and infrared, which is a very small difference in wavelength as compared to other PPG devices that uses green light LEDs. Therefore, the tunability in sensing energy is not as high.

(2) Would there be a case where energy efficiency is not given as much consideration to increase the accuracy of measurement depending on the patient?

Yes, it is possible when a patient is mostly bedridden. In this case, the sensor devices does not need to be adjusted to save energy.

(3) Do you think the perspiration during physical activities is a factor that affects the error in the sensors?

It is possible that perspirations can affect sensor measurements. Further research will have to be conducted on whether perspiration plays a great factor in the error.

