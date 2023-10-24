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

 Oblivious transfer with a random oracle

* ***Input***: the chooser's input is $\sigma\isin\{0,1\}$. The sender's is $(M_0,M_1)$ 

* ***Output***: the chooser's output is $M_\sigma$

* ***Prelim***: The protocol operates over a group $\Z_q$ of **prime order**. $G_q$ can be a **subgroup of order $q$** of $\Z_p^*$ where $p$ is prime and and $q|p-1$. Let $g$ be the generator group for which **Comp DH** holds. The protocol uses a function $H$ which is assumed to be a random oracle.

 * ***Init***: The sender chooses a random element $C\isin\Z_q$ and publishes it. The chooser will not know the Dlog of $C$ to the base $g$. We do not care if the sender knows Dlog of $C$
 
 * ***Protocol:***
    1. The chooser picks a random $1\leqslant k \leqslant q$, sets public keys $PK_\sigma = g^k$ and $PK_{1-\sigma} = C/PK_\sigma$ and sends $PK_0$ to the sender.
    2. The sender computes $PK_1 = C/PK_0$ and chooses a random $r_0,r_1 \isin \Z_q$. It encrypts $M_0$ by $E_0 = \braket{g^{r0}, H(PK_0^{r0})\oplus M_0}$ and $M_1$ by $E_1 = \braket{g^{r1}, H(PK_1^{r1})\oplus M_1}$ and sends $(E_0,E_1)$ to the chooser.
    3. chooser computes $H((g^{r\sigma})^k) = H(PK_\sigma^{r\sigma})$ and uses it to decrypt $M_\sigma$.


* ***Overhead:*** The sender has to compute four exps. (two are precomputed before the protocol). The chooser has to choose two exponentiations (one is precomputed). This is referring to the $E_0 = \braket{g^{r0}, H(PK_0^{r0})\oplus M_0}$ and the corresponding $E_1$ that is also sent along. 
    * chooser $\rightarrow$ sender: one group element is used 
    * sender $\rightarrow$ chooser: two group elements are used, and two elements in the size of the inputs 
* ***Security:***
    * chooser's privacy: This is preserved since the value that she sends to the sender is uniformly random and independent of $\sigma$.
    * sender's security: The chooser cannot know the Dlog of both $PK_0$ and $PK_1$, since that would reveal the Dlog of $C$. The DH assumption imples that she (the chooser) cannot compute both $(PK_0)^{r0}$ and $(PK_1)^{r1}$. Together with the random oracle assumption, this ensures that she (the chooser) cannot distinguish $H((PK_0)^{r0})$ or $H((PK_1)^{r1})$ from random.
