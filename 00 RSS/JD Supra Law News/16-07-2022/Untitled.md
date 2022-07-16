Cognitive Techniques for Early Detection
of Cybersecurity Events
Sandeep Narayanan, Ashwinkumar Ganesan, Karuna Joshi, Tim Oates, Anupam Joshi and Tim Finin

arXiv:1808.00116v1 [cs.CR] 1 Aug 2018

Department of Computer Science & Electrical Engineering
University of Maryland, Baltimore County, Baltimore, MD, USA
{sand7, gashwin1, kjoshi1, oates, joshi, finin}@umbc.edu

Abstract—The early detection of cybersecurity events such as
attacks is challenging given the constantly evolving threat landscape. Even with advanced monitoring, sophisticated attackers
can spend as many as 146 days1 in a system before being detected.
This paper describes a novel, cognitive framework that assists
a security analyst by exploiting the power of semantically rich
knowledge representation and reasoning with machine learning
techniques. Our Cognitive Cybersecurity system ingests information from textual sources, and various agents representing host
and network based sensors, and represents this information in a
knowledge graph. This graph uses terms from an extended version of the Unified Cybersecurity Ontology. The system reasons
over the knowledge graph to derive better actionable intelligence
to security administrators, thus decreasing their cognitive load
and increasing their confidence in the system. We have developed
a proof of concept framework for our approach and demonstrate
its capabilities using a custom-built ransomware instance that is
similar to WannaCry.

I. I NTRODUCTION
Cybersecurity threats and associated costs to organizations
are surging. About 23,000 [24] new malware samples are
produced daily and a company’s average cost for a data breach
is about $3.4 million (according to Microsoft [16]). Many
corporate enterprises fell prey to cybersecurity attacks because
of the time gap between the exploit becoming public and
patching their systems. For example, consider the time line of
the wannacry ransomware, which uses an SMB vulnerability
in Windows 7 machines for gaining access to victim systems.
On March 14 2017, Microsoft Security Bulletin [18] and Cisco
NGFW published this vulnerability. A hacker group, Shadow
Brokers [8], released a set of vulnerabilities including Eternal
Blue and Double Pulsar on April 14, 2017.
By Mid-May, the actual wannacry ransomware, which
exploits the SMB vulnerability using Eternal Blue started
spreading2 . Had enterprises patched their systems or properly
configured their intrusion detection systems to detect the
vulnerability, the wide-scale spread of this ransomware, which
infected over two hundred thousand victims, could have been
prevented. Such incidents reveal how critical it is to be aware
of newly reported vulnerabilities and attacks. However, due to
the avalanche of threat intelligence information from sources
like chat forums, security bulletins, blogs and reports, security
analysts find it difficult to keep track of all such information.

Variations of the same cyber-attack is another concern for
attack detection. When attacks become popular, security companies release signatures to detect them. To evade detection,
attackers often modify the attack or use different modes to
attack. An example is the Petya ransomware3 attack, which
was discovered in 2016. It spread via email attachments
and infected computers running Windows, overwriting the
Master Boot Record (MBR), installing a custom boot loader,
and forcing a reboot. The custom boot-loader encrypts all
Master-File-Table (MFT) records, rendering the complete file
system unreadable. The attack did not succeed in large-scale
infections. However, another attack resurfaced in 2017 sharing
significant code with Petya. Instead of using email attachments
to spread, the new attack, named NotPetya, used Eternal Blue
to spread.
Advanced Persistent Threats (APTs) are another class of
attacks that are difficult to detect. APT attacks tend to be
sophisticated and the attackers are persistent over a long
period of time [14][25]. The attackers gain illegal access to an
organization’s network and may go undetected for a significant
time period, with the complete scope of attack remaining
unknown. Unlike other common threats, such as viruses and
trojans, APTs are implemented in multiple stages [25]. The
stages broadly include a reconnaissance (or surveillance) of
the target network or hosts, gaining illegal access & payload
delivery, and execution of malicious programs [7]. Although
these steps remain the same, the specific vulnerabilities used to
perform them might change from one APT to another. Hence
an important challenge when creating new approaches to detect
threats (or APTs) is designing systems that can easily adapt
to the evolving threat landscape, and detect attacks early (i.e.,
”left of exploit” in the ”Cyber Kill Chain”.)
Modern Security Information and Event Management
(SIEM) systems emerged when early security monitoring
systems like Intrusion Detection Systems (IDS), and Intrusion
Detection and Prevention Systems (IDPS) started to flood the
security analyst with alerts. LogRhythm, Splunk, IBM, and
AlienVault are just a few of the commercially [9] available
SIEM systems. A typical SIEM collects security log events
from a large array of machines in a big enterprise, aggregates
this data centrally, and does simple analyses to provide security
analysts with information. However, despite ingesting large

