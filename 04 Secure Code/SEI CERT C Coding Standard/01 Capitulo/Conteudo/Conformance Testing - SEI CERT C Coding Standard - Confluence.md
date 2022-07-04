To ensure that the source code [conforms](https://wiki.sei.cmu.edu/confluence/display/c/BB.+Definitions#BB.Definitions-conformingprogram) to this coding standard, it is necessary to have measures in place that check for rule violations. The most effective means of achieving this goal is to use one or more ISO/IEC TS 17961–conforming analyzers. Where a guideline cannot be checked by a tool, a manual review is required.

The [Source Code Analysis Laboratory (SCALe)](http://www.cert.org/secure-coding/products-services/scale.cfm) provides a means for evaluating the conformance of software systems against this and other coding standards. CERT coding standards provide a normative set of rules against which software systems can be evaluated. Conforming software systems should demonstrate improvements in the safety, reliability, and security over nonconforming systems.

The SCALe team at CERT analyzes a developer’s source code and provides a detailed report of findings to guide the code’s repair. After the developer has addressed these findings and the SCALe team determines that the product version conforms to the standard, CERT issues the developer a certificate and lists the system in a registry of conforming systems.

## Conformance

Conformance to the CERT C Coding Standard requires that the code not contain any violations of the rules specified in this standard. If an exceptional condition is claimed, the exception must correspond to a predefined exceptional condition, and the application of this exception must be documented in the source code. Conformance with the recommendations on the wiki is not necessary to claim conformance with the CERT C Coding Standard. Conformance to the recommendations will, in many cases, make it easier to conform to the rules, eliminating many potential sources of defects.

## Levels

Rules and recommendations in this standard are classified into three levels (see [How this Coding Standard is Organized](https://wiki.sei.cmu.edu/confluence/display/c/How+this+Coding+Standard+is+Organized)). Emphasis should be placed on conformance Level 1 (L1) rules. Software systems that have been validated as complying with all Level 1 rules are considered to be L1 conforming. Software systems can be assessed as L1, L2, or fully conforming, depending on the set of rules to which the system has been validated.

## Deviation Procedure

Strict adherence to all rules is unlikely and, consequently, deviations associated with specific rule violations are necessary. Deviations can be used in cases where a true-positive finding is uncontested as a rule violation but the code is nonetheless determined to be correct. An uncontested true-positive finding may be the result of a design or architecture feature of the software or may occur for a valid reason that was unanticipated by the coding standard. In this respect, the deviation procedure allows for the possibility that coding rules are overly strict \[[Seacord 2013](https://wiki.sei.cmu.edu/confluence/display/c/AA.+Bibliography#AA.Bibliography-Seacord2013)\].

Deviations are not granted for reasons of performance or usability. A software system that successfully passes conformance testing must not contain defects or exploitable vulnerabilities. Deviation requests are evaluated by the lead assessor, and if the developer can provide sufficient evidence that the deviation will not result in a vulnerability, the deviation request is accepted. Deviations are used infrequently because it is almost always easier to fix a coding error than it is to provide an argument that the coding error does not result in a vulnerability.

___

 **[![](https://wiki.sei.cmu.edu/confluence/download/attachments/87152044/button_arrow_left.png?version=1&modificationDate=1201021124000&api=v2)](https://wiki.sei.cmu.edu/confluence/display/c/Rules+versus+Recommendations)** **[![](https://wiki.sei.cmu.edu/confluence/download/attachments/87152044/button_arrow_up.png?version=1&modificationDate=1201021146000&api=v2)](https://wiki.sei.cmu.edu/confluence/display/c/1+Front+Matter)****[![](https://wiki.sei.cmu.edu/confluence/download/attachments/87152044/button_arrow_right.png?version=1&modificationDate=1201021137000&api=v2)](https://wiki.sei.cmu.edu/confluence/display/c/Development+Process)**