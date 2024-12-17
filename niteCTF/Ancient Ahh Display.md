# Ancient Ahh Display

In the given files, `display.txt` and `fpga_inputs.xlsx` :

display.txt:
```
module display (i,o,anode); 
input [4:0]  i;
output reg [6:0]  o;    
output [3:0] anode; 
assign anode = 4'b0001; 

always @(i) 
case (i) 
    5'b00000 :  o = 7'b1000000; 
    5'b00001 :  o = 7'b1111001; 
    5'b00010 :  o = 7'b0100100; 
    5'b00011 :  o = 7'b0110000; 
    5'b00100 :  o = 7'b0011001; 
    5'b00101 :  o = 7'b0010010; 
    5'b00110 :  o = 7'b0000010; 
    5'b00111 :  o = 7'b1111000; 
    5'b01000 :  o = 7'b0000000; 
    5'b01001 :  o = 7'b0010000; 
    5'b01010 :  o = 7'b0001000; 
    5'b01011 :  o = 7'b0000011; 
    5'b01100 :  o = 7'b1000110; 
    5'b01101 :  o = 7'b0100001; 
    5'b01110 :  o = 7'b0000100; 
    5'b01111 :  o = 7'b0001110; 
    5'b10000 :  o = 7'b0001001; 
    5'b10001 :  o = 7'b1101111; 
    5'b10010 :  o = 7'b1100001; 
    5'b10011 :  o = 7'b1000111; 
    5'b10100 :  o = 7'b0101011; 
    5'b10101 :  o = 7'b0001100; 
    5'b10110 :  o = 7'b0011000; 
    5'b10111 :  o = 7'b0101111; 
    5'b11000 :  o = 7'b0000111; 
    5'b11001 :  o = 7'b1000001; 
    5'b11010 :  o = 7'b0010001; 
    5'b11011 :  o = 7'b1000110; 
    5'b11100 :  o = 7'b1110000; 
    5'b11101 :  o = 7'b0111111; 

    default:  o = 7'b1110111;
endcase 

endmodule



// i[0] -> V17
// i[1] -> W16
// i[2] -> W13
// i[3] -> A3
// i[4] -> W2
// anode -> anode display pin
```

fpga_inputs.xlsx:

![image](https://github.com/user-attachments/assets/4cf3e6b1-ee8a-4f96-93d6-252da388d1ca)

---

I formatted the inputs given in the excel sheet according to the instructions from the text file.

Got the inputs and the corresponding outputs but the given 7 bit binary numbers from the output were not getting converted to text or ascii.

Upon a bit of research, I figured out that it was supposed to be for the 7 segement display.

![image](https://github.com/user-attachments/assets/0a5177b1-4df0-494b-850c-603cb9b60d3e)



Used this to decode the 7 segment display: https://www.dcode.fr/7-segment-display


![image](https://github.com/user-attachments/assets/7920da15-4cfe-42bd-b627-73a70252892d)


Thus I got the flag after converting everything to 7 segment display:

![image](https://github.com/user-attachments/assets/5996eeeb-18b5-48f4-810c-20a138ddf253)

**Flag:**

```
nite{tr0UbLe_bUbbLe_L0L}
```