1 https://thebestvpn.com/cybersecurity-statistics-2018/
2 https://en.wikipedia.org/wiki/WannaCry

ransomware attack

3 https://blog.checkpoint.com/2016/04/11/decrypting-the-petya-ransomware/

volumes of host/network sensor data, SIEM reports are hard
to understand, noisy, and not actionable [28]. Noise in SIEM
reports bothers 81% of users as reported in a survey [29]
on SIEM efficiency. What is missing in such systems is
the integration of threat intelligence from disparate sources
and efficient interpretation of data using known intelligence.
This can reduce false positives and improve the current state
of the art in this domain. Equally important, it reduces the
cognitive load on the analyst, because the system can fuse
threat intelligence with observed data to detect attacks early,
ideally before the exploit has started.
In this paper, we describe a cognitive strategy to assimilate
and process information from a wide variety of traditional
and non-traditional sources. A key challenge with textual
sources like blogs and security bulletins, is their inherent
incompleteness. They are often written for specific audiences
and do not explain or define what each term means. For
example, an excerpt from the Microsoft security bulletin is
“The most severe of the vulnerabilities could allow remote
code execution if an attacker sends specially crafted messages
to a Microsoft Server Message Block 1.0 (SMBv1) server.”.
Since this is intended for experts in computer science, the rest
of the text will not describe what a remote code execution or
SMB server is.
To fill this gap, we use the Unified Cybersecurity Ontology
[27] to represent the cybersecurity domain knowledge. It
provides a common ontology for information from a disparate
stream of sources and gives a combined/unified view of the
data. Concepts and standards from different intelligent sources
like STIX [5], CVE [17], CCE, CVSS, CAPEC, CYBOX,
KillChain, and STUCCO can be represented directly using
UCO.
We have developed a proof of concept system that ingests
information from textual sources, combines it with knowledge
about the state of the system as observed by host and network
sensors, and reasons over them to detect known and potentially
unknown attacks. We developed multiple agents, including a
process monitoring agent, a file monitoring agent and a snort
agent, that run on respective machines and deliver knowledge
to the Cognitive CyberSecurity (CCS) module. The CCS
module then reasons over the data and knowledge to detect
cybersecurity events and reports them to the security analyst
using a dashboard interface as described in section V. We also
developed a custom ransomware program, similar to wannacry,
to test and evaluate the capabilities of our prototype system.
Its design and working are described in detail in section V-B.
We build upon our earlier work in this domain [19].
In the following sections, we describe in detail the various
approaches that are similar to our work (section II), a detailed
description of CCS and how it works (section III), the system
architecture (section IV) and evaluation of our system using
a simulated ransomware attack (section V) to showcase the
effectiveness of the approach.

II. R ELATED W ORK
A. Security & Event Management
As the complexity of threats and APTs has grown, several
companies have released commercial platforms or security
information and event management (SIEM) systems that integrate information from different sources. A typical SIEM has
a number of features such as managing logs from disparate
sources, correlation analysis of various events, and mechanisms to alert system administrators [26]. IBM’s QRadar, for
example, can manage logs, detect anomalies, assess vulnerabilities, and perform forensic analysis of known incidents
[4]. Its threat intelligence comes from IBMs X-Force [20].
Cisco’s Talos [2] is another threat intelligence system. Many
SIEMs4 , such as LogRhythm, Splunk, AlienVault, Micro Focus, McAfee, LogPoint, Dell Technologies (RSA), Elastic,
Rapid 7 and Comodo, exist in the market with capabilities
like real-time monitoring, threat intelligence, behavior profiling, data and user monitoring, application monitoring, log
management and analytics.
B. Ontology based Systems
Obrst et. al [21] detail a process to design an ontology
for the cybersecurity domain. The study is based on the
diamond model that defines malicious activity [12]. Ontologies
are constructed in a three tier architecture consisting of a
domain-specific ontology at the lowest layer, a mid-level
ontology that clusters and defines multiple domains together
and an upper-level ontology that is defined to be as universal
as possible. Multiple ontologies designed later-on have used
the above mentioned process. Oltramari et. al [22] created
CRATELO as a three layered ontology to characterize different
network security threats. The layers include an ontology for
secure operations (OSCO) that combines different domain
ontologies, a security-related middle ontology (SECCO) that
extends security concepts, and the DOLCE ontology [15] at
the higher level. In Oltramari et. al [23], a simplified version
of the DOLCE ontology (DOLCE-SPRAY) is used to show
how a SQL injection attack can be detected. Ben-Asher et.
al. [6] designed a hybrid ontology-based model combining a
network packet-centric ontology representing network-traffic
with an adaptive cognitive agent that learns how humans
make decisions while defending against malicious attacks.
The agent is based on instance-based learning theory, using
reinforcement learning to improve decision making through
experience. Gregio et. al. [10] discusses a comprehensive
ontology to define malware behavior.
Each of these systems and ontologies looks at a narrow subset of information, such as network traffic or host system information, while SIEM products do not use the vast capabilities
and benefits of an ontological approach and systems to reason
using them. In this regard, Cognitive CyberSecurity (CCS)
takes a larger and comprehensive view of security threats
by integrating information from multiple existing ontologies
4 https://www.gartner.com/reviews/market/security-information-event-management/
compare/logrhythm-vs-logpoint-vs-splunk

