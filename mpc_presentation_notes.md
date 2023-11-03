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

### propose the the solution

* Yao's garbled circuits
    * what is garbeling?
    * how does it work?

* There is a non-trivial step...

### Oblivious Transfer (OT)

* Go through how OT work and summerize
    * this will protect us against a semi-honest attacker


### Circle back to the yao's millionare problem

* Apply apply OT
* Hey, this only seems to work with one bit? how do we make this work with larger number of bits?

## Run time (if possible)
* Lets talk about efficiency if we can....

* How are we protected from semi-honest attackers?
* How are we protected froma malicious scenario?
    * The sender sends a garbled circuit, but it isn't correct.

### Let do a live demo of OT -> there are few libraries out there that will allow us to use garbled cicuits

* pull up the Alice's teminal and Bob's terminal


