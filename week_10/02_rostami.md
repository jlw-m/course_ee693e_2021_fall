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