as well as network & host-based sensors (including system
information) to first create a single representative view of the
data for system administrators and then provide a framework
to reason across these various sources of data.
This paper significantly improves our previous work [19] in
this domain, where semantic rules were used to detect cyber
attacks. CCS uses the Unified Cybersecurity Ontology (UCO)
which is a sophisticated and STIX compliant Ontology to
represent the knowledge in this domain. Current extensions
to it help linking standard cyber kill chain phases to various
host behaviors and network behaviors that are detected by
traditional sensors like Snort and monitoring agents. Unlike
our previous work, such extensions allow our technique to
assimilate incomplete textual sources for cybersecurity event
detection in a cognitive manner.

•

•

•
•

•

III. C OGNITIVE A PPROACH TO C YBERSECURITY
This section describes our approach to detect cyber-attacks
mimicking the cognitive capabilities of humans. Oxford dictionary defines cognition [1] as “the mental action or process of
acquiring knowledge and understanding through thought, experience, and the senses”. Our cognitive strategy involves acquiring knowledge from various intelligence sources, combining them into an existing knowledge graph (which is already
populated with information about attack patterns, previous
attacks, tools used for attacks, etc.) and using this knowledge
graph to reason over the data from multiple traditional and
non-traditional sensors to detect cybersecurity events.
A novel feature of our framework is its ability to assimilate
information from dynamic textual sources and combine it
with malware behavioral information, detecting known and
unknown attacks. The main challenge with the textual sources
is that they are meant for human consumption and hence the
information can be incomplete. Moreover, the text is written
for a specific audience who already has some knowledge about
the topic. For instance, if the target audience of an article is
a security analyst, the line “Wannacry is a new ransomware.”
carries more knowledge than the textual information. Some
thoughts readily inferred by a human who reads it may be
the following. “wannacry is a ransomware”, “wannacry tries
to encrypt sensitive files”, “It uses some encryption tool to
encrypt these sensitive files”, “A downloaded program may
have initiated the encryption”, “Either downloaded keys or
randomly generated keys are used for encryption”, “Encryption can increase the processor usage in the victim machine”,
“It modifies many sensitive files”, etc. Our cognitive approach addresses this issue by remembering the experiences or
knowledge in a knowledge graph, and combining it with new
and potentially incomplete textual knowledge using standard
reasoning techniques.
Most cybersecurity events follow a pattern which we call
an intrusion kill chain. Lockheed Martin [11] defines it with
the following seven steps.
• Reconnaissance: Gathering information about the target
and various existing attacks (e.g., port scanning, collecting public information on hardware/software used, etc.)

•

Weaponization: Combining a specific trojan (software
to provide remote access to a victim machine) with an
exploit (software to get first unauthorized access to the
victim machine, often exploiting vulnerabilities). Trojans
and exploits are chosen taking the knowledge from Reconnaissance into consideration.
Delivery: Deliver the weaponized payload to the victim machine. (e.g., email attachments, removable media,
HTML pages, etc.)
Exploitation: Execution of the weaponized payload on
the victim machine.
Installation: Once the exploitation is successful, the attacker gains easier access to victim machine by installing
the trojan attached.
Command and Control (C2): The trojan installed on the
victim machine can connect to a Command and Control
machine and get ready to receive various commands to
be executed on the victim machine. Often APTs use such
a strategy.
Actions on Objectives: The final step is to carry out
different malicious actions on the victim machine. For
example, a ransomware starts searching and encrypting
sensitive files.

