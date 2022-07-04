---

---

# NewsBites Volume XXIV – Issue 51  SANS NewsBites


1.  [Home](chrome-extension://pcmpcfapbekmbjjkdalcgopdkipoggdi/)
2.  [Newsletters](chrome-extension://pcmpcfapbekmbjjkdalcgopdkipoggdi/newsletters/)
3.  [SANS NewsBites](chrome-extension://pcmpcfapbekmbjjkdalcgopdkipoggdi/newsletters/newsbites)
4.  Malicious Python Modules Found on PyPI;...

SANS NewsBites

## Malicious Python Modules Found on PyPI; Oracle Finally Patches Complex Critical Flaw; FTC Fines Residual Pumpkin for Café Press Breach and Applies Sanctions to Acquirer Planet Art, Too

June 28, 2022  |  Volume XXIV - Issue #51

## Top of the News

___

2022-06-25

### Malicious Python Packages Uploaded Data to Publicly Exposed Endpoints

Sonatype detected several malicious Python packages on the PyPI repository that have been stealing sensitive information, including AWS credentials, and uploading it to publicly exposed endpoints. Sonatype has reported the malicious packages to PyPI; the packages have been removed from the repository.

#### Editor's Note

Another day, another malicious Python package. Sonatype is making a good case for not only scanning code you write, but also scanning code you are using from repositories like PyPi.

![Johannes Ullrich](https://images.contentstack.io/v3/assets/blt36c2e63521272fdc/blt072a994e5736ae1f/5e9a419445a2a97194a1d4b5/370x370_Johannes-Ullrich.jpg)

##### Johannes Ullrich

A reminder to not just trust modules provided externally. Make sure that you're using the version you've qualified versus an imposter with “added functionality.” Even so, you're doing static and dynamic code analysis, right? Consider limiting outbound connections to prevent connection to C2 services.

![Lee Neely](https://images.contentstack.io/v3/assets/blt36c2e63521272fdc/blt287a7a830c1223e8/60285112efec26565b3dc240/Lee-Neely-headshot-768x1024.png)

##### Lee Neely

Developers are reminded that they are responsible for the quality of all code that they include or distribute in their products, regardless of its source.

![William Hugh Murray](https://images.contentstack.io/v3/assets/blt36c2e63521272fdc/blt87790c02b0e2371c/60285133dcc0d576d2f9369f/William_High_Murray.jpg)

##### William Hugh Murray

#### Read more in

___

2022-06-24

### Oracle Took Six Months to Fix Critical Flaw in Fusion Middleware

Researchers say that six months elapsed between the time they notified Oracle of a critical vulnerability in Fusion Middleware and the day Oracle released a fix for the issue. The deserialization of untrusted data vulnerability can be exploited remotely without authentication to allow arbitrary code execution. The researchers notified Oracle of the flaw in October 2021; Oracle fixed the issue in its April 2021 Critical Patch Update.

#### Editor's Note

Deserialization issues are all too common in middleware, and can be difficult to patch right. The usual fix employed by Oracle in the past is to establish blocklists to not allow the instantiation of very specific, deemed to be dangerous, objects. But these blocklists have been bypassed in the past if they were not defined well. A huge ecosystem of applications relies on this middleware and Oracle does need to pay attention to minimize the possibilities of breaking these applications.

![Johannes Ullrich](https://images.contentstack.io/v3/assets/blt36c2e63521272fdc/blt072a994e5736ae1f/5e9a419445a2a97194a1d4b5/370x370_Johannes-Ullrich.jpg)

##### Johannes Ullrich

As we’ve seen with Microsoft and many other vendors of large complex software, some software flaws can take several months to fix and test. But, Oracle has been silent on why this one took so long or in providing any guidance to customers in shielding or workaround actions to take while awaiting a real fix.

![John Pescatore](https://images.contentstack.io/v3/assets/blt36c2e63521272fdc/blt52401881b1eb3b47/5ec57c253a450a58554b667a/370x370_john-pescatore.jpg)

##### John Pescatore

One exploit involves chaining two vulnerabilities, CVE-2022-21445 (deserialization of untrusted data) and CVE-2022-21497 (SSRF), to achieve pre-authentication RCE. The time to release a patch was likely due to interdependency and regression testing and resolution. You should have already deployed the April CPU. If not, the publishing of the exploit details should be seen as a call to act.

![Lee Neely](https://images.contentstack.io/v3/assets/blt36c2e63521272fdc/blt287a7a830c1223e8/60285112efec26565b3dc240/Lee-Neely-headshot-768x1024.png)

##### Lee Neely

Having been on the inside of some of these decisions, one can testify that the vendors are often between a rock and a hard place, in a dilemma that cannot be recognized or appreciated from the outside. Moreover, the vendor may be aware of many vulnerabilities more severe than those reported from the outside and is fixing them in the most efficient order. One is inclined to cut the vendor some slack. That said, six months with no explanation or guidance to customers is a little much. One starts to question the vendors priorities.

![William Hugh Murray](https://images.contentstack.io/v3/assets/blt36c2e63521272fdc/blt87790c02b0e2371c/60285133dcc0d576d2f9369f/William_High_Murray.jpg)

##### William Hugh Murray

#### Read more in

___

2022-06-27

### CafePress Fined Over Data Breach and Cover-up

The US Federal Trade Commission (FTC) has finalized an order against CafePress over a 2019 breach that compromised data for nearly 23 million accounts. CafePress kept data longer that it needed to; stored sensitive information, like Social Security numbers (SSNs), in plaintext; did not secure its systems sufficiently; and covered up the breach, electing not to inform impacted customers. The complaint was filed against former CafePress parent company Residual Pumpkin, LLC, and current CafePress owner PlanetArt, LLC. The final order requires both companies to implement comprehensive cybersecurity programs, employ multi-factor authentication, store data for only the minimum amount of time necessary, and encrypt SSNs.

#### Editor's Note

This is a good report to use to convince management of the importance of cybersecurity review being part of Merger and Acquisition decisions. Planet Art acquired Café Press after the 2019 and may have adjusted the amount they paid downward. However, 3 years later Planet Art will be subject to the FTC action on their security program, even if the original parent company (Residual Pumpkin) has to pay the fine.

![John Pescatore](https://images.contentstack.io/v3/assets/blt36c2e63521272fdc/blt52401881b1eb3b47/5ec57c253a450a58554b667a/370x370_john-pescatore.jpg)

##### John Pescatore

It's not a bad idea to review where you're storing PII and make sure you're aligned with the relevant privacy laws, (CCPA, GDPR, etc.) to include retention and appropriate use restrictions. Be sure to check online services used, such as event registration services, for data collected and stored to ensure they also meet protection requirements. Leverage your legal team to understand how these laws apply to your business. Build awareness training for both developers and users as well as creating any needed supporting KB articles and/or policies.

![Lee Neely](https://images.contentstack.io/v3/assets/blt36c2e63521272fdc/blt287a7a830c1223e8/60285112efec26565b3dc240/Lee-Neely-headshot-768x1024.png)

##### Lee Neely

#### Read more in

## The Rest of the Week's News

___

2022-06-27

### $100M Stolen from Blockchain Firm Harmony

Thieves have stolen more than $100M in cryptocurrency from blockchain company Harmony. Harmony provides bridge services for users who want to transfer cryptocurrency across different blockchains. The company’s Horizon Ethereum Bridge was compromised last week. Harmony is offering a $1M bounty for the return of the stolen funds.

#### Editor's Note

Of course, that $100M was only worth $30M a few days later… Hard to get real data on “cryptocurrency” use but it seems clear more of it is stolen each year than is used for actual business transactions.

![John Pescatore](https://images.contentstack.io/v3/assets/blt36c2e63521272fdc/blt52401881b1eb3b47/5ec57c253a450a58554b667a/370x370_john-pescatore.jpg)

##### John Pescatore

Harmony transfers cryptocurrencies, stablecoins and non-fungible tokens between their blockchain and other networks. The Ethereum tokens were what was stolen. The attackers used 11 transactions which extracted the ETH tokens on the bridge. Moreover, these were doubly encrypted via passphrase and key management service. The pilfered keys were able to satisfy the multi-signature contract allowing the funds to be transferred. The point is you need to understand how your crypto is protected, how exchanges are authorized and what recourse you have if compromised.

![Lee Neely](https://images.contentstack.io/v3/assets/blt36c2e63521272fdc/blt287a7a830c1223e8/60285112efec26565b3dc240/Lee-Neely-headshot-768x1024.png)

##### Lee Neely

#### Read more in

___

2022-06-24

### Ransomware as a Distraction from IP Theft

Researchers from Secureworks say that Chinese state-sponsored threat actors may be using ransomware as a distraction while they plumb organizations’ networks for intellectual property and other sensitive data. Secureworks has provided a list of threat indicators to help detect malicious activity related to the threat actors.

#### Editor's Note

Same is often true of denial of service attacks that are often used as distractions from the main tactics, or are used simply to flood SIEM consoles with alerts that will slow the security team from handling the critical alerts.

![John Pescatore](https://images.contentstack.io/v3/assets/blt36c2e63521272fdc/blt52401881b1eb3b47/5ec57c253a450a58554b667a/370x370_john-pescatore.jpg)

##### John Pescatore

View this as a twist to current ransomware + extortion techniques. The ransomware is used to obfuscate evidence, distract investigators and otherwise cover the indications relating to exfiltration of data. The attackers are using the HUI loader, which is a custom DLL loaded by legitimate programs subject to DLL search order hijacking. The loader then installs a RAT such as Cobalt Strike, PlugX, SodaMaster and QuasarRAT. The attack leverages weaknesses in your boundary control devices, taking us back to making sure they are patched, the configuration is verified as secure, and you're using MFA for remote access. Leverage the IOCs in the Secureworks article.

![Lee Neely](https://images.contentstack.io/v3/assets/blt36c2e63521272fdc/blt287a7a830c1223e8/60285112efec26565b3dc240/Lee-Neely-headshot-768x1024.png)

##### Lee Neely

#### Read more in

___

2022-06-24

### GAO: Private Cyber Insurance, TRIP May Not be Enough to Cover Catastrophic Losses

The US Government Accountability Office (GAO) is concerned that currently available private cyber event insurance and the government’s Terrorism Risk Insurance Program (TRIP) may not be sufficient to cover catastrophic financial losses due to cyberattacks. GAO recommends that “CISA and the Department of the Treasury's Federal Insurance Office (FIO) should jointly assess the extent to which risks to critical infrastructure from catastrophic cyber incidents and potential financial exposures warrant a federal insurance response, and inform Congress of the results of their assessment.”

#### Editor's Note

The key line in this 53 page report is “One option that has been proposed is to tie federal assistance for cyber-related losses to cybersecurity requirements.” Insurance can’t cover catastrophic losses that are due to lack of basic security hygiene. Like any form of insurance, to be useful to businesses, or for the government to step in when state-sponsored or terrorist-initiated attacks cause broad damage, cyberinsurance policies have to be based on proof of maintaining baseline standards. In this case, the government will likely point to the NIST framework.

![John Pescatore](https://images.contentstack.io/v3/assets/blt36c2e63521272fdc/blt52401881b1eb3b47/5ec57c253a450a58554b667a/370x370_john-pescatore.jpg)

##### John Pescatore

Insurance companies have been revising language and criteria in response to trends in ransomware claims. Review your cyber insurance to understand what it covers and what are the triggers. For example, the GAO believes that incidents may not meet the criteria needed to be categorized as terrorism, resulting in a non-payment. Determine if there are new criteria, such as vulnerability assessments or MFA you are also now required to meet for your insurance to be valid, don't delay closing any gaps here.

![Lee Neely](https://images.contentstack.io/v3/assets/blt36c2e63521272fdc/blt287a7a830c1223e8/60285112efec26565b3dc240/Lee-Neely-headshot-768x1024.png)

##### Lee Neely

#### Read more in

___

2022-06-24

### CISA: Assume VMware Products Not Patched Against Log4Shell are Compromised

In a joint cybersecurity advisory, the US Cybersecurity and Infrastructure Security Agency (CISA) and the United States Coast Guard Cyber Command (CGCYBER) warn that threat actors are continuing to exploit Log4Shell in VMware Horizon® and Unified Access Gateway (UAG) servers. CISA and CGCYBER urge organizations with vulnerable systems to assume compromise and begin threat hunting action using the indicators of compromise included with the advisory.

#### Editor's Note

VMware released fixes for Log4J back in December. If you have any systems which are still not updated, you're going to want to forensicate them fully before trusting them. Make sure that you're minimizing the services exposed to the Internet, that accounts are audited, removing which are unused or no-longer-needed. Lastly, strong authentication is pretty important, don't overlook it, keep an eye on excepted users, find a way to not have any exceptions.

![Lee Neely](https://images.contentstack.io/v3/assets/blt36c2e63521272fdc/blt287a7a830c1223e8/60285112efec26565b3dc240/Lee-Neely-headshot-768x1024.png)

##### Lee Neely

Post SolarWinds, assuming persistent but covert compromise, might well be the appropriate default. In the face of such compromise, the efficient defensive strategy is strong process-to-process isolation. The goal should be so-called “zero trust.”

![William Hugh Murray](https://images.contentstack.io/v3/assets/blt36c2e63521272fdc/blt87790c02b0e2371c/60285133dcc0d576d2f9369f/William_High_Murray.jpg)

##### William Hugh Murray

#### Read more in

___

2022-06-22

### CISA Asks for Feedback on Trusted Internet Connections 3.0 Cloud Use Case

The US Cybersecurity and Infrastructure Security Agency (CISA) is seeking feedback and comments on its Trusted Internet Connections (TIC) 3.0 Cloud Use Case. This rounds out the series of TIC use cases: CISA released the Traditional TIC Use Case, Branch Office Use Case, and Remote User Use Case last year. “The goal of TIC 3.0 is to secure federal data, networks, and boundaries while providing visibility into agency traffic, including cloud communications.” CISA is accepting public comment on the TIC 3.0 Cloud Use Case through July 22, 2022.

#### Editor's Note

TIC is a mixed bag. In some scenarios such as HPC, a non-starter for effective connectivity across the internet. The goal is to achieve a version of TIC which is aligned with Zero-Trust and a cloud based service architecture. Take a hard look at the draft and provide feedback to ensure the end model is usable.

![Lee Neely](https://images.contentstack.io/v3/assets/blt36c2e63521272fdc/blt287a7a830c1223e8/60285112efec26565b3dc240/Lee-Neely-headshot-768x1024.png)

##### Lee Neely

#### Read more in

___

2022-06-24

### Google: Hermit Spyware is Being Used in Italy and Kazakhstan

Google says that spyware from Italian company RCS Labs is being used to target people in Italy and Kazakhstan. The spyware, known as Hermit, targets both iOS and Android devices, and uses drive-by downloads to gain initial footholds on targeted devices. Hermit can steal data from infected phones and can also make and record calls.

#### Editor's Note

The malicious applications masquerade as account recovery applications. Consider carefully requests to install applications to support actions like this, verify, out-of-band that they are indeed part of the process. Make sure that your users understand the recovery processes for accounts associated with applications they use. Make sure that users only install applications from trusted app stores, including what to do when they are requested to install one from another source.

![Lee Neely](https://images.contentstack.io/v3/assets/blt36c2e63521272fdc/blt287a7a830c1223e8/60285112efec26565b3dc240/Lee-Neely-headshot-768x1024.png)

##### Lee Neely

#### Read more in

___

2022-06-22

### ToddyCat APT

Researchers at Kaspersky have discovered an advanced persistent threat (APT) actor that is exploiting the ProxyLogon vulnerability in targeted attacks against government and military organizations in Europe and Asia. Dubbed ToddyCat, the threat actor does not appear to have ties to other known threat actors. ToddyCat uses two tools, also not seen before, that Kaspersky is calling ”Samurai backdoor” and “Ninjas Trojan.” The tools are being used to exploit two backdoors in the Exchange Server environment. Targeting Exchange Servers.

#### Editor's Note

The China Chopper web shell is installed, which allows for svchost to load the malicious "iiswmi.dll" which then uses a .Net loader to execute the Samurai backdoor; which is hard to detect. The SecureList blog post includes IOCs for you to incorporate into your processes to discover this activity. Make sure your Exchange infrastructure is up to date. Given the low-profile of this attack group, proactively scanning for the IOCs is a good idea.

![Lee Neely](https://images.contentstack.io/v3/assets/blt36c2e63521272fdc/blt287a7a830c1223e8/60285112efec26565b3dc240/Lee-Neely-headshot-768x1024.png)

##### Lee Neely

#### Read more in

## Internet Storm Center Tech Corner