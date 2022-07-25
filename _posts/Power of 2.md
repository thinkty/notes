---
category: algorithms
---

# Power of 2
Using bit manipulation, one can easily find if the given number (n >= 0) is a power of 2.
The core idea is that if a number is a power of 2, the binary form of that number will always have only one 1-bit.

> 2 = 0b10
> 4 = 2<sup>2</sup> = 0b100
> 8 = 2<sup>3</sup> = ob1000

Also, if we extract 1 from those numbers, it always results in a number with all bits being 1-bit.

> 2 - 1 = 1 = 0b1
> 4 - 1 = 3 = 0b11
> 8 - 1 = 7 = 0b111

If we execute an & operation on a number that is a power of 2 and that number subtracted by 1, it will always be 0.

> 2 & (2 - 1) = 0b10 & 0b01 = 0b00
> 4 & (4 - 1) = 0b100 & 0b011 = 0b00
> 8 & (8 - 1) = 0b1000 & 0b0111 = 0b000

###### Implementation
```
bool isPowerOf2(int n) {
	return n > 0 && !(n & n - 1);
}
```