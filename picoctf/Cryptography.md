# Cryptograhy - Mandatory Challenges

## C3

**Description:**

```
This is the Custom Cyclical Cipher!
Download the ciphertext here.
Download the encoder here.
Enclose the flag in our wrapper for submission. If the flag was "example" you would submit "picoCTF{example}".
```
<br>

**Given encoder program:**

```
import sys
chars = ""
from fileinput import input
for line in input():
  chars += line

lookup1 = "\n \"#()*+/1:=[]abcdefghijklmnopqrstuvwxyz"
lookup2 = "ABCDEFGHIJKLMNOPQRSTabcdefghijklmnopqrst"

out = ""

prev = 0
for char in chars:
  cur = lookup1.index(char)
  out += lookup2[(cur - prev) % 40]
  prev = cur

sys.stdout.write(out)
```
<br>

**Given ciphertext:**

```
DLSeGAGDgBNJDQJDCFSFnRBIDjgHoDFCFtHDgJpiHtGDmMAQFnRBJKkBAsTMrsPSDDnEFCFtIbEDtDCIbFCFtHTJDKerFldbFObFCFtLBFkBAAAPFnRBJGEkerFlcPgKkImHnIlATJDKbTbFOkdNnsgbnJRMFnRBNAFkBAAAbrcbTKAkOgFpOgFpOpkBAAAAAAAiClFGIPFnRBaKliCgClFGtIBAAAAAAAOgGEkImHnIl
```
<br>

**Approach:** 

The script uses lookup1 to find the index of each character in the ciphertext and maps it to lookup2, using a dynamic offset (prev).

To decrypt, we need to reverse the process: for each character in lookup2, find the index, adjust by prev (moving backward), then map it back to lookup1.

Using the same lookup1 and lookup2, iterate backward through the ciphertext to reveal the original message.

<br>

**Script to reverse the cypher:**

```
ciphertext = "DLSeGAGDgBNJDQJDCFSFnRBIDjgHoDFCFtHDgJpiHtGDmMAQFnRBJKkBAsTMrsPSDDnEFCFtIbEDtDCIbFCFtHTJDKerFldbFObFCFtLBFkBAAAPFnRBJGEkerFlcPgKkImHnIlATJDKbTbFOkdNnsgbnJRMFnRBNAFkBAAAbrcbTKAkOgFpOgFpOpkBAAAAAAAiClFGIPFnRBaKliCgClFGtIBAAAAAAAOgGEkImHnIl"

lookup1 = "\n \"#()*+/1:=[]abcdefghijklmnopqrstuvwxyz"
lookup2 = "ABCDEFGHIJKLMNOPQRSTabcdefghijklmnopqrst"

decrypted_text = ""

prev = 0
for char in ciphertext:
    # Find the index of `char` in lookup2 (as it's encrypted)
    cur = lookup2.index(char)
    # Reverse the cyclical shift based on `prev`
    original_index = (cur + prev) % 40
    # Append the character from lookup1 at the decrypted index
    decrypted_text += lookup1[original_index]
    # Update `prev` to current character's index in lookup1 for next iteration
    prev = original_index

# Print the decrypted message
print(decrypted_text)
```
<br>

