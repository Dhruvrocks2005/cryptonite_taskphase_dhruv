# Reverse Engineering

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

To make the program print "win," the argument passed to `func` must result in `w0` being `0` after all operations. Here's a breakdown of how the calculations work in `func` and how we can find the required input:

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

### Condition for "Win"
For the program to print "win," the final result (`w0`) must be `0`. So, the equation we need to solve is:

90 - input = 0

Rearranging, we get:

input = 90

### Flag Format Conversion
The flag format specifies a 32-bit hexadecimal representation. Converting `90` to hexadecimal:


90<sub>10</sub> = 5a<sub>16</sub>


To meet the 32-bit format with zero-padding, it becomes `0000005a`.

### Final Flag
The flag is:

picoCTF{0000005a}


**Flag:**

```
picoCTF{0000005a}
```
