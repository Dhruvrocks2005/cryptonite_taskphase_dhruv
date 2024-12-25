# Reverse Engineering - Mandatory Challenges

## vault-door-3

**Approach:** The flag is given in the program's source code, just need to decode/rearrange it a bit

```
import java.util.*;

class VaultDoor3 {
    public static void main(String args[]) {
        VaultDoor3 vaultDoor = new VaultDoor3();
        Scanner scanner = new Scanner(System.in);
        System.out.print("Enter vault password: ");
        String userInput = scanner.next();
	String input = userInput.substring("picoCTF{".length(),userInput.length()-1);
	if (vaultDoor.checkPassword(input)) {
	    System.out.println("Access granted.");
	} else {
	    System.out.println("Access denied!");
        }
    }

    // Our security monitoring team has noticed some intrusions on some of the
    // less secure doors. Dr. Evil has asked me specifically to build a stronger
    // vault door to protect his Doomsday plans. I just *know* this door will
    // keep all of those nosy agents out of our business. Mwa ha!
    //
    // -Minion #2671
    public boolean checkPassword(String password) {
        if (password.length() != 32) {
            return false;
        }
        char[] buffer = new char[32];
        int i;
        for (i=0; i<8; i++) {
            buffer[i] = password.charAt(i);
        }
        for (; i<16; i++) {
            buffer[i] = password.charAt(23-i);
        }
        for (; i<32; i+=2) {
            buffer[i] = password.charAt(46-i);
        }
        for (i=31; i>=17; i-=2) {
            buffer[i] = password.charAt(i);
        }
        String s = new String(buffer);
        return s.equals("jU5t_a_sna_3lpm12g94c_u_4_m7ra41");
    }
}
```

String after the operations: `jU5t_a_sna_3lpm12g94c_u_4_m7ra41`.

We need to reverse these 4 operations in order to obtain the original string and thus get the flag. 

- First Loop (i = 0 to 7):
  
  These characters remain unchanged.
  
  Result: `jU5t_a_s`
  
- Second Loop (i = 8 to 15):

  The characters are copied from indexes 15 to 8 of the password in reverse order, that is, the subString is reversed. (8 and 15 get exchanged, 9 and 14 get exchanged, 10 and 13 get exchanged, and 11 and 12 get exchanged)
  
  Result: `1mpl3_an`
  
- Third Loop (i = 16 to 30, i += 2):

  The even indexed elements in this range are reversed (exchanged with each other in reverse order - 16 and 30 get exchanged, 18 and 28 get exchanged, 20 and 26 get exchanged, and 22 and 24 get exchanged)

  Result: `4g r4 m_ 4_ u_ c7 9a 21`

- Fourth Loop (i = 31 to 17, i -= 2):
  
   These characters, at odd indexes in this range, remain unchanged. (Indexes: 17, 19, 21, 23, 25, 27, 29, 31)

   Result: `r4 m_ 4_ u_ c7 9a 21`

<br>

jU5t_a_s na_3lpm1 2g 94 c_ u_ 4_ m7 ra 41

jU5t_a_s 1mpl3_an 4g r4 m_ 4_ u_ c7 9a 21

**Flag:**

```
picoCTF{jU5t_a_s1mpl3_an4gr4m_4_u_c79a21}
```

## GDB baby step 1

Learned about `gdb` in the `Low Level Binary Intro` playlist on `picoCTF`:

```
GDB is a well-known debugger that can do disassembly as well. If you don’t have access to GDB on your own machine, I would recommend using our webshell to use GDB. If you already have some expertise in a different debugger/disassembler, by all means use that, but this playlist will be addressing these problems from a GDB perspective.

Revisit the hints in Obedient Cat if you need a refresher on downloading challenge artifacts to your webshell.

Start GDB by passing it the name of the program you’ve been given, i.e. $ gdb program_to_debug. If you need a refresher on how to make a file executable, see the hints in file-run1. This only matters if you run the program in GDB, but it’s a good habit to get into.

Once it loads, disassemble main with the command: (gdb) disassemble main, at this point, you should be presented with a disassembly listing very alike to the ones you have been dealing with.
```

Challenge Description:

```
Can you figure out what is in the eax register at the end of the main function? Put your answer in the picoCTF flag format: picoCTF{n} where n is the contents of the eax register in the decimal number base. If the answer was 0x11 your flag would be picoCTF{17}.
Disassemble this.
```

Command used:

```
gdb debugger0_a
(gdb) disassemble main
```

