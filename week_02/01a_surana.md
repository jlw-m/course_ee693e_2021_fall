---
title: "01a: Deploying a Rural Wireless Telemedicine System: Experiences in Sustainability
Sonesh Surana, Rabin Patra, Sergiu Nedevschi, and Eric Brewer"
date: 2021-08-30
type: book
commentable: true

# Provide the name of the presenter
summary: "Presenter(s): Nguyen Banh, Saige Dacuycuy, Beenet Alemayehu"

# Provide other tags that describe the paper
tags:
- teaching
- ee693e

---

***
## Paper Summary
While there is a belief that information and communication technology (ICT) may have a major effect on development, developing sustainable ICT initiatives is challenging in reality. A typical project begins with a pilot stage to establish fundamental objectives, followed by a deployment stage focused on scalability and sustainability. In rural India, an ICT initiative is using long-distance Wi-fi networking to provide high-quality telemedicine between eye clinics and distant communities. TIER assisted Aravind Eye Care System (www.aravind.org) in southern India with the deployment of a rural wireless telemedicine system. Aravind plans to expand the Theni network to 50 locations if this initiative is successful. Within three years, the network's full capacity is anticipated to conduct 500,000 examinations per year and offer eye care to a rural population of 2.5 million.
***

## Presentation
{{< youtube C2LOWF_K-FM >}}

***

## Review
### Strengths
- Optimizing the current system: required to increase rural residents' access to eye care systems.
- Financial sustainability results: achieved positive cash flow which means the monthly revenue can cover the monthly expense.
- Operational sustainability results: 
    - Improving power quality has reduced the number of power-related router downtimes, 
    - Limit downtime periods to under one day, 
    - Eliminated CF card corruptions.
    - Operational responsibility for the network has migrated from Tier 3 to local staff (Tier 1).

### Weaknesses
- Limited local expertise
  - Misconfiguration
  - Limited diagnostic capabilities
  - Equipment misuse.
- Hardware and software failures
  - Poor-quality power
- Lack of connectivity
  - Have to physically go on site
- Lack of physical access
  - Remote locations are far or hard to access

### Detailed Comments
They educate both local employees and local suppliers, although the latter have a stronger IT background and are more equipped to tackle more complex problems. India is experiencing an ophthalmologist deficit, with 90% of physicians located in metropolitan regions. Aravind vision centers use a wireless local-loop technology, or VC, that is provided by a local carrier. A counselor follows up with patients after a doctor's diagnosis at the base hospital. A VC visit costs the patient 25 cents.

In two years, the Aravind-Theni telemedicine network allowed 51,205 remote eye exams. 96 percent of Aravind patients who get cataracts lose their ability to work. Long-distance connection through Wi-Fi is a low-cost option for remote hospitals. Wi-Fi significantly lowers deployment and operating expenses in a variety of ways. Additionally, it provides the hospital with the operational flexibility to establish connections whenever and wherever they are required.

As the connection distance grows, the chance of two end-hosts initiating transmission inside a window defined by proportionately rising propagation delay rises as well. WiLDNet was developed by the Wildnet team to solve these concerns. While power outages in rural India are common, we were shocked at the extent of poor power quality. When disconnected from the grid, low-quality electricity flows via low-quality devices. It took us days and a significant financial investment to install or repair equipment.

A 10-year-old solar panel costs $8.24, or approximately 35% more per kilowatt-hour than grid electricity. A UPS with enough battery capacity to last three days during an outage costs $6.08 per month, or about 24 times higher.

TIER's main objective is to improve system availability, reduce operational costs, and eventually delegate operational responsibilities to local teams. We developed a monitoring system, alternate back-channels for remote management in the event of connection failures, and self-recovery mechanisms, all of which contributed to increased operational sustainability. A critical component of automatic recovery is a system reboot initiated by a watchdog processor. Referral revenue covers 20% of the cost of cataract operations performed at the base hospital on patients recommended by the center. The following table summarizes the profits of Theni's five venture capitalists.

Bodi maintained a positive cash flow in 2006 and 2007 after accounting for both construction and operational costs associated with the network. Aravind is expanding the vision center network to 50 locations. Aravind's vision centers have been a tremendous success, benefiting both the hospitals and the patients. Over 50,000 virtual patient-doctor consultations have been conducted in the system's first two years of operation. Aravind has delegated operational responsibilities for the network to local employees.


##Audience Questions
In Table-1 it is showing they calculated the monthly cost with 8% interest (last column). What is the rationel/reasoning behind considering 8% interest? 

In the article the authors stated that “the last column includes interest on borrowed capital that is typically used to pay up-front costs.” Take a look at the interest rate a couple of years back since 2008 which is the paper’s publication date. Although they have lower interest rates at that time, in the past the interest rate can go up to 8% or 9%.


Why do you think improving community awareness in rural areas for “eye camps” beforehand is not one of their targeted areas of improvement for the eye care system before trying to implement telemedicine?

The authors stated that “Aravind’s first strategy to address needless blindness was to conduct periodic “eye camps” in rural areas.” So “eye camps” are an attempt to improve community awareness in rural areas. But the result from “eye camps” only reached 7% of the population and did not solve the issue of doctor scarcity. 
