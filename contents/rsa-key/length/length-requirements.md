# Length requirements

In the first decade of the 21th century, and counting, on a given year no RSA key bigger than `(year - 2000) * 32 + 512 [bits]` has been openly factored other than by exploitation of a flaw of the key generator (a pitfall [observed][1] in poorly implemented devices [including Smart Cards][2]). This linear estimate of _academic_ factoring progress should be used neither for long-term predictions (after 2016 or 1024-bits); nor for _choosing_ a key length so as to be safe from attacks with high confidence (or, equivalently, conforming to standards with that aim), a goal best served by this website on [keylength][3].

The current factoring record is [768 bits, by the end of 2009][4], and quoting this:

> NOTE: It is not unreasonable to expect that 1024-bit RSA moduli can be factored well within the next decade by an academic effort.

_Update_: I emphasize that the above is about attacks _actually performed_ by _academics_. So far, hackers have always been some years behind (see below). On the other hand, it is quite conceivable that well funded government agencies are many years _ahead_ in the factoring game. They have [the hardware and CPU time][5]. And there are so many 1024-bit keys around that it is likely a worthwhile technique to be in a position to break these. It is one of the most credible and [conjectured][6] explanation for [claims of cryptanalytic breakthrough by the NSA][7]. Also, dedicated hardware could change the picture someday; e.g. as outlined by Daniel Bernstein and Tanja Lange: [_Batch NFS_][8] (in [proceedings of SAC 2014][9], to appear; also in [Cryptology ePrint Archive][10], November 2014).

By 2015, the main _practical_ threat to systems still using 1024-bit RSA to protect commercial assets often is _not_ factorization of a public modulus (but rather, penetration of the IT infrastructure by other means, such as hacking, and trust in digital certificates issued to entities that should not be trusted). With 2048 bits or more we are safe from that factorization threat for perhaps two decades, with fair (but not absolute) confidence.

_Update 2_: Factorization progress is best shown on a graph (to get at the the raw data e.g. to make a better graph, edit this answer):
	![Size computation-power risk function](assets/size-computation_risk-function.png)
(This also shows the linear approximation at the beginning of this answer, which actually is a conjecture at even odds for the \[2000-2016\] period that I made privately circa 2002, and [committed publicly in 2004 (in French)][12]. Also pictured are the three single events that I know of hostile factorization of an RSA key (other than copycats of these events, or exploitation of flawed key generator):

+ The [Blacknet PGP Key][13] in 1995. Alec Muffett, Paul Leyland, Arjen Lenstra and Jim Gillogly covertly factored a 384-bit RSA key that was used to PGP-encipher "the BlackNet message" spammed over many usenet newsgroup. There was no monetary loss.

+ The French "YesCard" circa 1998. An individual factored the 321-bit key then used (even though it was clearly much too short) in issuer certificates for French debit/credit bank Smart Cards. By proxy of a lawyer, he contacted the card issuing authority, trying to monetize his work. In order to prove his point, he made a handful of counterfeit Smart Cards and actually used them in metro tickets vending machine(s). He was caught and got a [10 months suspended sentence (judgment in French)][14]. In 2000 the factorization of the same key [was posted (in French)][15] and soon after, counterfeit Smart Cards burgeoned. These worked with any PIN, hence the name [YesCard (in French)][16]. For a while, they caused real monetary loss in vending machines.

+ The [TI-83 Plus OS Signing Key][17] in 2009. An individual [factored][18] the 512-bit key used to sign downloadable firmware in this calculator, easing installation of custom OS, thus making him a hero among enthusiasts of the machine. There was no direct monetary loss, but the manufacturer was apparently less than amused. Following that, many 512-bit keys (including that of other calculators) have been factored.

_Update 3_: Definitely, 512-bit RSA is no longer providing sizable security. Despite that, [reportedly][19], certificates with this key size have been recently issued by official Certification Authorities, and used to sign malware, possibly by mean of an hostile factorization.

## References

> Adapted from: StackExchange
> [How big an rsa key is considered secure today][20]


<!-- REFERENCES -->

  [1]: http://eprint.iacr.org/2012/064
  [2]: http://smartfacts.cr.yp.to/
  [3]: http://www.keylength.com/
  [4]: http://eprint.iacr.org/2010/006
  [5]: http://www.top500.org/lists/2011/11
  [6]: https://www.schneier.com/blog/archives/2012/03/can_the_nsa_bre.html
  [7]: http://www.wired.com/threatlevel/2012/03/ff_nsadatacenter/all/1
  [8]: http://cr.yp.to/papers.html#batchnfs
  [9]: http://www.springer.com/computer/security+and+cryptology/book/978-3-319-13050-7
  [10]: http://eprint.iacr.org/2014/921
  [11]: http://i.stack.imgur.com/VSwml.png
  [12]: https://groups.google.com/forum/?fromgroups#!msg/fr.misc.cryptologie/F6ghzB_Pgx8/lSOpPFxOUwMJ
  [13]: http://baby.indstate.edu/msattler/_sci-tech/comp/privacy/pgp/misc/blacknet-key-attack.html
  [14]: http://www.legalis.net/spip.php?page=jurisprudence-decision&id_article=1200
  [15]: https://groups.google.com/forum/?fromgroups#!msg/fr.misc.cryptologie/lKaAfKTeEM8/lNTX14KpYLsJ
  [16]: http://web.archive.org/web/20060411051448/http://parodie.com/monetique/
  [17]: http://www.ticalc.org/archives/news/articles/14/145/145154.html
  [18]: http://www.unitedti.org/forum/index.php?showtopic=8888&st=0&p=135113&#entry135113
  [19]: https://groups.google.com/forum/?fromgroups#!topic/mozilla.dev.security.policy/cn1sBm2ibWo
  [20]:https://crypto.stackexchange.com/questions/1978/how-big-an-rsa-key-is-considered-secure-today/1982#1982