Different attacks use one or more of these seven steps during
their execution. However, many attacks have fewer steps. For
example, some attacks are self-contained such that there is no
requirement of a command and control setup. Attacks often
use the same tools or similar techniques during their execution.
Newer attacks could be permutations of tools/techniques used
in different stages in older attacks. We use this understanding to detect known and potentially unknown attacks. Some
examples are attackers using the same port scanning tools
like “nmap” for reconnaissance or using the same exploit
“Eternal Blue” in the Weaponization stage for different major
attacks like Wannacry, NotPetya, Retefe, etc. Thus, combining
information about different known attacks, fusing it with
incomplete textual information and reasoning over them will
help us to detect newer attacks.
Consider an example in which a blog reported a new
ransomware which uses nmap for reconnaissance, and Eternal Blue for exploitation. Our knowledge graph is already
populated with common information including that “Eternal
Blue uses mal-formed SMB packets for exploitation”, “a
generic ransomware modifies sensitive files”, “ransomware
increases the processor utilization”, etc. Let’s also consider
that sensors detected sensitive file modifications, mal-formed
SMB packets, and the nmap port scan. This data alone
cannot conclusively detect the presence of a ransomware attack
because these can happen for other reasons also (eg. files
are modified intentionally by the user, incorrect SMB packets
due to a bad network, etc.). However, when we register the
information from the blog that a new ransomware uses Eternal
Blue for exploitation it will act as the missing piece of a
jigsaw puzzle to indicate the presence of an attack with better
certainty.

A. Attack Model
To constrain the system, we make some assumptions about
the attacker. The attacker does not have complete inside
knowledge of the system being attacked which implies that he
will perform some level of probing or reconnaissance. Another
assumption we make is that not all attacks are brand new. The
attackers will reuse published (in security blogs, dark market,
intelligence sharing formats like STIX, etc.) vulnerabilities in
software/systems to perform different mal-activities like DoS
(Denial-of-Service), data ex-filtration, unauthorized access,
etc. Finally, we assume that our framework will have enough
traditional sensors to detect basic behaviors in a network
(Snort), host (HIDS), etc.
We categorize attackers into script kiddies, intermediate
and advanced state actors. Often script kiddies use existing
known techniques and try permutations of known tools for
intrusion. Intermediate attackers, on the other hand, modify
known attacks or tools significantly and try to evade direct
detection, but attack behaviors remain the same. The state
actors or experts mine for new vulnerabilities and come up
with brand new attacks. Our system tries to defend effectively
against the first two categories, but it will be hard to defend the
third category until information about those attacks is added
to the knowledge graph.
IV. S YSTEM A RCHITECTURE
New attack techniques are reported on a daily basis. In
this paper, we propose a cognitive framework to detect cybersecurity events amalgamating information from traditional
sensors, dynamic online textual information and knowledge
graphs. The system architecture for our framework is described
in Figure 1. The three major input sources to our framework
are the dynamic information from textual sources, input from
traditional sensors, and inputs from human experts. The IntelAggregate module captures information from these sources,
converts them to semantic web OWL representation and delivers them to the CCS (Cognitive CyberSecurity) module. The
CCS module is the brain of our framework where actionable
intelligence will be generated to assist the security analyst.
The various components are described in detail below.
A. CCS Framework Inputs
The first input is from textual sources. This input can either
be structured information in formats like STIX, TAXII, etc.
(from threat intelligence sources like US-CERT, Talos, etc.)
or plain text from sources like blogs, twitter, Reddit posts,
and dark-web posts. Part of a sample threat intelligence in
STIX format shared by US-CERT on wannacry is presented
in Figure 2. We use an off-the-shelf Named-Entity Recognizer
(NER) trained on cybersecurity text from Joshi et al. [13]
for extracting entities from plain text. The next input is from
traditional network sensors (Snort, Bro, etc.) and host sensors
(Host intrusion detection systems, file monitoring modules,
process monitoring modules, firewalls, etc.). We use the logs
from these sensors as input to our system. Finally, human
experts can define specific rules to detect complex behaviors

Fig. 1. Cognitive CyberSecurity Architecture

or complex attacks. Input from human experts is vital because
most organizations maintain policies or standards for the
activities in their networks. For example, organizations may
use a white-list policy for inbound IP connections (ie. Only IP
addresses from a specific list are accepted by default). In such
cases, a simple firewall rule will block unauthorized accesses.
However, it would add value to a security analyst to know if
there is a sudden spike in the inbound accesses from illegal
IP addresses even though they are blocked (Simple blocking
techniques cannot stop a motivated attacker and he will find
a way in. Perhaps an analyst considers such activities as a
precursor). Moreover, today an analyst’s intuitions are used for
identifying potential intrusions. Hence if we can capture these
intuitions we can make our framework better. All these inputs
are sent to the Intel-Aggregate module for further processing.
B. Cognitive CyberSecurity Module
The Cognitive CyberSecurity (CCS) module is the brain of
our framework which generates actionable intelligence from
the input data. The core of this module is knowledge represen-

