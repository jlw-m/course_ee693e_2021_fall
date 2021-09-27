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
{{< youtube 5FkW8F8-CMw >}}

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
Wearable biomedical devices can take advantage of the exponential reduction in cost per function enabled by Moore's Law and broadband penetration in large sectors of the population. They typically consist of monitors of vital signs, wirelessly connected to a smartphone or to a computer that often enable data logging and visualization through a web or mobile application. Overwhelming demographic trends are expected to increase the demand for healthcare services. Net annual savings in US health care expenditure of $12 billion could be achievable with widespread adoption of remote monitoring technologies for chronic diseases. They propose an ECG remote monitoring system dedicated to long-term health monitoring of users/patients in residential environments without assistance, and integrated in a broader IoT infrastructure.

A single local network can monitor up to six patients per single ZigBee channel at the same time, with the same wireless infrastructure, reducing system cost per patient, perceived complexity, and marginal cost of adding a monitored patient. Sensors send messages to the IoT server, where the data management unit extracts information and enters it into the sensor database. The gateway encapsulates the packets of the sensors in a universal format which preserves all the information present in the native format. In this way, data processing and configuration is separated from measurement and data collection, and does not need to take into account the communication protocol of the originating source. The actual ECG signal has a bandwidth from 0.05 Hz to150 Hz and peak-to-peak amplitude of approximately 1 mV but can reach 3 mV.

Motion artifacts (including respiration and body movements) and a poor skin-electrode contact can generate an additional large low frequency offset (±300 mV) that can cause baseline wander. A typical single-channel ECG AFE with DRL circuit amplifies the input common mode voltage and feeds it back into the patient's body, in order to suppress the amplitude of the common-mode interference at the amplifier input. System is based on a general-purpose, high performance, high resolution, low power ADC (Texas InstrumentsADS1246) that also includes a digital filter. The analog front end is a passive two-stage filter connected to conductive rubber electrodes installed into a chest belt. Since the spectral content of the baseline wander is usually in the range between 0.05 and 1 Hz, a linear high-pass filter with a cut-off frequency close to 1 Hz would be required to reject it.

The electronic circuit for recording ECG signals is based on a TI ADS1246 24-Bitanalog-to-digital converter powered at 3 V and sampling at 320 Hz. Under these conditions, the complete ECG front-end has an ENOB of 14, much higher than the ENOB between 8 and 12 of most present-day systems. The ECG circuit has been realized as a standard two layer PCB. The cost of the ECG sensor board can be estimated below $10 for a production of 1000 pieces. ZigBee data are transmitted to the receiver as ZigBee packets of near maximum length, in order to minimize packet rate, duty cycle, and power consumption. Each packet is encrypted by the ZigBee stack with a 128-bit key and uses the 32-bit MIC (Message Integrity Code) created using the 128-AES algorithm. The reconstruction algorithm is able to resynchronize after every packet and can tolerate missing or defective packets.

An actual deployment of the system was used to evaluate key aspects, including the possibility to monitor the ECG signal of multiple patients in a large area and for a long time. The test deployment consisted of six ECG sensor nodes, a ZigBee gateway and an IoT server. Various tests have been performed in order to evaluate: A. quality of the wireless ECG signals; B. maximum range; C. maximum data rate; D. power consumption. This is comparable to that of the sensor proposed in where data are sampled at 250 Hz and stored on a micro SD card. In this section we compare our results with related works. Our system does not use driven right leg circuit, which is not needed, as we have discussed in section III. The absence of the third electrode makes the proposed system more compact, more easily wearable, and more energy efficient.

They propose to use the energy per effective number of quantization levels (EENQL) as a relevant figure of merit for sensors. EENQL is the total power consumption of the battery powered parts of the system (in their case, only the ECG board). Other ECG sensors use SimpliciTI, Bluetooth, ANT, and Bluetooth Low Energy which are simply used for two-way links.

The gateway collects data from multiple sensors and encapsulates raw sensor data in a secure TCP/IP packet, whereas there is one gateway per sensor. Their system has the lowest total cost of gateways for a given number of sensors, and the lower marginal cost of adding one ECG sensor to the system. A wireless wearable ECG monitoring system embedded in an IoT platform that integrates heterogeneous nodes and applications, has a long battery life, and provides a high-quality ECG signal. The system allows monitoring multiple patients in a relatively large indoor area(home, building, nursing home, etc.). Their ECG sensor exhibits the record-low EEQNL figure of energy per effective number of quantized levels of all solutions.


### Audience Questions
1. While using the device, does a patient's physical activity (e.g. running, standing still, etc.) affect the magnitude of the ECG signal (i.e. mV to V)?

The patient’s physical activity does affect the signal reading, but not in terms of changing order of magnitudes. The paper states that the peak-to-peak amplitude is approximately around 1 mV but can reach up to 3 mV. So, an amplitude reading in V magnitude does not look like a possibility. Another reason for this affect is motion artifacts (including respiration and body movements) and a poor skin-electrode contact can generate an additional large low frequency offset (±300 mV) that can cause baseline wander.

2. Can this wearable ECG monitoring system detect "Arrythmias (problem in heart rythm/missing or irregular heartbeat)"?

There was no official testing done to see how this device performs in Arrythmias detection, but based on the information provided we can make an educated guess. The ECG signal provides a clearly identifiable reading of the QRS Complex, the P and T waves, and the ST segment. These are all important information used in identifying Arrythmias, the only requirement would be to collect the data over enough amount of time. Another note that this paper focus on developing a high signal quality and low power consumption, so detection any health problems was not mentioned and simply output the graph signals through web interface.

3. What do you think should be improved in the system/experiment?

Future testing of the system will be required to evaluate, among other things, the signal quality and range capabilities of the system in order to ensure that it remains operational. Examine the processes followed by the information-processing server in order to guarantee the security and reliability of the server's operation.
