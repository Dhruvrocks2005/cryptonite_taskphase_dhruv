# Cryptograhy

## miniRSA

**Given:**

N: 29331922499794985782735976045591164936683059380558950386560160105740343201513369939006307531165922708949619162698623675349030430859547825708994708321803705309459438099340427770580064400911431856656901982789948285309956111848686906152664473350940486507451771223435835260168971210087470894448460745593956840586530527915802541450092946574694809584880896601317519794442862977471129319781313161842056501715040555964011899589002863730868679527184420789010551475067862907739054966183120621407246398518098981106431219207697870293412176440482900183550467375190239898455201170831410460483829448603477361305838743852756938687673

e: 3

ciphertext (c): 2205316413931134031074603746928247799030155221252519872650080519263755075355825243327515211479747536697517688468095325517209911688684309894900992899707504087647575997847717180766377832435022794675332132906451858990782325436498952049751141 

<br>

**Approach:** 

To decrypt the ciphertext, I used an online RSA decryption tool.

I entered `N`, `e` and `c` in the RSA Decoder and found the flag.

**Website:** https://www.dcode.fr/rsa-cipher

<br>

![image](https://github.com/user-attachments/assets/63eb9052-64a6-4aba-91c4-dd8d2c7f84f0)

<br>

**Knowledge Gained:**

I learned about RSA encryption in further detail and explored its vulnerabilities- the implications of using small public exponents in RSA encryption(small e attack).

**RSA Encryption: c = m<sup>e</sup> (mod n)**

**RSA Decryption: m = c<sup>d</sup> (mod n)**


Utility of online cryptographic tools for quickly testing and validating decryption methods without the need for extensive manual calculations.

**Incorrect Tangents:**

I briefly considered writing my own decryption script. However, I quickly switched to the online tool after realizing the complexity and time required for implementing the algorithm from scratch.

**Flag:**

```
picoCTF{n33d_a_lArg3r_e_d0cd6eae}
```

**Resources used:**

https://en.wikipedia.org/wiki/RSA_(cryptosystem)

https://ctf101.org/cryptography/what-is-rsa/

https://www.dcode.fr/rsa-cipher
