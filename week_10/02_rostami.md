---
title: "02: Heart-to-Heart(H2H): 
Authentication for Implanted Medical Devices
M. Rostami, A. Juels, F. Koushanfar"

date: 2021-10-27
type: book
commentable: true
# Provide the name of the presenter
summary: "Presenter(s): Clyde James Felix, Jeana Wadsack-Myers and Banh Nguyen "
# Provide other tags that describe the paper
tags:
- teaching
- ee693e
- Cryptography
- ECG
---
***
## Paper Summary
Implantable Medical Device (IMD) applies continuous monitoring therapies for chronic medical disordered patients. Patients have been implanted with IMDs to assess vital signs. To reprogram the IMD and to extract its data, a Commercial Device Programmers is a device that can perform these tasks wirelessly. A problem with this technology is the security risk that can harm patients. Hackers can seize unauthorized control of the IMDs. This paper proposes Heart-to-Heart (H2H) that establishes a novel access-control policy between the programmer and the IMD. H2H utilizes Electrocardiogram signals to generate random key sources to authorize control to IMDs. This paper further discusses the validity of ECG signals for authentication by examining their entropy. This paper also described the cryptographic pairing protocol between the programmer and the IMD and tested it on an adversarial model. Lastly, this paper describes the full implementation of H2H while displaying code size and power consumption analysis.
***
## Presentation
{{< youtube cQj1CtbFsMI >}}
***
## Review
### Strengths
- Provides greater security for the IMDs
- Provides a protocol for crucial cases (i.g. patient ECG goes flat)

### Weaknesses


### Detailed Comments

### Implementation
H2H was implemented into an IMD prototype consisting of three boards which can be seen from Figure 6. The ARM board was chosen to be the Leopard Gecko EFM-32 microcontroller (EFM32LG-DK3650) with a 32-bit ARM Cortex-M3 processor. This board communicates with the ECG analog front end (TI ADS1298) and the wireless board (TI CC430F5137). It has convenient power debugging tools and can extract the ECG features and communicate with the Programmer using TLS all while having a good power consumption profile. The main components can be seen in Figure 7.

TLS is used to establish the secure channel implementation between the Programmer and H2H. It is designed to provide an encrypted and authenticated channel between the two parties, usually comparing the Programmer certificate to PKI. However, the authors chose to forgo that for the ECG PV comparison which is more forgiving to the noise typical in ECG signals. RSA encryption for key exchange is chosen since it is the fastest exchange option for TLS in this application which has a small public exponent of 216 + 1. The RSA follows the NIST key length recommendation of modulus and message length set to 2048 bits and is also MISRA-C standard compliant. A breakdown of the size, number of clock cycles and power consumption can be found in Table 4.

A NIST-recommended pseudo-random number generator or PRNG is used to allow certain actions such as RSA ciphertext padding and key generation and commitment. The initial random seed is generated offline and stored in the IMD’s non-volatile memory. As for ECG parameter extraction, the prototype annotates the ECG R-peaks by using an open source algorithm called WQRS to apply a simple length transformation to the ECG waveform.

### Experimentation
<!-- {{< figure src="https://github.com/gustybear-teaching/course_ee693e_2021_fall/raw/main/week_02/images/responsetime.jpg" title="Response Time" width="300" >}}

{{< figure src="https://github.com/gustybear-teaching/course_ee693e_2021_fall/raw/main/week_02/images/successrate.jpg" title="Success Rate with One Round" width="300" >}}

{{< figure src="https://github.com/gustybear-teaching/course_ee693e_2021_fall/raw/main/week_02/images/multipleattempts.jpg" title="Success Rate with Multiple Rounds" width="300" >}} -->

### Discussion


### Questions
(1) Do you think other biometrics can be used for H2H? Something other than PV?

- Respiration measurements can be also used for authentication. The proposal of this paper might have a different approach since statistics might be different than ECGs. 

(2) Would there be a noticable difference in running time for the algorithm shown? Is it worth improving the n4logn time complexity?
- It is possible to improve time complexity of the algorithm by using another sorting algorithm. Further research has to be conducted. 

(3) Would x86 or other CISC architecture offer a better performance in place of the ARM architecture?
- Any processor can be used for the IMD. It should be best to choose a processor that consumes less power.