Fig. 3. Proof of Concept CCS Architecture
Fig. 2. STIX for Wannacry Ransomware

tation. We use an extension of UCO (Unified CyberSecurity
Ontology) using a W3C standard OWL format to represent
knowledge in the domain. We extend UCO such that it can
reason over the inputs from various network sensors like Snort,
IDS, etc. and information from the cyber-Kill chain. We also
use SWRL (Semantic Web Rule Language) to specify rules
between entities. For instance, SWRL rules are used to specify
that an attack would be detected if different stages in the kill
chain are identified for a specific IP address. The information
in the knowledge graph is general such that experts can easily
add new knowledge to it. Experts can directly use different
known techniques as indicators because how indicators can
be detected (directly from sensors or using complex analysis
of these sensors) is already present in the knowledge graph.
For example, if an expert mentions port scan as an indicator,
the reasoner will automatically infer that Snort can detect it
and looks for Snort alerts. The statistical analytics sub-module
and graph analytic sub-module check for anomalous activities
using standard techniques like frequency analysis, clustering
techniques, etc. Any standard technique can be utilized to
generate indicators as far as they generate standard OWL
triplets to be fed to the CCS knowledge graph. A standard
reasoner is also part of the CCS module which will reason
over the knowledge graph generating actionable intelligence.
A concrete proof of concept implementation for this model is
described in Section V.
C. Intel-Aggregate Module
The Intel-Aggregate (IA) Module is responsible for the
conversion of various traditional and non-traditional network
sensor inputs to the standard semantic web OWL format.
Various inputs to our system are mentioned in Section IV-A.
However, they will produce outputs in different formats and
will be incompatible with our framework’s knowledge graph
(represented using UCO). UCO has defined various entities,
classes, etc. and, to be consistent with this knowledge graph,
these inputs need to be transformed. This module assimilates
all inputs to the cognitive framework, maps them to UCO
classes and entities, and generates their corresponding well-

formed OWL statements. The IA module will be part of all
the sensors which are attached to the framework.
V. E VALUATION
Evaluation of a system by detecting real attacks is difficult.
Various challenges involve getting access to an actual malware,
finding a safe execution environment within existing laws, etc.
Hence, we developed a sample ransomware which is safe but
displays typical malicious behaviors.
In this section, we describe the proof of concept implementation of our approach, an evaluation network on which we
ran the custom ransomware, and discuss the effectiveness of
our cognitive approach using the simulated network.
A. Proof of Concept Cognitive CyberSecurity System
Our proof of concept implementation has an architecture
similar to some real-world systems like Symantec Data Center
Security and Crowd Strike. Our system has a CCS module (the
master node) which detects various cybersecurity events and a
configurable set of cognitive agents which run on host systems
collecting various statistics, as shown in Figure 3.
1) Cognitive Agents: A full agent is a combination of the
Intel-Aggregator module and a traditional sensor. The IntelAggregator module is developed in such a way that it can be
customized to work with multiple traditional sensors collecting
and sending information to the CCS module (in OWL format)
for further processing. In our proof of concept to detect
ransomware attacks, we used a process monitoring agent, a
file monitoring agent and a Snort agent as enumerated below.
• Process Monitoring Agent: This agent combines a custom
process monitor and an IA module. It will run on all
host machines in the network and monitor different processes in the machine, their parent hierarchy, and various
statistics like memory usage, CPU usage etc. The agent
converts all this information into OWL format using the
IA module and reports them to the CCS module.
• File Monitoring Agent: A custom file monitor is attached
to an IA module to develop this agent. Similar to a
process monitoring agent, the file monitoring agent also
runs on all host machines aggregating various file-related

4)
5)

6)
7)

8)
Fig. 4. CCS Dashboard

•

statistics. Monitoring all files is a cumbersome task.
Hence, we maintain a list of sensitive files, file locations,
and suspicious files. The suspicious ones are all those new
files generated by a new process, large files downloaded
from the Internet, files copied from mass storage devices,
etc. Various statistics which are sent to the CCS module
include the process which modified the file, size, how it
was created, etc.
Snort Agent: Like the name suggests, this agent is a combination of a traditional snort and IA module. This agent
will read the output log file of a snort and generates OWL
consistent with the CCS module’s knowledge graph.

