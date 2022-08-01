---
link: https://www.nist.gov/blogs/cybersecurity-insights/differential-privacy-bugs-and-why-theyre-hard-find
author: Joseph Near, David Darais
published: 2021-05-25T09:00:00
tags: []
---
# Highlights


---
# Differential Privacy Bugs and Why They’re Hard to Find
In previous posts we have explored what differential privacy is, how it works, and how to answer questions about data in ways that protect privacy. All of the algorithms we’ve discussed have been demonstrated via mathematical proof to be effective for protecting privacy. However, when translating these algorithms from paper to code, it's possible to introduce bugs in the resulting software which can result in failure to protect privacy. In this post we'll explore what these bugs typically look like, why it is so hard to detect them, and approaches to software assurance that can ensure your