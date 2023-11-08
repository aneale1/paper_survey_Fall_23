I'm looking at this paper for more detail on the encoding and decoding that was shown in g_c intro paper

### Fig 1
* having e and x let someone compute the garbled input.
* having F,X lets someone compute the garbled output
* having d and Y lets someone recover the final output y = De(d,Y)
* e and d are functions s.t $f = d \circ F \circ e$

* a party acquiring (F,X,d) shouldn't learn anything impermissible eyond that which is revealed by knowing just the final output of y. (i.e we may be able to hide the ouputs, but we can't stop someone learning somethign about the inputs once they have the output.)

* Side information function? -> what is this? i should probably gloss over this for the presentation though.
* obliviousness: a party aquuirung F and X, but not d, shouldn't learn anything about f,x, or y.