2) CCS Module: The CCS module is the brain of our
approach which uses cognitive analytics to detect attacks using
information from cognitive agents. We implemented it using
an Apache Fuseki server configured with a SWRL and Jena
reasoner. This module will get inputs from all the agents
enumerated, reason over them and feed output to a cognitive
dashboard (a custom website). The dashboard will dynamically
display various statistics, IP information, detected activities,
etc. On detection of a full-scale attack, the dashboard will pop
attack alerts as shown in Figure 4 (dashboard screenshot).
B. Custom Ransomware Design
Our custom ransomware targets Windows 7 machines which
have CVE-2017-0143 vulnerability [3] (buffer overflow related
to SMB protocol). We use the exploit from metasploit (for
this CVE) to get access to the victim machine. Once the
custom ransomware gets access to the victim machine, it
downloads the malware script from the attacker machine to
the victim machine. The downloaded malware script performs
the following functions.
1) Download an executable to encrypt files
2) Download a public key from the attacker machine
3) The script enumerates the sensitive files/folders in the
victim’s machine. The malware script contains a compiled list of potential locations (eg. Default Thunderbird
email client storage location, default Outlook location,
documents folder, default downloads folder, etc.). Our

9)

ransomware avoids system files because it hampers the
booting process.
All the selected files are split into chunks and a random
key is generated for each chunk
Files from each chunk are encrypted using the AES
algorithm and the corresponding random key. (AES is
used because RSA implementations are not normally
used to encrypt big files).
The corresponding raw data files are deleted securely.
A file is created with all encrypted file locations and
corresponding random keys used for their AES encryption.
This newly generated file is encrypted using RSA and
the downloaded attacker public key.
The raw text file with chunk info is then deleted.

C. Proof of Concept Network Architecture
To deploy our system and infect it using the custom ransomware described in section V-B, we created a network with
three different machines as shown in Figure 6.
1) Attack Machine: The attack machine is an Ubuntu
16 loaded with custom scripts and a webserver. The attack
script is responsible for scanning the network for vulnerable
machines and identifying their IP addresses. Once the IP list is
compiled, it will begin the attack by sending mal-formed SMB
packets and get access to the victim machine. The next step is
to download the ransomware script from the attack machine to
the victim machine and start running it. The machine will also
run a webserver which hosts the ransomware script, encryption
software, etc. along with a mechanism to generate, send and
save public-private key pairs for each of the requested IP
addresses.
2) Victim Machine: In this proof of concept, we are using
the exploit for CVE-2017-0143, as described in section V-B
which targets Windows 7 machines. Hence, we choose a fresh
installation of Windows 7 SP1 as the victim machine. The only
additional software we install on it are the file monitoring and
process monitoring agents (described in Section V-A1). We
also added some valuable files into some of the folders like
Documents, Pictures, etc.
3) CCS Master Machine: The core detection techniques are
installed in the CCS master machine. Apart from this, we run
Snort and snort agent in this machine (Snort could also be run
on another machine because the Snort agent will take care
of sending it to the CCS Master module). The CCS module
includes two components. First, the Fuseki server loaded with
the modified UCO Ontology and related SWRL rules. Standard
reasoners are also part of the Fuseki server. The CCS module is
the second component which extracts new information related
to new attacks, host machine activities, etc. and updates the
CCS dashboard dynamically.
D. Proof of Concept Timeline
We implemented the associated modules of CCS and created
a network described in Section V-C. Our next goal is to check
if we can detect the ransomware attack or not. Our knowledge

Fig. 5. Proof of Concept ransomware attack timeline

•
•
•

•
•

Fig. 6. Proof of Concept Network Architecture
•

graph is updated with common knowledge (the cyber-kill chain
and knowledge mentioned in section III) about cyber attacks.
We demonstrate that even such simple information could be
used for detecting newer attacks using this proof of concept.
Figure 5 depicts the timeline of the attack performed and the
actions from our CCS module. Each step in it is detailed below.
•
•
•
•
•

Step 1: Attacker performs a port scan on the victim
machine using Nmap
Step 2: Snort detects port scan and reports to the CCS
module.
Step 3: Attacker uses the attack script to exploit the
victim machine (using “Eternal Blue”)
Step 4: Snort detects mal-formed SMB packets in the
network.
Step 5: On successful exploitation, the attacker injects
malware into the victim machine.

•

