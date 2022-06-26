---
link: https://www.youtube.com/watch?v=SOr_G8oOstc
author: 
   
published: 2021-11-16T17:18:00
tags: []
---
# Highlights


---
# Detecting DCSync and DCShadow Network Traffic
Relevant Course: https://www.sans.org/sec599 Presented by: Michel Coene and Didier Stevens Follow: https://twitter.com/DidierStevens Follow: https://twitter.com/coenemichel In order to interact with a real domain controller, Mimikatz can spoof a Windows domain controller, and read information from or write information to active directory. Mimikatz's DCSync command is used to read information: typically, it is used to dump credentials from active directory. And the DCShadow command is used to write information: for example, modify the primary group of an account to a group with higher privileges. The use of these Mimikatz commands results in active directory replication network traffic between the compromised machine and domain controllers. In this webinar, we will show you what this network traffic looks like, and how you can detect it. IDS rules to detect DCSync and DCShadow network traffic will be developed. Finally, more generic detection rules will also be covered.