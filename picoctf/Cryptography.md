# Cryptograhy - Mandatory Challenges

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

# Cryptograhy - Extra Challenges

## interencdec

```
YidkM0JxZGtwQlRYdHFhR3g2YUhsZmF6TnFlVGwzWVROclh6YzRNalV3YUcxcWZRPT0nCg==
```

Given string was encoded in base64.

![image](https://github.com/user-attachments/assets/8cd3a341-d77e-4ad0-8836-7c57ae9c57b9)

```
b'd3BqdkpBTXtqaGx6aHlfazNqeTl3YTNrXzc4MjUwaG1qfQ=='
```

After decoding it, the result also seemed to be encoded in base64.

![image](https://github.com/user-attachments/assets/c98eedf1-fecd-4443-8e70-7ade9a2cc8bd)

```
wpjvJAM{jhlzhy_k3jy9wa3k_78250hmj}
```

After decoding it, the result seemed to be encoded in caesar cypher.

![image](https://github.com/user-attachments/assets/baf4d070-c728-48b5-92d2-ba60b8904ac6)

After decoding it, I found the flag.

**Flag:**

```
picoCTF{caesar_d3cr9pt3d_78250afc}
```

Tool used: https://cryptii.com/

## Mod 26

ROT13 is a simple substitution cipher that shifts each letter 13 positions in the alphabet. Applying ROT13 again on the encoded text will return the original text.

**Encoded text:**

```
cvpbPGS{arkg_gvzr_V'yy_gel_2_ebhaqf_bs_ebg13_nSkgmDJE}
```

![image](https://github.com/user-attachments/assets/9b4d23a6-23c4-4fdb-8468-ec08090fb06d)

**Decoded text:**

```
picoCTF{next_time_I'll_try_2_rounds_of_rot13_aFxtzQWR}
```

**Flag:**

```
picoCTF{next_time_I'll_try_2_rounds_of_rot13_aFxtzQWR}
```

## substitution0

Tool used: https://planetcalc.com/8047/

![image](https://github.com/user-attachments/assets/dee7d8c9-de6e-47b3-97ae-65798671b63b)

**Flag:**

```
picoCTF{5UB5717U710N_3V0LU710N_357BF9FF}
```

## substitution1

Tool used: https://planetcalc.com/8047/

![image](https://github.com/user-attachments/assets/505e2687-15d6-4ad2-8d0d-8c77e8466707)

![image](https://github.com/user-attachments/assets/9ca576c8-f25d-4eb5-ae75-e4d5a5db9799)

![image](https://github.com/user-attachments/assets/a6cfee76-a3f6-4e5a-bb6d-2812f2265b64)

![image](https://github.com/user-attachments/assets/ab6c65a4-b5a0-42a8-848f-c7cce135fb3a)

There were no instances of `J`, `Z`, `X` or `Q` in the decrypted paragraph so the flag could be calculated with permutation and combination but even that was not required since it was obvious which character('Q') would be used as the flag is in leetspeak.

**Flag:**

```
picoCTF{FR3QU3NCY_4774CK5_4R3_C001_7AA384BC}
```

## substitution2

Tool used: https://planetcalc.com/8047/

![image](https://github.com/user-attachments/assets/74a92857-baaf-46e9-8fdc-a4fbe81a4e1f)

**Flag:**

```
picoCTF{N6R4M_4N41Y515_15_73D10U5_8E1BF808}
```