Step 6: The first attack script starts running the malware
from the victim machine.
Step 7: As described in section V-B, the malware now
initiates downloads of encryption software, keys, etc.
Step 8: Encryption software and keys get downloaded
into the victim machine. The next task from the malware
is the detection of sensitive files and their encryption
using the downloaded tool.
Step 9: Snort detects downloads from unknown / potentially bad IP addresses.
Step 10: The file monitoring agent will detect new files
downloaded from the Internet.
Step 11: While performing encryption, the malware
modifies many sensitive files and the file monitoring agent
reports it to the CCS module.
Step 12: When encryption is performed on larger files,
the processor usage showed larger values and the process
monitoring agent reports it to the CCS module.

In this test, the CCS Knowledge graph has the information
about a new ransomware attack from textual sources. The
new information from textual sources are “Wannacry is a
ransomware” and “Wannacry uses Malformed SMB packets
to exploit”. In the attack timeline, at Step 2, Snort will
report a port scan which will be inferred by the CCS module
as a potential reconnaissance step. At step 4, when Snort
detects some mal-formed packets in the network, it is not
conclusive to tell that it is an attack. It could just be some
error packets. Subsequent steps, Step 9 through Step 12, detect
downloads from unknown sources, sensitive file modification,
increased processor usage, etc. From the knowledge graph, we
know the typical characteristics of a ransomware’s “Action-on-

objective”; a lot of sensitive file modification, high processor
usage, etc. However, these can also happen because of normal usage (for example, the user manually modifying files,
downloading and running applications from the Internet, etc.).
The presence of these indicators taken alone cannot be used to
detect a ransomware. However, the CCS system already knows
about a new ransomware attack using malformed SMB packets
from textual sources and when combined with data from
various sensors, the CCS system infers that the WannaCry
attack is happening in the system and it is displayed on the
dashboard as shown in Figure 4.
VI. C ONCLUSION
In this paper, we have described the design and implementation of a cognitive system to detect cybersecurity events.
Our technique assimilates and interprets often incomplete
textual information from a variety of sources such as security
bulletins, CVE’s and blogs, and represents it as a knowledge
graph using terms from the Unified Cybersecurity Ontology.
It represents the data from traditional host and network sensors, as well as any analysis generated by machine learning
techniques, in the same knowledge graph. It reasons over this
knowledge to detect cybersecurity events. We also developed
a proof of concept CCS system which features a cognitive
dashboard where cybersecurity events are reported to the
security analysts. Our technique reduces the cognitive load
on the analyst to interpret complex events occurring in large
enterprises by fusing information from multiple sources and
reasoning over it much like a human analyst. The capability
of our system is demonstrated by testing it against a custom
built ransomware, which uses the SMB vulnerability to infect
victims similar to the infamous WannaCry ransomware. In
ongoing work, we are analyzing the scalability of our system
by adding more sensors and concepts that define the behavior
of various processes running on typical networks.
ACKNOWLEDGMENT
This research was conducted in the UMBC Accelerated
Cognitive Computing Lab (ACCL), which is supported in part
by a gift from IBM. We thank the other members of the ACCL
Lab for their input in developing this system.
R EFERENCES
[1] Definition of cognition in English:. https://en.oxforddictionaries.com/
definition/cognition. [Online; accessed 2-March-2018].
[2] CISCO Talos. https://www.cisco.com/c/en/us/products/security/talos.
html, 2017. [Online].
[3] CVE-2017-0143
Detail.
https://nvd.nist.gov/vuln/detail/
CVE-2017-0143, 2017. [Online; accessed 2-March-2018].
[4] IBM QRadar Security Intelligence Platform. http://www-03.ibm.com/
software/products/en/qradar-siem/, 2017. [Online].
[5] Sean Barnum. Standardizing cyber threat intelligence information with
the structured threat information expression (stix). MITRE Corporation,
11:1–22, 2012.
[6] Noam Ben-Asher, Alessandro Oltramari, Robert F Erbacher, and
Cleotilde Gonzalez. Ontology-based adaptive systems of cyber defense.
In STIDS, pages 34–41, 2015.
[7] Parth Bhatt, Edgar Toshiro Yano, and Per Gustavsson. Towards a
framework to detect multi-stage advanced persistent threats attacks. In
Service Oriented System Engineering (SOSE), 2014 IEEE 8th International Symposium on, pages 390–395. IEEE, 2014.