![image](https://github.com/user-attachments/assets/858496f9-5f11-412b-9040-7026c8182627)

**Disassembled Code:**

```
Dump of assembler code for function main:
   0x0000000000001129 <+0>:     endbr64
   0x000000000000112d <+4>:     push   %rbp
   0x000000000000112e <+5>:     mov    %rsp,%rbp
   0x0000000000001131 <+8>:     mov    %edi,-0x4(%rbp)
   0x0000000000001134 <+11>:    mov    %rsi,-0x10(%rbp)
   0x0000000000001138 <+15>:    mov    $0x86342,%eax
   0x000000000000113d <+20>:    pop    %rbp
   0x000000000000113e <+21>:    ret
End of assembler dump.
```

Content of the eax register: `0x86342`

Converting it to decimal format:

![image](https://github.com/user-attachments/assets/f3b8a880-f186-4f8b-b126-4d8b842acd3c)

**Flag:**

```
picoCTF{549698}
```

## ARMssembly 1

**Description:**

```
For what argument does this program print `win` with variables 68, 2 and 3? File: chall_1.S Flag format: picoCTF{XXXXXXXX} -> (hex, lowercase, no 0x, and 32 bits. ex. 5614267 would be picoCTF{0055aabb})
```

**Given Program:**

```
	.arch armv8-a
	.file	"chall_1.c"
	.text
	.align	2
	.global	func
	.type	func, %function
func:
	sub	sp, sp, #32
	str	w0, [sp, 12]
	mov	w0, 68
	str	w0, [sp, 16]
	mov	w0, 2
	str	w0, [sp, 20]
	mov	w0, 3
	str	w0, [sp, 24]
	ldr	w0, [sp, 20]
	ldr	w1, [sp, 16]
	lsl	w0, w1, w0
	str	w0, [sp, 28]
	ldr	w1, [sp, 28]
	ldr	w0, [sp, 24]
	sdiv	w0, w1, w0
	str	w0, [sp, 28]
	ldr	w1, [sp, 28]
	ldr	w0, [sp, 12]
	sub	w0, w1, w0
	str	w0, [sp, 28]
	ldr	w0, [sp, 28]
	add	sp, sp, 32
	ret
	.size	func, .-func
	.section	.rodata
	.align	3
.LC0:
	.string	"You win!"
	.align	3
.LC1:
	.string	"You Lose :("
	.text
	.align	2
	.global	main
	.type	main, %function
main:
	stp	x29, x30, [sp, -48]!
	add	x29, sp, 0
	str	w0, [x29, 28]
	str	x1, [x29, 16]
	ldr	x0, [x29, 16]
	add	x0, x0, 8
	ldr	x0, [x0]
	bl	atoi
	str	w0, [x29, 44]
	ldr	w0, [x29, 44]
	bl	func
	cmp	w0, 0
	bne	.L4
	adrp	x0, .LC0
	add	x0, x0, :lo12:.LC0
	bl	puts
	b	.L6
.L4:
	adrp	x0, .LC1
	add	x0, x0, :lo12:.LC1
	bl	puts
.L6:
	nop
	ldp	x29, x30, [sp], 48
	ret
	.size	main, .-main
	.ident	"GCC: (Ubuntu/Linaro 7.5.0-3ubuntu1~18.04) 7.5.0"
	.section	.note.GNU-stack,"",@progbits
```

**Approach: I asked ChatGPT to explain the program to me and it explained, solved and gave me the flag**

This assembly code is for the ARMv8-A architecture and contains two functions: `func` and `main`. Here’s a step-by-step breakdown of what each part is doing:

### `.arch armv8-a` and `.file "chall_1.c"`
These directives specify the architecture and source file for the assembly code.

### `func` Function
This function does some arithmetic operations and returns a result stored in `w0`. Let's look at the steps in detail.

1. **Setting Up the Stack:**  
   ```
   sub sp, sp, #32
   ```
   This allocates 32 bytes on the stack for local variables.

2. **Storing and Initializing Values:**
   ```
   str w0, [sp, 12]     ; Store the function argument w0 at offset 12 in the stack
   mov w0, 68           ; Move the value 68 into w0
   str w0, [sp, 16]     ; Store 68 at offset 16 in the stack
   mov w0, 2            ; Move the value 2 into w0
   str w0, [sp, 20]     ; Store 2 at offset 20
   mov w0, 3            ; Move 3 into w0
   str w0, [sp, 24]     ; Store 3 at offset 24
   ```

3. **Bit Shift Operation:**
   ```
   ldr w0, [sp, 20]     ; Load the value 2 from offset 20 into w0
   ldr w1, [sp, 16]     ; Load the value 68 from offset 16 into w1
   lsl w0, w1, w0       ; Logical shift left: w0 = 68 << 2 = 272
   str w0, [sp, 28]     ; Store 272 at offset 28
   ```

4. **Division Operation:**
   ```
   ldr w1, [sp, 28]     ; Load 272 into w1
   ldr w0, [sp, 24]     ; Load 3 into w0
   sdiv w0, w1, w0      ; Divide 272 by 3, w0 = 272 / 3 = 90
   str w0, [sp, 28]     ; Store the result (90) at offset 28
   ```

5. **Subtraction Operation:**
   ```
   ldr w1, [sp, 28]     ; Load 90 into w1
   ldr w0, [sp, 12]     ; Load the initial input from offset 12 into w0
   sub w0, w1, w0       ; Subtract the input from 90: w0 = 90 - input
   str w0, [sp, 28]     ; Store the final result at offset 28
   ```

6. **Return Value:**
   ```
   ldr w0, [sp, 28]     ; Load the final result into w0 to be returned
   add sp, sp, 32       ; Restore the stack pointer
   ret                  ; Return from the function with the result in w0
   ```

### `.LC0` and `.LC1` Strings
- `.LC0` holds `"You win!"`
- `.LC1` holds `"You Lose :("`

### `main` Function
This function is the program’s entry point and uses the result from `func` to print either `"You win!"` or `"You Lose :("`.

1. **Stack Setup for `main`:**
   ```
   stp x29, x30, [sp, -48]!
   add x29, sp, 0
   ```
   This sets up a stack frame by saving the frame pointer and return address.

2. **Parsing Input Argument:**
   ```
   ldr x0, [x29, 16]      ; Load the first argument pointer (argv) into x0
   add x0, x0, 8          ; Point to the first argument string (argv[1])
   ldr x0, [x0]           ; Dereference to get the string address
   bl atoi                ; Convert the string to an integer
   str w0, [x29, 44]      ; Store the integer result in offset 44
   ```

3. **Calling `func` with Argument:**
   ```
   ldr w0, [x29, 44]      ; Load the integer into w0
   bl func                ; Call `func` with this integer as an argument
   ```

4. **Checking `func` Result:**
   ```
   cmp w0, 0              ; Compare the result with 0
   bne .L4                ; Branch to .L4 if result is not 0
   ```

5. **Printing the Result:**
   - If `func` returns 0, it prints `"You win!"`.
   - Otherwise, it prints `"You Lose :("`.

### Summary
This program essentially checks if an integer input (from `argv[1]`) leads to a specific result after several arithmetic operations. If it matches a specific expected outcome (0), you win; otherwise, you lose.

### Breakdown of `func` Calculations

The function `func` follows these steps with an initial argument `input`:

1. **Initialize Variables:**
   - Store `input` at `sp + 12`.
   - Set `sp + 16` to `68`.
   - Set `sp + 20` to `2`.
   - Set `sp + 24` to `3`.

2. **First Calculation - Left Shift:**
   - Load `sp + 20` (`2`) into `w0`.
   - Load `sp + 16` (`68`) into `w1`.
   - Perform `w0 = w1 << w0`, which is `w0 = 68 << 2 = 272`.
   - Store `272` in `sp + 28`.

3. **Second Calculation - Division:**
   - Load `272` from `sp + 28` into `w1`.
   - Load `3` from `sp + 24` into `w0`.
   - Perform `w0 = w1 / w0`, which is `w0 = 272 / 3 = 90`.
   - Store `90` in `sp + 28`.

4. **Final Calculation - Subtraction:**
   - Load `90` from `sp + 28` into `w1`.
   - Load `input` from `sp + 12` into `w0`.
   - Perform `w0 = w1 - w0`, which is `w0 = 90 - input`.
   - Store this final value in `sp + 28`.

![image](https://github.com/user-attachments/assets/62d2f683-720b-42cc-abd5-fb659881e90a)

90<sub>10</sub> = 5a<sub>16</sub>

To meet the 32-bit format, it becomes `0000005a`.

**Flag:**

```
picoCTF{0000005a}
```

# Reverse Engineering - Extra Challenges

## vault-door-training

**Approach:** The flag is given in the program's source code

```
import java.util.*;

class VaultDoorTraining {
    public static void main(String args[]) {
        VaultDoorTraining vaultDoor = new VaultDoorTraining();
        Scanner scanner = new Scanner(System.in); 
        System.out.print("Enter vault password: ");
        String userInput = scanner.next();
	String input = userInput.substring("picoCTF{".length(),userInput.length()-1);
	if (vaultDoor.checkPassword(input)) {
	    System.out.println("Access granted.");
	} else {
	    System.out.println("Access denied!");
	}
   }

    // The password is below. Is it safe to put the password in the source code?
    // What if somebody stole our source code? Then they would know what our
    // password is. Hmm... I will think of some ways to improve the security
    // on the other doors.
    //
    // -Minion #9567
    public boolean checkPassword(String password) {
        return password.equals("w4rm1ng_Up_w1tH_jAv4_be8d9806f18");
    }
}
```

**Flag:**

```
picoCTF{w4rm1ng_Up_w1tH_jAv4_be8d9806f18}
```

## vault-door-1

**Approach:** The flag is given in the program's source code

Source Code:

```
import java.util.*;

class VaultDoor1 {
    public static void main(String args[]) {
        VaultDoor1 vaultDoor = new VaultDoor1();
        Scanner scanner = new Scanner(System.in);
        System.out.print("Enter vault password: ");
	String userInput = scanner.next();
	String input = userInput.substring("picoCTF{".length(),userInput.length()-1);
	if (vaultDoor.checkPassword(input)) {
	    System.out.println("Access granted.");
	} else {
	    System.out.println("Access denied!");
	}
    }

    // I came up with a more secure way to check the password without putting
    // the password itself in the source code. I think this is going to be
    // UNHACKABLE!! I hope Dr. Evil agrees...
    //
    // -Minion #8728
    public boolean checkPassword(String password) {
        return password.length() == 32 &&
               password.charAt(0)  == 'd' &&
               password.charAt(29) == 'a' &&
               password.charAt(4)  == 'r' &&
               password.charAt(2)  == '5' &&
               password.charAt(23) == 'r' &&
               password.charAt(3)  == 'c' &&
               password.charAt(17) == '4' &&
               password.charAt(1)  == '3' &&
               password.charAt(7)  == 'b' &&
               password.charAt(10) == '_' &&
               password.charAt(5)  == '4' &&
               password.charAt(9)  == '3' &&
               password.charAt(11) == 't' &&
               password.charAt(15) == 'c' &&
               password.charAt(8)  == 'l' &&
               password.charAt(12) == 'H' &&
               password.charAt(20) == 'c' &&
               password.charAt(14) == '_' &&
               password.charAt(6)  == 'm' &&
               password.charAt(24) == '5' &&
               password.charAt(18) == 'r' &&
               password.charAt(13) == '3' &&
               password.charAt(19) == '4' &&
               password.charAt(21) == 'T' &&
               password.charAt(16) == 'H' &&
               password.charAt(27) == '6' &&
               password.charAt(30) == 'f' &&
               password.charAt(25) == '_' &&
               password.charAt(22) == '3' &&
               password.charAt(28) == 'd' &&
               password.charAt(26) == 'f' &&
               password.charAt(31) == '4';
    }
}

```

Upon unscrambling it:

```
password.charAt(0)  == 'd'
password.charAt(1)  == '3'
password.charAt(2)  == '5'
password.charAt(3)  == 'c'
password.charAt(4)  == 'r'
password.charAt(5)  == '4'
password.charAt(6)  == 'm'
password.charAt(7)  == 'b'
password.charAt(8)  == 'l'
password.charAt(9)  == '3'
password.charAt(10) == '_'
password.charAt(11) == 't'
password.charAt(12) == 'H'
password.charAt(13) == '3'
password.charAt(14) == '_'
password.charAt(15) == 'c'
password.charAt(16) == 'H'
password.charAt(17) == '4'
password.charAt(18) == 'r'
password.charAt(19) == '4'
password.charAt(20) == 'c'
password.charAt(21) == 'T'
password.charAt(22) == '3'
password.charAt(23) == 'r'
password.charAt(24) == '5'
password.charAt(25) == '_'
password.charAt(26) == 'f'
password.charAt(27) == '6'
password.charAt(28) == 'd'
password.charAt(29) == 'a'
password.charAt(30) == 'f'
password.charAt(31) == '4'
```

**Flag:**

```
picoCTF{d35cr4mbl3_tH3_cH4r4cT3r5_f6daf4}
```

## vault-door-4

**Approach:** The flag is given in the program's source code

```
import java.util.*;

class VaultDoor4 {
    public static void main(String args[]) {
        VaultDoor4 vaultDoor = new VaultDoor4();
        Scanner scanner = new Scanner(System.in);
        System.out.print("Enter vault password: ");
        String userInput = scanner.next();
	String input = userInput.substring("picoCTF{".length(),userInput.length()-1);
	if (vaultDoor.checkPassword(input)) {
	    System.out.println("Access granted.");
	} else {
	    System.out.println("Access denied!");
        }
    }

    // I made myself dizzy converting all of these numbers into different bases,
    // so I just *know* that this vault will be impenetrable. This will make Dr.
    // Evil like me better than all of the other minions--especially Minion
    // #5620--I just know it!
    //
    //  .:::.   .:::.
    // :::::::.:::::::
    // :::::::::::::::
    // ':::::::::::::'
    //   ':::::::::'
    //     ':::::'
    //       ':'
    // -Minion #7781
    public boolean checkPassword(String password) {
        byte[] passBytes = password.getBytes();
        byte[] myBytes = {
            106 , 85  , 53  , 116 , 95  , 52  , 95  , 98  ,
            0x55, 0x6e, 0x43, 0x68, 0x5f, 0x30, 0x66, 0x5f,
            0142, 0131, 0164, 063 , 0163, 0137, 0146, 064 ,
            'a' , '8' , 'c' , 'd' , '8' , 'f' , '7' , 'e' ,
        };
        for (int i=0; i<32; i++) {
            if (passBytes[i] != myBytes[i]) {
                return false;
            }
        }
        return true;
    }
}
```

The given list contains integers in different formats (decimal, hexadecimal, octal, and characters) representing ASCII values. We need to convert each value to its corresponding character to obtain the flag.

- Decimal values:  
  (106) = `j`, (85) = `U`, (53) = `5`, (116) = `t`, (95) = `_`, (52) = `4`, (95) = `_`, (98) = `b`

- Hexadecimal values:  
  (0x55) = `U`, (0x6e) = `n`, (0x43) = `C`, (0x68) = `h`, (0x5f) = `_`, (0x30) = `0`, (0x66) = `f`, (0x5f) = `_`

- Octal values:  
  (0142) = `b`, (0131) = `Y`, (0164) = `t`, (063) = `3`, (0163) = `s`, (0137) = `_`, (0146) = `f`, (064) = `4`

- Character literals:  
  `'a'`, `'8'`, `'c'`, `'d'`, `'8'`, `'f'`, `'7'`, `'e'`

Putting it all together, the text is:

```
jU5t_4_bUnCh_0f_bYt3s_f4a8cd8f7e
```

**Flag:**

```
picoCTF{jU5t_4_bUnCh_0f_bYt3s_f4a8cd8f7e}
```
## vault-door-5

**Approach:** The flag is given in the program's source code

```
import java.net.URLDecoder;
import java.util.*;

class VaultDoor5 {
    public static void main(String args[]) {
        VaultDoor5 vaultDoor = new VaultDoor5();
        Scanner scanner = new Scanner(System.in);
        System.out.print("Enter vault password: ");
        String userInput = scanner.next();
	String input = userInput.substring("picoCTF{".length(),userInput.length()-1);
	if (vaultDoor.checkPassword(input)) {
	    System.out.println("Access granted.");
	} else {
	    System.out.println("Access denied!");
        }
    }

    // Minion #7781 used base 8 and base 16, but this is base 64, which is
    // like... eight times stronger, right? Riiigghtt? Well that's what my twin
    // brother Minion #2415 says, anyway.
    //
    // -Minion #2414
    public String base64Encode(byte[] input) {
        return Base64.getEncoder().encodeToString(input);
    }

    // URL encoding is meant for web pages, so any double agent spies who steal
    // our source code will think this is a web site or something, defintely not
    // vault door! Oh wait, should I have not said that in a source code
    // comment?
    //
    // -Minion #2415
    public String urlEncode(byte[] input) {
        StringBuffer buf = new StringBuffer();
        for (int i=0; i<input.length; i++) {
            buf.append(String.format("%%%2x", input[i]));
        }
        return buf.toString();
    }

    public boolean checkPassword(String password) {
        String urlEncoded = urlEncode(password.getBytes());
        String base64Encoded = base64Encode(urlEncoded.getBytes());
        String expected = "JTYzJTMwJTZlJTc2JTMzJTcyJTc0JTMxJTZlJTY3JTVm"
                        + "JTY2JTcyJTMwJTZkJTVmJTYyJTYxJTM1JTY1JTVmJTM2"
                        + "JTM0JTVmJTMwJTYyJTM5JTM1JTM3JTYzJTM0JTY2";
        return base64Encoded.equals(expected);
    }
}
```

Base64 encoded String:

```
JTYzJTMwJTZlJTc2JTMzJTcyJTc0JTMxJTZlJTY3JTVmJTY2JTcyJTMwJTZkJTVmJTYyJTYxJTM1JTY1JTVmJTM2JTM0JTVmJTMwJTYyJTM5JTM1JTM3JTYzJTM0JTY2
```

![image](https://github.com/user-attachments/assets/30441fdf-4102-4816-9d35-608d4e811c3f)

URL encoded String:

```
%63%30%6e%76%33%72%74%31%6e%67%5f%66%72%30%6d%5f%62%61%35%65%5f%36%34%5f%30%62%39%35%37%63%34%66
```

![image](https://github.com/user-attachments/assets/ebf4ea8c-3b4c-4404-83d7-b2366069219e)

Original String:

```
c0nv3rt1ng_fr0m_ba5e_64_0b957c4f
```

**Flag:**

```
picoCTF{c0nv3rt1ng_fr0m_ba5e_64_0b957c4f}
```

Tool used: https://cryptii.com/

## vault-door-6

**Approach:** The flag is given in the program's source code

```
import java.util.*;

class VaultDoor6 {
    public static void main(String args[]) {
        VaultDoor6 vaultDoor = new VaultDoor6();
        Scanner scanner = new Scanner(System.in);
        System.out.print("Enter vault password: ");
        String userInput = scanner.next();
	String input = userInput.substring("picoCTF{".length(),userInput.length()-1);
	if (vaultDoor.checkPassword(input)) {
	    System.out.println("Access granted.");
	} else {
	    System.out.println("Access denied!");
        }
    }

    // Dr. Evil gave me a book called Applied Cryptography by Bruce Schneier,
    // and I learned this really cool encryption system. This will be the
    // strongest vault door in Dr. Evil's entire evil volcano compound for sure!
    // Well, I didn't exactly read the *whole* book, but I'm sure there's
    // nothing important in the last 750 pages.
    //
    // -Minion #3091
    public boolean checkPassword(String password) {
        if (password.length() != 32) {
            return false;
        }
        byte[] passBytes = password.getBytes();
        byte[] myBytes = {
            0x3b, 0x65, 0x21, 0xa , 0x38, 0x0 , 0x36, 0x1d,
            0xa , 0x3d, 0x61, 0x27, 0x11, 0x66, 0x27, 0xa ,
            0x21, 0x1d, 0x61, 0x3b, 0xa , 0x2d, 0x65, 0x27,
            0xa , 0x6c, 0x60, 0x37, 0x30, 0x60, 0x31, 0x36,
        };
        for (int i=0; i<32; i++) {
            if (((passBytes[i] ^ 0x55) - myBytes[i]) != 0) {
                return false;
            }
        }
        return true;
    }
}
```

If A XOR B = C, then C XOR B = A

![image](https://github.com/user-attachments/assets/a9225bd8-1505-4626-b24c-a2bf8b0a9e91)

Original String:

```
n0t_mUcH_h4rD3r_tH4n_x0r_95be5dc
```

**Flag:**

```
picoCTF{n0t_mUcH_h4rD3r_tH4n_x0r_95be5dc}
```

## vault-door-7

**Approach:** The flag is given in the program's source code

```
import java.util.*;
import javax.crypto.Cipher;
import javax.crypto.spec.SecretKeySpec;
import java.security.*;

class VaultDoor7 {
    public static void main(String args[]) {
        VaultDoor7 vaultDoor = new VaultDoor7();
        Scanner scanner = new Scanner(System.in);
        System.out.print("Enter vault password: ");
        String userInput = scanner.next();
	String input = userInput.substring("picoCTF{".length(),userInput.length()-1);
	if (vaultDoor.checkPassword(input)) {
	    System.out.println("Access granted.");
	} else {
	    System.out.println("Access denied!");
        }
    }

    // Each character can be represented as a byte value using its
    // ASCII encoding. Each byte contains 8 bits, and an int contains
    // 32 bits, so we can "pack" 4 bytes into a single int. Here's an
    // example: if the hex string is "01ab", then those can be
    // represented as the bytes {0x30, 0x31, 0x61, 0x62}. When those
    // bytes are represented as binary, they are:
    //
    // 0x30: 00110000
    // 0x31: 00110001
    // 0x61: 01100001
    // 0x62: 01100010
    //
    // If we put those 4 binary numbers end to end, we end up with 32
    // bits that can be interpreted as an int.
    //
    // 00110000001100010110000101100010 -> 808542562
    //
    // Since 4 chars can be represented as 1 int, the 32 character password can
    // be represented as an array of 8 ints.
    //
    // - Minion #7816
    public int[] passwordToIntArray(String hex) {
        int[] x = new int[8];
        byte[] hexBytes = hex.getBytes();
        for (int i=0; i<8; i++) {
            x[i] = hexBytes[i*4]   << 24
                 | hexBytes[i*4+1] << 16
                 | hexBytes[i*4+2] << 8
                 | hexBytes[i*4+3];
        }
        return x;
    }

    public boolean checkPassword(String password) {
        if (password.length() != 32) {
            return false;
        }
        int[] x = passwordToIntArray(password);
        return x[0] == 1096770097
            && x[1] == 1952395366
            && x[2] == 1600270708
            && x[3] == 1601398833
            && x[4] == 1716808014
            && x[5] == 1734291511
            && x[6] == 960049251
            && x[7] == 1681089078;
    }
}
```

Decimal to Hexadecimal Conversion:

![image](https://github.com/user-attachments/assets/a1e4a94d-7109-46bf-8dfc-80e7b3880c45)

Hex to Text Conversion:

![image](https://github.com/user-attachments/assets/1541d2e3-1f35-474c-9d49-f1e93b486977)

Original String:

```
A_b1t_0f_b1t_sh1fTiNg_07990cd3b6
```

**Flag:**

```
picoCTF{A_b1t_0f_b1t_sh1fTiNg_07990cd3b6}
```

Tools used:

https://cryptii.com/

https://www.duplichecker.com/hex-to-text.php

## vault-door-8

**Approach:** Reverse or undo the bits that were switched

In the `scramble()` method, bits of each character in the password are scrambled through a specific sequence of bit switches. To reverse the scrambling, we need to perform these bit swaps in reverse order. This will effectively "undo" the scrambling.

Source Code:

```
// These pesky special agents keep reverse engineering our source code and then
// breaking into our secret vaults. THIS will teach those sneaky sneaks a
// lesson.
//
// -Minion #0891

import java.util.*;
import javax.crypto.Cipher;
import javax.crypto.spec.SecretKeySpec;
import java.security.*;

class VaultDoor8 {
    public static void main(String args[]) {
        Scanner b = new Scanner(System.in);
        System.out.print("Enter vault password: ");
        String c = b.next();
        String f = c.substring(8, c.length() - 1);
        VaultDoor8 a = new VaultDoor8();
        
        if (a.checkPassword(f)) {
            System.out.println("Access granted.");
        } else {
            System.out.println("Access denied!");
        }
    }

    public char[] scramble(String password) {
        /* Scramble a password by transposing pairs of bits. */
        char[] a = password.toCharArray();
        
        for (int b = 0; b < a.length; b++) {
            char c = a[b];
            c = switchBits(c, 1, 2);
            c = switchBits(c, 0, 3);
            /* c = switchBits(c, 14, 3); c = switchBits(c, 2, 0); */
            c = switchBits(c, 5, 6);
            c = switchBits(c, 4, 7);
            c = switchBits(c, 0, 1);
            /* d = switchBits(d, 4, 5); e = switchBits(e, 5, 6); */
            c = switchBits(c, 3, 4);
            c = switchBits(c, 2, 5);
            c = switchBits(c, 6, 7);
            a[b] = c;
        }
        
        return a;
    }

    public char switchBits(char c, int p1, int p2) {
        /* Move the bit in position p1 to position p2, and move the bit
           that was in position p2 to position p1. Precondition: p1 < p2 */
        char mask1 = (char) (1 << p1);
        char mask2 = (char) (1 << p2);
        /* char mask3 = (char)(1 << p1 << p2); mask1++; mask1--; */
        char bit1 = (char) (c & mask1);
        char bit2 = (char) (c & mask2);
        /* System.out.println("bit1 " + Integer.toBinaryString(bit1));
           System.out.println("bit2 " + Integer.toBinaryString(bit2)); */
        char rest = (char) (c & ~(mask1 | mask2));
        char shift = (char) (p2 - p1);
        char result = (char) ((bit1 << shift) | (bit2 >> shift) | rest);
        
        return result;
    }

    public boolean checkPassword(String password) {
        char[] scrambled = scramble(password);
        char[] expected = {
            0xF4, 0xC0, 0x97, 0xF0, 0x77, 0x97, 0xC0, 0xE4, 0xF0, 0x77,
            0xA4, 0xD0, 0xC5, 0x77, 0xF4, 0x86, 0xD0, 0xA5, 0x45, 0x96,
            0x27, 0xB5, 0x77, 0xC2, 0xD2, 0x95, 0xA4, 0xF0, 0xD2, 0xD2,
            0xC1, 0x95
        };
        
        return Arrays.equals(scrambled, expected);
    }
}
```

Program to undo the bit switches while reusing the `switchBits()` method

```
public class VaultDoor8 {
    public static void main(String[] args) {
        char[] expected = {
            0xF4, 0xC0, 0x97, 0xF0, 0x77,
            0x97, 0xC0, 0xE4, 0xF0, 0x77,
            0xA4, 0xD0, 0xC5, 0x77, 0xF4,
            0x86, 0xD0, 0xA5, 0x45, 0x96,
            0x27, 0xB5, 0x77, 0xC2, 0xD2,
            0x95, 0xA4, 0xF0, 0xD2, 0xD2,
            0xC1, 0x95
        };

        char[] unscrambledPassword = unscramble(expected);
        System.out.println("Unscrambled password: " + new String(unscrambledPassword));
    }

    public static char[] unscramble(char[] scrambledPassword) {
        for (int b = 0; b < scrambledPassword.length; b++) {
            char c = scrambledPassword[b];
            c = switchBits(c, 6, 7);
            c = switchBits(c, 2, 5);
            c = switchBits(c, 3, 4);
            c = switchBits(c, 0, 1);
            c = switchBits(c, 4, 7);
            c = switchBits(c, 5, 6);
            c = switchBits(c, 0, 3);
            c = switchBits(c, 1, 2);
            scrambledPassword[b] = c;
        }
        return scrambledPassword;
    }

    public static char switchBits(char c, int p1, int p2) {
        char mask1 = (char)(1 << p1);
        char mask2 = (char)(1 << p2);
        char bit1 = (char)(c & mask1);
        char bit2 = (char)(c & mask2);
        char rest = (char)(c & ~(mask1 | mask2));
        char shift = (char)(p2 - p1);
        return (char)((bit1 << shift) | (bit2 >> shift) | rest);
    }
}
```

`unscramble()` Method: This method takes each character in the scrambled expected array and applies the reverse sequence of bit swaps to retrieve the original password.

Output:

```
Unscrambled password: s0m3_m0r3_b1t_sh1fTiNg_89eb3994e
```

**Flag:**

```
picoCTF{s0m3_m0r3_b1t_sh1fTiNg_89eb3994e}
```

## keygenme-py

The flag is `picoCTF{1n_7h3_|<3y_of_xxxxxxxx}` where `xxxxxxxx` is the dynamic part that changes based on the username `SCHOFIELD`.

The dynamic part of the flag is derived from the username SCHOFIELD by hashing it with SHA-256 and extracting specific characters from the hash.

The code specifically grabs the following characters from the SHA-256 hash: hash[4], hash[5], hash[3, ]hash[6], hash[2], hash[7], hash[1], hash[8].

Calculating the dynamic part of the flag:

![image](https://github.com/user-attachments/assets/b117489f-c1ab-4e59-80c9-026d8b3ed624)

**Flag:**

```
picoCTF{1n_7h3_|<3y_of_e584b363}
```

## Transformation

**Description:**

```
I wonder what this really is... enc ''.join([chr((ord(flag[i]) << 8) + ord(flag[i + 1])) for i in range(0, len(flag), 2)])
```

**Operation**:

   - `ord(flag[i])`: Converts the character at position `i` to its Unicode code point.
   - `ord(flag[i + 1])`: Converts the next character to its Unicode code point.
   - `(ord(flag[i]) << 8)`: Shifts the first character's code point 8 bits to the left.
   - `+ ord(flag[i + 1])`: Adds the second character's code point to the shifted value.
   - `chr(...)`: Converts this combined value back to a character.

The loop processes the `flag` in chunks of 2 characters, producing one encoded character for each pair.


**Decoding the `enc` String**:

To decode it, we need to reverse the process:
1. Split each character in `enc` back into two original flag characters.
2. For a given encoded character `c`:
   - `val = ord(c)`: Get its Unicode code point.
   - `char1 = chr(val >> 8)`: Extract the first character by shifting 8 bits to the right. Extracts the upper 8 bits.
   - `char2 = chr(val & 0xFF)`: Extract the second character using a bitwise AND with `0xFF`. Extracts the lower 8 bits.

**Program to decode:**

```
enc = "灩捯䍔䙻ㄶ形楴獟楮獴㌴摟潦弸彥ㄴㅡて㝽"

decoded_flag = ''
for c in enc:
    val = ord(c)
    char1 = chr(val >> 8)  
    char2 = chr(val & 0xFF)  
    decoded_flag += char1 + char2

print("Decoded flag:", decoded_flag)
```

**Flag:**

```
picoCTF{16_bits_inst34d_of_8_e141a0f7}
```

## Safe Opener

Program:
```
import java.io.*;
import java.util.*;  
public class SafeOpener {
    public static void main(String args[]) throws IOException {
        BufferedReader keyboard = new BufferedReader(new InputStreamReader(System.in));
        Base64.Encoder encoder = Base64.getEncoder();
        String encodedkey = "";
        String key = "";
        int i = 0;
        boolean isOpen;
        

        while (i < 3) {
            System.out.print("Enter password for the safe: ");
            key = keyboard.readLine();

            encodedkey = encoder.encodeToString(key.getBytes());
            System.out.println(encodedkey);
              
            isOpen = openSafe(encodedkey);
            if (!isOpen) {
                System.out.println("You have  " + (2 - i) + " attempt(s) left");
                i++;
                continue;
            }
            break;
        }
    }
    
    public static boolean openSafe(String password) {
        String encodedkey = "cGwzYXMzX2wzdF9tM18xbnQwX3RoM19zYWYz";
        
        if (password.equals(encodedkey)) {
            System.out.println("Sesame open");
            return true;
        }
        else {
            System.out.println("Password is incorrect\n");
            return false;
        }
    }
}
```

According to the program, the encoded key is `cGwzYXMzX2wzdF9tM18xbnQwX3RoM19zYWYz`, which is encoded in Base64.

![image](https://github.com/user-attachments/assets/d1bcd48c-1cda-4b84-824e-f7d8fb556910)

**Flag:**

```
picoCTF{pl3as3_l3t_m3_1nt0_th3_saf3}
```

## Safe Opener 2

I found the flag when I opened the file with a text editor.

![image](https://github.com/user-attachments/assets/30886d31-17de-4e27-9ee8-92d6b09b1869)

**Flag:**

```
picoCTF{SAf3_0p3n3rr_y0u_solv3d_it_198203f7}
```

## Picker I

**win() function:**

```
def win():
  # This line will not work locally unless you create your own 'flag.txt' in
  #   the same directory as this script
  flag = open('flag.txt', 'r').read()
  #flag = flag[:-1]
  flag = flag.strip()
  str_flag = ''
  for c in flag:
    str_flag += str(hex(ord(c))) + ' '
  print(str_flag)
```

**command used:**

```
root@DhruvsPC:~# nc saturn.picoctf.net 53990
Try entering "getRandomNumber" without the double quotes...
==> win
0x70 0x69 0x63 0x6f 0x43 0x54 0x46 0x7b 0x34 0x5f 0x64 0x31 0x34 0x6d 0x30 0x6e 0x64 0x5f 0x31 0x6e 0x5f 0x37 0x68 0x33 0x5f 0x72 0x30 0x75 0x67 0x68 0x5f 0x63 0x65 0x34 0x62 0x35 0x64 0x35 0x62 0x7d
```
**Decoding flag from hex:**

![image](https://github.com/user-attachments/assets/7266edef-6061-4c30-997c-999c3f0c45ec)

**Flag:**

```
picoCTF{4_d14m0nd_1n_7h3_r0ugh_ce4b5d5b}
```

