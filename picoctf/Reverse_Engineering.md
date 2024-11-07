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
