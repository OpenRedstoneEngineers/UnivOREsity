# Hexadecimal


## Prerequisites

- [Binary](Binary.md#Binary)

---

## Contents

Topics to be covered in this lesson:

- [What is hexadecimal?](Hexadecimal.md#what-is-hexadecimal)
- [Translating from hexadecimal to binary](Hexadecimal.md#hexadecimal-to-binary)
- [Translating from binary to hecadecimal](Hexadecimal.md#binary-to-hexadecimal)


---

## What is Hexadecimal
Hexadecimal (or hex) is a base-16 number system. It uses sixteen distinct symbols:
- The numbers 0 to 9 represent values 0 to 9.
- The letters A to F represent values 10 to 15.

Hexadecimal is commonly used in computing and digital electronics because it is more compact than binary. For example, a single byte (8 bits) can be represented by two hexadecimal digits, making it easier to read and write.

Hexadecimal is often used in programming to represent:
- Memory addresses
- Color codes in web design (e.g., #FF5733)
- Machine code and assembly language

## Hexadecimal to Binary
The process to take a hexadecimal number and convert it to a binary one, is fairly straightforward. Each hexadecimal digit corrosponds to 4 binary digits. So all you have to do is decode one digit at a time and then conjoin the binary outputs one after another, in the same order as the previous hex digits were. The process to convert one hex digit to the 4 bits is as follows:

1. Take the inputed hex digit, for this example `0xD`
2. Compare that digit to a signal strength of the most significant bit in 4 bit binary, or 8.
3. If the input is larger than r equal to 8, you know that the 8s place must be on. If not, the 8s bit is off. `0xD` is greater or equal to 8, so this bit is on. Our current output is `0b1000`.
4. If its on, you must then subtract 8 from the input, so that the number is properly passed on to the 4s place. Our 8s bit for `0xD` was turned on, so we do `0xD - 0x8` (in Minecraft this can be done with a subtract mode comparator). This leaves us with `0x5`.
5. You then compare the new signal to 4. Again looking for greater than or equal to. `0x5` is greater than or equal to 4, so the 4s bit is on. Our new output is `0b1100`.
6. We then subtract 4 from that new number if the 4s bit was turned on. In our example, we do `0x5 - 0x4` leaving us with `0x1`.
7. You can probably guess that we do this process again with 2. Compare, and if greater than or equal to, turn on the 2s bit. In our example, our current signal is `0x1` which is not greater than or equal to 2, therefore we keep our output as `0b1100` and move on to our last bit.
8. The 1s bit is a bit different. You know that if after all of that, if there is signal, the 1s bit must be on, and if there isn't signal, the 1s bit must be off because the only possible value at this point is a 1 or a 0. Therefore, in our example, `0x1` is greater than 0, therefore we finish with the output as `0b1101`.

## Binary to Hexadecimal
The translation from binary to hexadecimal is much simpler. All you have to do is add together the values of the on bits every 4 bits. Forexample, turning the byte `0b11010110` into hex would be as follows:
1. The first four most significant bits are `1101`. That's `8 + 4 + 1`, not 2 since its respective bit is turned off (it's a 0). `8 + 4 + 1 = 13` which in hex is `D`.
2. We do the same thing with the next four bits, `0110`. `4 + 2 = 6` so the hex representation for these four bits is `6`.
3. You combine these how they were originally. The `D` is more significant than the `6` since it was more significant in the binary, so it comes first. Our final output is `0b11010110 = 0xD6`.