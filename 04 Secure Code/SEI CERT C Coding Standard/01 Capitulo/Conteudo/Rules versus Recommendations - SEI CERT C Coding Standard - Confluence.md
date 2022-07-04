This coding standard consists of _rules_ and _recommendations_. Rules are meant to provide normative requirements for code; recommendations are meant to provide guidance that, when followed, should improve the safety, reliability, and security of software systems. However, a violation of a recommendation does not necessarily indicate the presence of a defect in the code. Rules and recommendations are collectively referred to as _guidelines_.

## Rules

Rules must meet the following criteria:

1.  Violation of the guideline is likely to result in a defect that may adversely affect the safety, reliability, or security of a system, for example, by introducing a  [security flaw](https://wiki.sei.cmu.edu/confluence/display/c/BB.+Definitions#BB.Definitions-securityflaw) that may result in an exploitable [vulnerability](https://wiki.sei.cmu.edu/confluence/display/c/BB.+Definitions#BB.Definitions-vulnerability).
2.  The guideline does not rely on source code annotations or assumptions.
3.  Conformance to the guideline can be determined through automated analysis (either static or dynamic), formal methods, or manual inspection techniques.

## Recommendations

Recommendations are suggestions for improving code quality. Guidelines are defined to be recommendations when all of the following conditions are met:

1.  Application of a guideline is likely to improve the safety, reliability, or security of software systems.
2.  One or more of the requirements necessary for a guideline to be considered a rule cannot be met.

The set of recommendations that a particular development effort adopts depends on the requirements of the final software product. Projects with stricter requirements may decide to dedicate more resources to ensuring the safety, reliability, and security of a system and consequently are likely to adopt a broader set of recommendations.

___

 **[![](https://wiki.sei.cmu.edu/confluence/download/attachments/87152044/button_arrow_left.png?version=1&modificationDate=1201021124000&api=v2)](https://wiki.sei.cmu.edu/confluence/display/c/Taint+Analysis)** **[![](https://wiki.sei.cmu.edu/confluence/download/attachments/87152044/button_arrow_up.png?version=1&modificationDate=1201021146000&api=v2)](https://wiki.sei.cmu.edu/confluence/display/c/1+Front+Matter)****[![](https://wiki.sei.cmu.edu/confluence/download/attachments/87152044/button_arrow_right.png?version=1&modificationDate=1201021137000&api=v2)](https://wiki.sei.cmu.edu/confluence/display/c/Conformance+Testing)**