[8] Cisco.
Timeline of ‘WannCry’ Ransomware Defense.
https:
//www.cisco.com/c/dam/en/us/solutions/collateral/enterprise-networks/
ransomware-defense/wannacry-timeline.pdf.
[Online; accessed 2March-2018].
[9] Gartner.
Reviews for Security Information and Event Management (SIEM) Software.
https://www.gartner.com/reviews/market/
security-information-event-management. [Online; accessed 3-March2018].
[10] André Grégio, Rodrigo Bonacin, Olga Nabuco, Vitor Monte Afonso,
Paulo Lı́cio De Geus, and Mario Jino. Ontology for malware behavior:
A core model proposal. In WETICE Conference (WETICE), 2014 IEEE
23rd International, pages 453–458. IEEE, 2014.
[11] Eric M Hutchins, Michael J Cloppert, and Rohan M Amin. Intelligencedriven computer network defense informed by analysis of adversary
campaigns and intrusion kill chains. Leading Issues in Information
Warfare & Security Research, 1(1):80, 2011.
[12] J Ingle. Organizing intelligence to respond to network intrusions and
attacks. In Briefing for the DoD Information Assurance Symposium,
2010.
[13] Arnav Joshi, Ravendar Lal, Tim Finin, and Anupam Joshi. Extracting
cybersecurity related linked data from text. In Semantic Computing
(ICSC), 2013 IEEE Seventh International Conference on, pages 252–
259. IEEE, 2013.
[14] Frankie Li and A Atlasis. A detailed analysis of an advanced persistent
threat malware. SANS Technology Institute, 2011.
[15] Claudio Masolo, Stefano Borgo, Aldo Gangemi, Nicola Guarino,
Alessandro Oltramari, and Luc Schneider. The wonderweb library of
foundational ontologies. 2002.
[16] John Mason.
Cyber Security Statistics.
https://thebestvpn.com/
cyber-security-statistics-2018/, 2018. [Online; accessed 2-March-2018].
[17] Peter Mell and Tim Grance. Use of the common vulnerabilities and
exposures (cve) vulnerability naming scheme. Technical report, NATIONAL INST OF STANDARDS AND TECHNOLOGY GAITHERSBURG MD COMPUTER SECURITY DIV, 2002.
[18] Microsoft. Microsoft Security Bulletin MS17-010 - Critical-Security
Update for Microsoft Windows SMB Server (4013389). https://docs.
microsoft.com/en-us/security-updates/securitybulletins/2017/ms17-010,
2017. [Online; accessed 2-March-2018].
[19] Sumit More, Mary Matthews, Anupam Joshi, and Tim Finin. A
knowledge-based approach to intrusion detection modeling. In Security
and Privacy Workshops (SPW), 2012 IEEE Symposium on, pages 75–81.
IEEE, 2012.
[20] Mark Nicolett and Kelly M Kavanagh. Magic quadrant for security
information and event management. 2017.
[21] Leo Obrst, Penny Chase, and Richard Markeloff. Developing an
ontology of the cyber security domain. In STIDS, pages 49–56, 2012.
[22] Alessandro Oltramari, Lorrie Faith Cranor, Robert J Walls, and Patrick
McDaniel. Computational ontology of network operations. In Military
Communications Conference, MILCOM 2015-2015 IEEE, pages 318–
323. IEEE, 2015.
[23] Alessandro Oltramari, Lorrie Faith Cranor, Robert J Walls, and Patrick D
McDaniel. Building an ontology of cyber security. In STIDS, pages 54–
61. Citeseer, 2014.
[24] Panda Security. 27% of all recorded malware appeared in 2015.
https://www.pandasecurity.com/mediacenter/press-releases/all-rec\
discretionary{-}{}{}orded-malware-appeared-in-2015/.
[Online;
accessed 2-March-2018].
[25] Aditya K Sood and Richard J Enbody. Targeted cyberattacks: a superset
of advanced persistent threats. IEEE security & privacy, 11(1):54–61,
2013.
[26] David Swift. A practical application of sim/sem/siem automating threat
identification. Paper, SANS Infosec Reading Room, The SANS, 2006.
[27] Zareen Syed, Ankur Padia, Tim Finin, M Lisa Mathews, and Anupam
Joshi. Uco: A unified cybersecurity ontology. In AAAI Workshop:
Artificial Intelligence for Cyber Security, 2016.
[28] Alex Vovk. How to Overcome SIEM Limitations. https://blog.netwrix.
com/2016/03/21/how-to-overcome-siem-limitations/, 2016. [Online; accessed 2-March-2018].
[29] Alex Vovk.
Infographics: Common Drawbacks of SIEM Solutions. https://blog.netwrix.com/2016/03/15/infographics-common-\
discretionary{-}{}{}drawbacks-of-siem-solutions/, 2016. [Online; accessed 2-March-2018].

