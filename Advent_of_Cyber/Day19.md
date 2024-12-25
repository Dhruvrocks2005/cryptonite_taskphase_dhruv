# Day 19: I merely noticed that you’re improperly stored, my dear secret!

**Connection to the Machine:**
To begin, a virtual machine was utilized for the analysis.

## TryUnlockMe - The Frostbitten OTP

- Started the game by running the command:

```
cd /home/ubuntu/Desktop/TryUnlockMe && ./TryUnlockMe
```

- Explored the game a bit and found a penguin asking for a PIN.

- Terminated the previous game instance and executed the following Frida command to intercept all the functions in the `libaocgame.so` library where some of the game logic is present:

```
frida-trace ./TryUnlockMe -i 'libaocgame.so!*'
```

- Revisited the NPC, the OTP function got logged on the console.

- Opened a new terminal, went to the `/home/ubuntu/Desktop/TryUnlockMe/__handlers__/libaocgame.so/` folder, and opened `Visual Studio Code` by running:

```
cd /home/ubuntu/Desktop/TryUnlockMe/__handlers__/libaocgame.so/
code .
```

- Selected the `_Z7set_otpi` JavaScript file. The i at the end of the set_otp function indicates that an integer will be passed as a parameter.

  ![image](https://github.com/user-attachments/assets/549b8469-2066-4a09-9282-ed035cc54a69)

- To get the parameter value, used the log function, specifying the first elements of the array `args` on the `onEnter` function:

```
log("Parameter:" + args[0].toInt32());
```

![image](https://github.com/user-attachments/assets/d599b74d-81c4-4723-9c23-3ad4b68a6226)

![image](https://github.com/user-attachments/assets/ae70d5aa-0f60-42e1-bccd-9e4db9731b22)

![image](https://github.com/user-attachments/assets/859a1fc9-01a7-44c4-b8e7-16b6d8c3869b)

---

## TryUnlockMe - A Wishlist for Billionaires

- Explored the new stage and found another penguin selling items, with a costly item named `Flag2`.

- This function has three integer parameters. I logged those values using the `log` function for each parameter.

```
defineHandler({
  onEnter(log, args, state) {
    log('_Z17validate_purchaseiii()');
    log('PARAMETER 1: '+ args[0]);
    log('PARAMETER 2: '+ args[1]);
    log('PARAMETER 3: '+ args[2]);

  },

  onLeave(log, retval, state) {
      
  }
});
```

![image](https://github.com/user-attachments/assets/76a38f41-3978-45c7-9999-b4c0afa035c2)

![image](https://github.com/user-attachments/assets/b9f99268-ca9a-4b9a-acaa-44bd6d234f87)

- The first parameter is the Item ID, the second is the price, and the third is the player's coins.

- I set the price as zero.

```
defineHandler({
  onEnter(log, args, state) {
    log('_Z17validate_purchaseiii()');
    args[1] = ptr(0)

  },

  onLeave(log, retval, state) {
      
  }
});
```

![image](https://github.com/user-attachments/assets/816947c5-58a3-4f18-a65b-46839a4a0199)

---

## TryUnlockMe - Naughty Fingers, Nice Hack

- This last stage was a bit more tricky because the output displayed by Frida is `_Z16check_biometricsPKc()`, which does not handle integers but only strings, making a bit more complex.

- Added the following code to the `onEnter()` function:
  
```
defineHandler({
  onEnter(log, args, state) {
    log('_Z16check_biometricsPKc()');
    log("PARAMETER:" + Memory.readCString(args[0]))
  },

  onLeave(log, retval, state) {
  }
});
```

![image](https://github.com/user-attachments/assets/2d6f2768-357f-466f-a78a-fb7fb5ec568f)

- Logged the return value of the function by adding the following log instruction in the `onLeave` function:

```
onLeave(log, retval, state) {
    log("The return value is: " + retval);
  }
});
```

![image](https://github.com/user-attachments/assets/174e49f1-40a4-45bd-b596-984c302123bd)

- So, the value returned is 0, which may indicate that it is a boolean flag set to `False`.

- Used the following instruction to set the return value to `True`:

  ```
  retval.replace(ptr(1))

![image](https://github.com/user-attachments/assets/a1016bf6-7579-4804-97ed-7123d166070a)

---

## Answers to the given questions:

What is the OTP flag?

```
THM{one_tough_password}
```

---

What is the billionaire item flag?

```
THM{credit_card_undeclined}
```

---

What is the biometric flag?

```
THM{dont_smash_your_keyboard}
```

---

![image](https://github.com/user-attachments/assets/c56c2fe1-9d54-464c-ae15-4f1b1aeb3f4b)
