# freakada 3301

We were given this image initially:

![freakada](https://github.com/user-attachments/assets/2eec47d8-6522-4f0e-8fef-314528ffad6c)

Opened it in a text editor:

![image](https://github.com/user-attachments/assets/fecc610e-7c62-403d-8c4d-b4684a8b051d)

Found this:

```
ZIT HQZI OL GWLEXKTR, WXZ ZIT ZKXZI SOTL OF ZIT LIQRGVL. LTTA ZIT HQZZTKFL. QDGFU ZIT EIQGL, Q WTQEGF QVQOZL: izzhl://woz.sn/yktqatlztof0. GFSN ZIT VGKZIN VOSS LTT ZIT XFLTTF. ZIT PGXKFTN IQL PXLZ WTUXF
```

this is a substitution cipher which on decoding gives:

![image](https://github.com/user-attachments/assets/23202eda-f07c-4816-a323-77176a691627)

```
THE PATH IS OBSCURED, BUT THE TRUTH LIES IN THE SHADOWS. SEEK THE PATTERNS. AMONG THE CHAOS, A BEACON AWAITS: https://bit.ly/freakestein0. ONLY THE WORTHY WILL SEE THE UNSEEN. THE JOURNEY HAS JUST BEGUN
```

This link led me to https://drive.proton.me/urls/JKQGGVGBP0#gnc8G2Sdj9hr where I found the following image:

![ducky (1)](https://github.com/user-attachments/assets/5f0800df-8764-4f9e-ba34-a1c1a27aa125)

Opened it in a text editor:

![image](https://github.com/user-attachments/assets/03820334-d050-4f2f-9f04-8b252afce772)

Found a link to this github https://github.com/freakada-3301

![image](https://github.com/user-attachments/assets/44308bb8-fbc6-4ab1-8d6e-ead7a6bcbfc2)

It had a single repository with 3 files.

The text in the README file looked like part of the flag: `1sk3vr3d_qw5yvvc}`.

The other two contained some `alien language` texts, which upon translating came out to be `We were here` and `Somehow forgotten`.

Found the next clues upon looking into the previous commits:

![image](https://github.com/user-attachments/assets/9d306977-0763-451a-ad1a-c1fb44086fc0)

![image](https://github.com/user-attachments/assets/23b8aa00-ce82-41ce-8952-f4fe68a131c6)

![image](https://github.com/user-attachments/assets/b26f453e-eb69-48f6-94d2-f7e636f93a31)

It was a poem and a timestamp, which was nothing but line:word:char, from the poem.

It yielded a string `httsdiscorggAHj7R2Qd` pointing to the link: https://discord.gg/AHj7R2Qd

It lead to a discord server named `freakada-3301`. The voice channel was a distraction. After listening to `thick of it` a few times, found a bot/app called `freakada` to which we had to send the message `3301`.

![image](https://github.com/user-attachments/assets/583badbf-3a99-4c63-85ba-e340da43b24e)

![image](https://github.com/user-attachments/assets/e6d73d5f-f2d1-4d8d-bb00-34d98a642eb2)

Two prime numbers which were a part of the original image, which turned out to be the dimension of the original image, `449x503` , upon multiplying the number was `745520947`

![image](https://github.com/user-attachments/assets/4fb7840c-6d80-40f5-9377-c26bef19a72d)

The bot replied with the coordinates of `Freaky Backshots Cliff`, where we found a qr code containing a link to a audio.

![image](https://github.com/user-attachments/assets/15421d29-b4b3-4213-86e2-a59df9593e33)

This audio when processed with a spectogram, gave the following message, `nite{4_wannabe_`  and a morse code beneath that which yielded the key to decode the second half from the github repo.

![image](https://github.com/user-attachments/assets/18e40412-ccf7-489e-b912-55b946cc0097)

We used Vigenere cipher decoder to decode the second half with this key and got `1nt3rn3t_my5tery}`

![image](https://github.com/user-attachments/assets/15797699-5d40-48d6-88a5-4706e2035931)

**FLag:**

```
nite{4_wannabe_1nt3rn3t_my5tery}
```


