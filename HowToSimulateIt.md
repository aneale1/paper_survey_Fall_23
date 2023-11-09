## How to Simulate it - a Tutorial on the Simulation Proof Technique

* semantic security for encryption compares what can be learned by na adversary who receives a real ciphertext to what can be learend by an adversary who recieves nothing.

* It hard to formalize the notion that "nothing is learned"

* We say that an ecryption shceme is secure if the only information derived (or output by the adversary) is that which is based on a priori knowledge.

* For now, it suffices to say that security proofs for definitions formualted in this way work by constructing a simualt that resides in the alternative world that is secvure by definitio, and generates a view for the adversary in the real world that is computationally indistinguishable from its real view.

The simulator must fufill these three tasks:
1. It must generate a view for the real adverasry that is indistinguishable form its real view.
2. It must extract the effective inputs used by the adversary in the execution; and
3. It must make the view generated be consistent with the output that is based on this input.

Semi-honest adversary $\rarr$ is following the protocol but is trying to learn more than they should by inspecting the protocol transcript.

TODO: There are some really good things to come back to and revisit in this paper in greater detail, but for now I just want a  basic idea of simulation and how it relates to OT. 


* In sematic security, consider $A$ and $A'$. $A$ lives in an ideal world where it has access to a cipher text. A' lives in a world where it only has access to auxillary information and the plaintext length only. A' can learn as much as A, which shows us the ideal versus real world comparison.

* A' outputs with almost the same probability as A, but its not the same because it does not have the ciphertext. A' know almost the same as A becuase it *simulates* an execution of A with its expected inputs. A' cannot do this perfectly since it doenst get all the same inputs. This is solved by having A' give A an encryption of garbage instead. 
    * for example, rather than giving A a cipher text, A' will give A encryption of all zeros.
    * If the encryptions are indistinguishable, then A should output $f(1^n,X_n)$ with approximatly the same probability.
    * we are showing that A cannot disitnguish between a legit encryption and a grabage encryption.
    * Note to self: what about homomorphic encryption?

#### Privacy by simulation:


#### Section 8: oblivious transfer functionality and show how the simulator extract the inputs from the adversary




