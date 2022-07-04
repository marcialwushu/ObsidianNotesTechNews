---
link: https://www.sans.org/newsletters/newsbites/xxiv-50/
date: 03-07-2022
tags: SANS, security
---

1.  [Home](chrome-extension://pcmpcfapbekmbjjkdalcgopdkipoggdi/)
2.  [Newsletters](chrome-extension://pcmpcfapbekmbjjkdalcgopdkipoggdi/newsletters/)
3.  [SANS NewsBites](chrome-extension://pcmpcfapbekmbjjkdalcgopdkipoggdi/newsletters/newsbites)
4.  US DoE Says Build Security Into All...

SANS NewsBites

## US DoE Says Build Security Into All Energy Systems; PowerShell Securely Configured is Better Than No PowerShell at All; OT Devices Are Not Secure and Need to Be Segmented/Shielded

June 24, 2022  |  Volume XXIV - Issue #50

## Top of the News

___

2022-06-21

### US DoE’s National Cyber-Informed Engineering Strategy

The US Department of Energy (DOE) has released its Cyber-Informed Engineering (CIE) Strategy. DoE’s publication notes that “CIE is an emerging method to integrate cybersecurity considerations into the conception, design, development, and operation of any physical system that has digital connectivity, monitoring, or control. CIE approaches use design decisions and engineering controls to mitigate or even eliminate avenues for cyber-enabled attack, or reduce the consequences when an attack occurs.” DoE’s CIE Strategy is supported by five pillars: awareness, education, development, current infrastructure, and future infrastructure.

#### Editor's Note

I’m not a big fan of the term “Cyber Informed Engineering” as it implies there is still some need for engineering that is NOT “cyber-informed.” The strategy is basically well known and proven “build security in” or “secure by design” concepts that should be integrated into all energy system operational, upgrade, and new system efforts. Given that the world’s energy systems will change quite a bit over the next 20 years, now is the time to do that.

![John Pescatore](https://images.contentstack.io/v3/assets/blt36c2e63521272fdc/blt52401881b1eb3b47/5ec57c253a450a58554b667a/370x370_john-pescatore.jpg)

##### John Pescatore

This is the most hopeful thing that one has heard in this space. In most industries we know what to do; we simply lack the will to do it. The energy sector is an exception. Because of the interdependencies in the grid, securing it is more complex than simply securing all the operators in the grid. Here, we need a strategic approach that goes across enterprises.

![William Hugh Murray](https://images.contentstack.io/v3/assets/blt36c2e63521272fdc/blt87790c02b0e2371c/60285133dcc0d576d2f9369f/William_High_Murray.jpg)

##### William Hugh Murray

This sprang from the 2019 National Defense Authorization Act for Fiscal Year 2020 which directed DOE to create this CIE strategy. Part of the idea is to engineer a system which is resistant to further attack once penetrated. The CIE in practice summary explains how this should be considered. Note that while this applies to critical infrastructure, there is applicability to important IT systems. Ask if system A is compromised, what could then be reached easily and how you could slow or stop the effectiveness of that lateral movement.

![Lee Neely](https://images.contentstack.io/v3/assets/blt36c2e63521272fdc/blt287a7a830c1223e8/60285112efec26565b3dc240/Lee-Neely-headshot-768x1024.png)

##### Lee Neely

#### Read more in

___

2022-06-23

### US, UK, New Zealand: Make Sure PowerShell is Securely Configured

Cybersecurity authorities in the UK, the US, and New Zealand have jointly released guidance urging organizations to ensure that they are using secure configurations of PowerShell, and recommending against disabling or removing the command-line tool. The guidance offers specific advice for using PowerShell to detect and reduce abuse.

#### Editor's Note

PowerShell has gotten a bit of a bad reputation. Many attackers use it to their advantage after they gain access to a system. But there are also many defensive opportunities, and this concise document does a great job in not only outlining how to restrict PowerShell but also showing how to detect malicious uses.

![Johannes Ullrich](https://images.contentstack.io/v3/assets/blt36c2e63521272fdc/blt072a994e5736ae1f/5e9a419445a2a97194a1d4b5/370x370_Johannes-Ullrich.jpg)

##### Johannes Ullrich

PowerShell 5 should be removed in favor of version 7 for windows 10/11 and Linux which adds needed security features such as SSH remoting and over-the-shoulder transcription. Leverage the AMSI integration as well as application control to enabler integration with anti-malware components on the endpoint and to restrict what PowerShell is permitted to do. Review the Defense document below for more on detection and properly securing PowerShell.

![Lee Neely](https://images.contentstack.io/v3/assets/blt36c2e63521272fdc/blt287a7a830c1223e8/60285112efec26565b3dc240/Lee-Neely-headshot-768x1024.png)

##### Lee Neely

This is an excellent resource and one I encourage all cybersecurity professionals to read and implement. In many investigations we investigate we see PowerShell being abused by criminals.

![Brian Honan](https://images.contentstack.io/v3/assets/blt36c2e63521272fdc/blte0f24e9999282d80/60285466dcc0d576d2f936a3/Brian_Honan.jpeg)

##### Brian Honan

#### Read more in

___

2022-06-23

### Multiple Vulnerabilities in Operational Technology Devices

Researchers from Forescout’s Vedere Labs have published a report detailing 56 vulnerabilities affecting operational technology (OT) devices. The vulnerabilities affect products from 10 vendors, including Honeywell, Emerson, Motorola, Siemens, JTEKT, Bentley Nevada, Phoenix Contact, Omron, and Yogogawa. The vulnerabilities include remote code execution (RCE); denial-of-service (DoS); file/firmware/configuration manipulation; compromise of credentials; and authentication bypass.

#### Editor's Note

The sad part is not the number of the vulnerabilities, but the type of vulnerabilities. It shows how many of these OT devices controlling critical infrastructure suffer from vulnerabilities that home security systems fixed (for the most part) years ago.

![Johannes Ullrich](https://images.contentstack.io/v3/assets/blt36c2e63521272fdc/blt072a994e5736ae1f/5e9a419445a2a97194a1d4b5/370x370_Johannes-Ullrich.jpg)

##### Johannes Ullrich

Operational Technology (OT) covers an enormous range of devices and uses. The only real common denominator is they all started out without thinking at all about “build security in” or “secure by design.” The only hope of changing that is making sure those requirements/concepts are part of procurements of new equipment – any OT items in use today have to be segmented/shielded etc.

![John Pescatore](https://images.contentstack.io/v3/assets/blt36c2e63521272fdc/blt52401881b1eb3b47/5ec57c253a450a58554b667a/370x370_john-pescatore.jpg)

##### John Pescatore

The guidance from Forescout, resulting from their OT:ICEFALL project, is to not wait for CVEs for your OT prior to taking actions to secure them. They have manufacturer-specific recommendations and segmentation, monitoring, patching, and identification of vulnerabilities are a good idea across the board. Make sure that your scanning and assessment teams know how to interact with OT/ICS systems without doing harm.

![Lee Neely](https://images.contentstack.io/v3/assets/blt36c2e63521272fdc/blt287a7a830c1223e8/60285112efec26565b3dc240/Lee-Neely-headshot-768x1024.png)

##### Lee Neely

#### Read more in

## The Rest of the Week's News

___

2022-06-21

### Malware Infects Networks at Two Texas Hospitals

Two Texas hospitals have notified patients that their personal health information (PHI) may have been compromised after the organizations’ networks were infected with malware. Baptist Medical Center and Resolute Health Hospital learned of the breach in April. The potentially compromised data include Social Security numbers, health insurance information, diagnoses, and billing information.

#### Editor's Note

Looks like attackers had over 3 weeks on target, including 4 days after the malware was first detected. Not a lot of data on this one, but looks like 1.2M individuals impacted, so this is an expensive one – just the costs of offering identity theft protection are likely to exceed the proactive cost that would have avoided or minimized the damage.

![John Pescatore](https://images.contentstack.io/v3/assets/blt36c2e63521272fdc/blt52401881b1eb3b47/5ec57c253a450a58554b667a/370x370_john-pescatore.jpg)

##### John Pescatore

We've been noting the security of health devices, and focusing on segmentation, access control and updates; don't forget the back-end systems. Ensure sufficient protections are in place not only from medical systems but also any public facing system. You say you have your IDS and WAF all set - have you verified they work? Nothing in learning mode? That someone is responding to configured alerts?

![Lee Neely](https://images.contentstack.io/v3/assets/blt36c2e63521272fdc/blt287a7a830c1223e8/60285112efec26565b3dc240/Lee-Neely-headshot-768x1024.png)

##### Lee Neely

#### Read more in

___

2022-06-22

### Cloudflare Outage Due to Network Configuration Issue

An outage affecting traffic in 19 Cloudflare data centers on Tuesday, June 21, was the result of a problematic network configuration change. The outage caused some websites and services to become unavailable. The issue was resolved within 90 minutes.

#### Editor's Note

It is becoming a buzzword to call information/cybersecurity “resiliency,” but this incident is an important reminder that security is really a subset of overall reliability/resilience. While Availability has been part of the Confidentiality/Integrity/Availability triad forever, security issues generally aren’t the top driver of downtime in most organizations. Important to plan for how IT admin code changes that crash systems or network admin config changes that cause self-inflicted denial of service storms impact your ability to continue to deliver security services.

![John Pescatore](https://images.contentstack.io/v3/assets/blt36c2e63521272fdc/blt52401881b1eb3b47/5ec57c253a450a58554b667a/370x370_john-pescatore.jpg)

##### John Pescatore

Even the best of us get bit by BGP changes. Cloudflare is working to make their architecture more robust and less susceptible to network configuration errors. In so doing the configuration updates to that model resulted in the same outages they wish to avoid. When successful their architecture and lessons learned can be leveraged to help others become more resistant to these issues.

![Lee Neely](https://images.contentstack.io/v3/assets/blt36c2e63521272fdc/blt287a7a830c1223e8/60285112efec26565b3dc240/Lee-Neely-headshot-768x1024.png)

##### Lee Neely

#### Read more in

___

2022-06-23

### CISA Publishes Revised Version of Cloud Security Technical Reference Architecture

The US Cybersecurity and Infrastructure Security Agency (CISA) has released the second version of its Cloud Security Technical Reference Architecture (TRA), which provides guidance for federal agencies to securely migrate to cloud services. The first version of the Cloud Security TRA was published in September 2021.

#### Editor's Note

With many organisations engaging with the cloud over the past two years as a result of the pandemic, this is a good resource to use to review and ensure any migrations to the cloud your organization has undertaken is done so in a secure way.

![Brian Honan](https://images.contentstack.io/v3/assets/blt36c2e63521272fdc/blte0f24e9999282d80/60285466dcc0d576d2f936a3/Brian_Honan.jpeg)

##### Brian Honan

#### Read more in

___

2022-06-23

### New US Cybersecurity Laws

Two US cybersecurity-related bills have been signed into law. The Federal Rotational Cyber Workforce Program Act of 2021 paves the way for IT, cybersecurity, and related workers to use their skills across multiple agencies. The Local Government Cybersecurity Act “fosters cybersecurity coordination between the Department of Homeland Security and state and local actors.”

#### Editor's Note

This should make it easier to work cross-agency, and while DHS and CISA have the charter and authority, this removes many barriers to success.

![Lee Neely](https://images.contentstack.io/v3/assets/blt36c2e63521272fdc/blt287a7a830c1223e8/60285112efec26565b3dc240/Lee-Neely-headshot-768x1024.png)

##### Lee Neely

#### Read more in

___

2022-06-22

### Cyberattack May Have Set Off Israeli Air Raid Sirens

The Israeli National Cyber Directorate (INCD) suspects that a cyberattack may be responsible for air raid sirens sounding in Jerusalem and Eilat on Sunday, June 19. The affected sirens were municipal rather than military. INCD published suggested remediations for similar systems.

#### Editor's Note

While this is likely just Iran poking at Israel as part of their ongoing disputes, it's still a good idea to make sure that you have properly secured your emergency communication systems, that access is regularly verified, to include new integrations or connections to ensure the level of security is not reduced over time. Excessive false positives, or even too much testing, will reduce their effectiveness in a true emergency.

![Lee Neely](https://images.contentstack.io/v3/assets/blt36c2e63521272fdc/blt287a7a830c1223e8/60285112efec26565b3dc240/Lee-Neely-headshot-768x1024.png)

##### Lee Neely

#### Read more in

___

2022-06-23

### CISA Warns of Hillrom Medical Device Vulnerabilities

The US Cybersecurity and Infrastructure Security Agency (CISA) has issued a warning about two vulnerabilities affecting Hillrom Medical heart monitors. Hillrom is releasing updates to fix the hard-coded password and improper access control issues.

#### Editor's Note

>Hillrom is releasing more than one patch. Note the timelines for the fixes, some due in late 2023.


![Lee Neely](https://images.contentstack.io/v3/assets/blt36c2e63521272fdc/blt287a7a830c1223e8/60285112efec26565b3dc240/Lee-Neely-headshot-768x1024.png)

##### Lee Neely

#### Read more in

___

2022-06-22

### Bill Would Require Regular Medical Device Security Requirement Updates from FDA

US legislators are considering a bill that would require the Food and Drug Administration (FDA) to update medical device cybersecurity requirements regularly. The Strengthening Cybersecurity for Medical Devices Act would require the FDA to review and amend premarket medical device cybersecurity guidance every two years.

#### Read more in

___

2022-06-23

### NSO Group: At Least Five European Countries Use Pegasus Surveillance Tool

NSO Group has admitted that its Pegasus surveillance tool has been used by at least five European countries. NSO Group also said it terminated a contract with one country that was abusing the Pegasus software.

#### Read more in

## Internet Storm Center Tech Corner

