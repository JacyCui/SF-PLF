# Software Foundations - Volumn 2 : Programming Language Foundations

> You need to finish learning of [Logic Foundations](https://github.com/JacyCui/SF-LF) before moving forward to Programming Language Foundations.

This repository consists of two parts:

- All coq files from [Online Programming Language Foundations Textbook](https://softwarefoundations.cis.upenn.edu/plf-current/index.html) (version 6.6) with solutions for all formal exercises.
- A summary of proof tactics for quick reference besides previous summary in Logic Foundations.

- A summary of tacticals for quick reference besides previous summary in Logic Foundations.



## Proof Tactics Summary

|                      Usage                      |                           Meaning                            |
| :---------------------------------------------: | :----------------------------------------------------------: |
| `specialize H with (a := your_a) (b := your_b)` | The hypothesis `H` will be instantiated on `your_a` and `your_b`. |
|                   `exact ...`                   | If you know the exact proof term that proves the goal,<br />you can provide it directly using the `exact` tactic. |



## Tacticals Summary

|   Usage    |                           Meaning                            |
| :--------: | :----------------------------------------------------------: |
| `T1 || T2` | First try the tactic on the left side.<br /> If it fails, then it applies the tactic on the right side. |

