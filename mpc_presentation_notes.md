## MPC presentation sketch

###What is MPC?

start with what MPC entails - yoink from the survey paper
multiple parties are able to securely compute a fucntion without revealing the each parties input

what sort of 

* Thresholding
    * Shamir Secret sharing

* Private Set Intersection
    * two untrusting parties try to calcualte 
### yao's millionare problem

* A basic example of MPC
    * we have two parties that don't trust each other but want to compute some result of their data

* Propose two types of attackers
    * the semi-honest attacker
        * people want to know know what each's other input is
    * the malicius attacker
        * what if someone wants to play a trick and try to subvert the protocol in someway?
        * you can protect this with a commitment value in some implementations. see the foundationsofgc paper.
        * the sender sends the wrong circuit -> what do they hope to achieve with this?

### propose the the solution

* Yao's garbled circuits
    * what is garbeling?
    * how does it work?

* Map an an intial input $x$ to a gabled input $X$ using the encoding information $e$
* $F$ is a garbled function that maps each $X$ to a garbled $Y$
* $d$ maps the garbled $Y$ to actual y.

details [read me](./gc_intro.md)


* There is a non-trivial step...

* naively, the chooser is going to attempt to every garbled output.
    * you will only get one valid output/decryption for one value.
    * if you got a valid output for more than one value, you would violate the authenticity!

### Oblivious Transfer (OT)
* What is the goal of oblivious transfer?
    * to hide the inputs of the sender and the evaluator from each other.

* Go through how OT work and summerize
    * this will protect us against a semi-honest attacker

* in a high level summary in the context of the GC. Remeber, the garbeling is seperate from the OT! we don't usually have the decoding part in OT though we do try to hide our input.
* the encoding part of the garbler is the labels.
    1. sender has a random element of the group
    2. the chooser computes two public keys, one is just $g^k$ and the other other is $(g^k)^{-1}*C$
    3. At this point, the sender has encrypted and permuted the outputs of the circuit using every option as key.
        * the sender knows the labels and knows the permuatations. but the chooser does not.

* extending the circuits to arbitraty bit widths for $X$ and $Y$
    * If you are familar with some basic computer architecture, you may already understand that we can represent every function
    * For example, look at an FPGA. You have collction of programmble look up tables (LUTs) that simulate hardware.
        * if we're able to show that this work one for gate, then we can abstract out this gate to get a circuit that represents an entire function with differnt input and output widths.

* **problem with the toy example, the output is too simple. becuase we will get a 0 or a 1, form the output, we may not know
which cipher text is correct. We can fix this by having label that corresponds with the output of the gate. In fact, this is how
we are able to** I don't think this is true. Try and figure this out and come back to it later


### Circle back to the yao's millionare problem

* Apply apply OT
* Hey, this only seems to work with one bit? how do we make this work with larger number of bits?

### how is the milliaonare problem different from Ginney and Evan

* we have differnt bit widths for input to the gate

## Run time (if possible)
* Lets talk about efficiency if we can....

* How are we protected from semi-honest attackers?
* How are we protected froma malicious scenario?
    * The sender sends a garbled circuit, but it isn't correct.
        * found a good little slide show on garbled circuits [https://web.engr.oregonstate.edu/~rosulekm/cryptabit/4-malicious.pdf]

### Let do a live demo of OT -> there are few libraries out there that will allow us to use garbled cicuits

* pull up the Alice's teminal and Bob's terminal


