---
link: https://www.youtube.com/watch?v=c5ORCYdcOKk
author: 
   
published: 2021-02-05T18:08:00
tags: []
---
# Highlights


---
# Stack Canaries – Gingerly Sidestepping The Cage
Affiliated Course: https://www.sans.org/sec660 Presented by: Michiel Lemmens Follow me here: https://twitter.com/mchllmmns Stack canaries or security cookies are tell-tale values added to binaries during compilation to protect critical stack values like return pointers against buffer overflow attacks. If an incorrect canary is detected during certain stages of the execution flow, such as right before return, the program will be terminated. Their presence makes exploitation of such vulnerabilities more difficult. But not impossible. In this webcast, we will be discussing: - What stack canaries look like - What kinds of stack canaries can be found - When compilers add them - How they can be circumvented Our trip will take us along 32 and 64 bit binaries, assembly (though no fluency is expected), /GS, my grandfathers professional history.