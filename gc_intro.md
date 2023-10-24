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

