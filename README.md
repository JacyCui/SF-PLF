# Software Foundations - Volumn 2 : Programming Language Foundations

> You need to finish learning of [Logic Foundations](https://github.com/JacyCui/SF-LF) before moving forward to Programming Language Foundations.

This repository consists of two parts:

- All coq files from [Online Programming Language Foundations Textbook](https://softwarefoundations.cis.upenn.edu/plf-current/index.html) (version 6.6) with solutions for all formal exercises.
- A summary of proof tactics for quick reference besides previous summary in Logic Foundations.

- A summary of tacticals for quick reference besides previous summary in Logic Foundations.



## Proof Tactics Summary

|                            Usage                             |                           Meaning                            |
| :----------------------------------------------------------: | :----------------------------------------------------------: |
| `specialize H with`<br />`(a := your_a)`<br />`(b := your_b)` | The hypothesis `H` will be instantiated on `your_a` and `your_b`. |
|                         `exact ...`                          | If you know the exact proof term that proves the goal,<br />you can provide it directly using the `exact` tactic. |
|                            `ring`                            | Compared to `lia`, adds support for multiplications, gives up support<br />for inequalities, and supports only integers (type `Z`) |

> The following tactics are from the `LibTatics` library, which require `From PLF Require LibTactics` before using the following tactics.

|           Usage           |                           Meaning                            |
| :-----------------------: | :----------------------------------------------------------: |
|       `introv H...`       | Automatically introduce the  variables of a theorem and explicitly<br /> name the hypotheses |
|        `inverts H`        | Behaves like inversion but performs substitution and clear.  |
|         `splits`          | Applies to a goal made of a conjunction of `n` propositions and it<br /> produces `n` subgoals. |
|        `branch k`         |   Proves a n-ary disjunction by proving its k'th subterm.    |
|    `asserts_rewrite E`    |    Peforms `rewrite E` in goal and produces the goal `E`.    |
|     `cuts_rewrite E`      | Similar to `asserts_rewrites E` except that<br />the two subgoals produced are swapped. |
|         `substs`          | Similar to `subst` except that it doesn't fail with circular equalities. |
|         `fequals`         | Similar to `f_equal` except that it discharges all the trivial subgoals produced. |
|       `applys_eq H`       | Applies `H` and introduces some equality goals to match `H` with goal. |
|         `unfolds`         |     Automatically calls `unfold` on the head definition.     |
|      `unfolds in H`       |        Unfold the head definition in hypothesis `H`.         |
|          `false`          | Calls `exfalso` and proves the goal if it contains absurd<br />or contradictory assumptions. |
|         `false H`         |     Replaces the goal with `False` and then applies `H`.     |
|           `gen`           | A shorthand for `generalize dependent` that accepts several arguments. |
|          `sort`           | Reorganizes the proof context by placing all the variables<br />at the top and all the hypotheses at the bottom. |
|   `lets I: E0 E1 .. EN`   | Builds an hypothesis named `I` by applying the fact `E0` to the arguments<br />`E1` to `En`. `I` can also be a destruction pattern. |
|  `lets I: X0 X1 .. ___`   | Triple-underscore symbol `___` indicates that we want all the remaining<br />arguments to be produced as subgoals. |
|     `lets I: H __ 3`      | Double-underscore symbol `__` allows skipping an argument<br />when several arguments. |
|  `forwards H: E0 E1 ...`  | The same as `let H: E0 E1 ... ___` , where the triple-underscore<br />has the same meaning as explained above. |
|    `applys E0 E1 ...`     |    The same as `lets H: E0 E1 ... ; eapply H; clear H` .     |
| `specializes H E0 E1 ...` | The same as `lets H': H E0 E1 ...; clear H; remame H' into H` . |
|          `iauto`          | Extends extends `eauto` with support for negation, conjunctions,<br />and disjunctions (very slow). Shorhand for `try solve [intuition auto]`. |
|          `jauto`          | Extends extends `eauto` with support for negation, conjunctions,<br />and existential at the head of hypothesis. |

### Tips

- `inverts H as.` is like `inverts H` except that the variables and hypotheses being produced are placed in the goal rather than in the context.
    - `inverts H as H1 H2 H3` is equivalent to `inverts H as; introv H1 H2 H3`.

- `(H1 & H2 & H3 & H4 & H5)` is shorthand for `[H1 [H2 [H3 [H4 H5]]]]` .



## Tacticals Summary

|   Usage    |                           Meaning                            |
| :--------: | :----------------------------------------------------------: |
| `T1｜｜T2` | First try the tactic on the left side.<br /> If it fails, then it applies the tactic on the right side. |