![image](https://github.com/user-attachments/assets/1ab7028f-3eaf-49c5-809f-e4dce7d8350f)

<br>

**Output:**

```
#asciiorder
#fortychars
#selfinput
#pythontwo

chars = ""
from fileinput import input
for line in input():
    chars += line
b = 1 / 1

for i in range(len(chars)):
    if i == b * b * b:
        print chars[i] #prints
        b += 1 / 1
```
<br>

The program would evaluate indices at b<sup>3</sup> = 1, 8, 27, 64, ... as it cubes the integer values of `b`.

The program will print characters from positions 1, 8, 27, ...

It essentially extracts characters from the input at cubic indices.

The `selfinput` comment given indicates that the above output will be the input for the program.

 <br>

![image](https://github.com/user-attachments/assets/23e73984-7c7c-41a9-9a5d-e3d98046b8fa)

<br>

I fixed the code a bit (brackets were missing from print statement), then ran it and got the output as `adlibs`.

<br>

**Incorrect Tangents:**

Initially, I didn't notice the `selfinput` comment, so I tried to provide the ciphertext, lookup1 and lookup2 as input for the second program. That did not give me the correct flag so I analyzed everything and noticed the `selfinput` then.

<br>

**Flag:**

```
picoCTF{adlibs}
```

## Custom encryption

**Description:**

```
Can you get sense of this code file and write the function that will decode the given encrypted file content.
Find the encrypted file here flag_info and code file might be good to analyze and get the flag.
```
<br>

**Given encoder program:**

```
from random import randint
import sys


def generator(g, x, p):
    return pow(g, x) % p


def encrypt(plaintext, key):
    cipher = []
    for char in plaintext:
        cipher.append(((ord(char) * key*311)))
    return cipher


def is_prime(p):
    v = 0
    for i in range(2, p + 1):
        if p % i == 0:
            v = v + 1
    if v > 1:
        return False
    else:
        return True


def dynamic_xor_encrypt(plaintext, text_key):
    cipher_text = ""
    key_length = len(text_key)
    for i, char in enumerate(plaintext[::-1]):
        key_char = text_key[i % key_length]
        encrypted_char = chr(ord(char) ^ ord(key_char))
        cipher_text += encrypted_char
    return cipher_text


def test(plain_text, text_key):
    p = 97
    g = 31
    if not is_prime(p) and not is_prime(g):
        print("Enter prime numbers")
        return
    a = randint(p-10, p)
    b = randint(g-10, g)
    print(f"a = {a}")
    print(f"b = {b}")
    u = generator(g, a, p)
    v = generator(g, b, p)
    key = generator(v, a, p)
    b_key = generator(u, b, p)
    shared_key = None
    if key == b_key:
        shared_key = key
    else:
        print("Invalid key")
        return
    semi_cipher = dynamic_xor_encrypt(plain_text, text_key)
    cipher = encrypt(semi_cipher, shared_key)
    print(f'cipher is: {cipher}')


if __name__ == "__main__":
    message = sys.argv[1]
    test(message, "trudeau")
```
<br>

**Given encrypted flag:**

```
a = 89
b = 27
cipher is: [33588, 276168, 261240, 302292, 343344, 328416, 242580, 85836, 82104, 156744, 0, 309756, 78372, 18660, 253776, 0, 82104, 320952, 3732, 231384, 89568, 100764, 22392, 22392, 63444, 22392, 97032, 190332, 119424, 182868, 97032, 26124, 44784, 63444]
```

<br>

**Approach:** 

**1. Initial Analysis:**

First, I examined the encryption script (using claude) to understand the encryption process. The script revealed a multi-step encryption scheme:

1. Uses Diffie-Hellman key exchange to generate a shared key
2. Applies a custom XOR encryption with the key "trudeau"
3. Finally multiplies each character by (shared_key * 311)

**2. Breaking Down the Encryption Components:**

**Diffie-Hellman Implementation:**

```
def generator(g, x, p):
    return pow(g, x) % p
```

The script uses basic Diffie-Hellman with:
- Prime modulus (p) = 97
- Generator (g) = 31
- Private keys: a = 89, b = 27


**Custom XOR Encryption:**

```
def dynamic_xor_encrypt(plaintext, text_key):
    cipher_text = ""
    key_length = len(text_key)
    for i, char in enumerate(plaintext[::-1]):
        key_char = text_key[i % key_length]
        encrypted_char = chr(ord(char) ^ ord(key_char))
        cipher_text += encrypted_char
    return cipher_text
```

Notable aspects:
- Reverses the plaintext before XOR operation
- Uses cyclic key "trudeau"
- Character-by-character XOR operation

**3. Decryption Strategy:**

To decrypt the flag, I needed to:
1. Calculate the shared key using given parameters
2. Divide the ciphertext numbers by (shared_key * 311)
3. Apply XOR decryption with "trudeau"
4. Reverse the final string

<br>

**Script to reverse the cypher:**

```
def generator(g, x, p):
    return pow(g, x) % p

def decrypt(cipher, key):
    plaintext = []
    for num in cipher:
        # Reverse the encryption: num = (ord(char) * key * 311)
        # So char = num / (key * 311)
        if num != 0:  # Handle special case for 0
            char = chr(int(num / (key * 311)))
            plaintext.append(char)
        else:
            plaintext.append('\x00')  # Add null byte for 0 values
    return ''.join(plaintext)

def dynamic_xor_decrypt(ciphertext, text_key):
    plaintext = ""
    key_length = len(text_key)
    # Note: The original encryption reversed the string first, so we'll need to reverse our result
    for i, char in enumerate(ciphertext):
        key_char = text_key[i % key_length]
        decrypted_char = chr(ord(char) ^ ord(key_char))
        plaintext += decrypted_char
    return plaintext[::-1]  # Reverse the final result

def solve_ctf():
    # Given values from the encryption
    p = 97
    g = 31
    a = 89
    b = 27
    text_key = "trudeau"
    
    # Calculate shared key using Diffie-Hellman
    u = generator(g, a, p)
    v = generator(g, b, p)
    shared_key = generator(v, a, p)
    
    # Encrypted data from flag_info
    encrypted = [33588, 276168, 261240, 302292, 343344, 328416, 242580, 85836, 
                82104, 156744, 0, 309756, 78372, 18660, 253776, 0, 82104, 
                320952, 3732, 231384, 89568, 100764, 22392, 22392, 63444, 
                22392, 97032, 190332, 119424, 182868, 97032, 26124, 44784, 63444]
    
    # First decrypt using the shared key
    semi_decrypted = decrypt(encrypted, shared_key)
    
    # Then decrypt using XOR with the text_key
    flag = dynamic_xor_decrypt(semi_decrypted, text_key)
    
    return flag

if __name__ == "__main__":
    flag = solve_ctf()
    print(f"Decrypted flag: {flag}")
```

<br>

**Output:**

```
Decrypted flag: picoCTF{custom_d2cr0pt6d_dc499538}
```

<br>

![image](https://github.com/user-attachments/assets/109afc6e-50c9-4882-a4fd-7cff45983855)

<br>

![image](https://github.com/user-attachments/assets/efe83ccd-3173-40b1-9925-29c70ef10dc3)

<br>

**Flag:**

```
picoCTF{custom_d2cr0pt6d_dc499538}
```

**Resources Used:**
- Claude.ai

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
