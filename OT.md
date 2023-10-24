#  Effcient Oblivious Transfer Protocols: Moni Naor, Benny Pinkas
This is just a test run to see if I can come up with a somewhat sane system to parse papers.
A lot of things will need to be filled in because I will not completly understand them on my first pass (or second, or third...), but I don't want to loose the tree for the forest.
I'm trying to learn something specific from this paper. In this case, I'm trying to understand basic Oblivious Transfer.

To summerize OT:
> the sender is assured that the chooser does not receive more information that it is entitled, while the chooser is assured that the sender does not learn which part of the inputs it received. 

#### Contributions

TODO: I don't fully understand this yet.

* low amortized overhaed
* badwidth/computation trade-off

#### Definitions

* 1-out-of-2 $(M_0,M_1)$... the generalized version is 1-out-of-N
* There only 1 one of the sender or the chooser can be information-theoretic protected\. The other is going to be computationally secure


* Relying on Random oracles
    * Chooser's Security: TODO -> chooser is info secure
    * Sender's Security: TODO -> sender is comp secure

* W/o Random oracles
    * Chooser's Security: TODO -> chooser is comp secure
    * Sender's Security: TODO -> sender is info secure and uses a trusted third party
        * There was something in the beginning about the sender being split into two parts (elaborate) 

#### Assumptions and Model

* Something something Random Oracle

## The basic oblivious transfer protocol (the good stuff)

 this includes random oracles.

 * *Input*: the chooser's input is $\sigma\isin\{0,1\}$. The sender's is $(M_0,M_1)$ 
 * *Output*: the chooser's output is $M_\sigma$
