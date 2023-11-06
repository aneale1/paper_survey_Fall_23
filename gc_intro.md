# A Gentle Introduction to Yao's Garbled Circuits: Sophia Yakoubov

# Classic GC

Two parties want to collaborate (call them Ginny and Evan). They want to hide their choices from each other
unless in case the other party doesn't want to collaborate. They want to know the AND (conjunction) of their
two bits without the revealing anything else to one another.

Ginny, in this case, is the garbler and is sending a garbled AND gate to Evan.

* Garbled gate Generation:
    * boolean truth table gates are obfuscated
    * Ginny Picks 4 labels/strings $W_G^0,W_G^1,W_E^0,W_G^1$
    * Each *pair* of labels corresponds to each scenario
    * Each *label pair* is used to encrypt the corresponding output
    * a function $H$ is used to derive an encryption key e.g $g=0$,$e=0$ $\rarr$ $Enc(H(W_G^0,W_E^0), g \land e = 0)$
    * The cipher texts are then permuted and have a random ordering

* Evaluation:
    * Evan must only decrypt one cipher text that corresponds to the real values of g and e.
    * Evan must get $W_G^g,W_E^e$ from Ginny. Ginney knows $g$ but does not know $e$.
    * Ginny cannot send both $W_E^0$ $W_E^1$, or else evan can generate two keys and decrypt two cipher texts.
    * Evan does not want Ginny to learn $e$, so we need a way to protect it.
    * This is where oblivious transfer comes in. In this case, Evan is the chooser, and Ginny is the sender.

## Formal stuff

* Garbeled Circuit Scheme:
    *  $\mathcal{G}$ is made up of four polynomial run time algs (Gb, En, Ev, De).
    1. Gb $(1^{\lambda},f$ -> $(F,e,d)$
        * takes in a circuit f and security paratmer. Encodes information e, and decoding information d
    2. En$(e,x)$ -> $X$
        * Takes the encoded information and returns the garbled input X.
    3. Ev$(F,X)$ -> $Y$
        * the evaluation alg EV take in the garbled circuit F and the garbled input X, and return garled input y.
    4. De$(d,Y)$ -> $y$
        * Take in the decoding information d, garbled output, and comes out with y.

### Security

provides obliviousness, privacy, and authenticity.
* oblivious : $F$ and $X$ do not reveal anything about input x.
* privacy: knowing d allows you to reveal y, but does not give you any more information about x. (e.g you know both people chose the same input if y=1, but you don't know who if y=0)
* authentic if an adversary given $F$ and $X$ cannot find a $Y' \neq Ev(F,X)$ that decodes without error.

what are the obliviousSim games and what are the privSim game?


