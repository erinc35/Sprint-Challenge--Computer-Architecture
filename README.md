# Sprint-Challenge--Computer-Architecture

## Binary, Decimal, and Hex

Complete the following problems:

* Convert `11001111` binary


    1100 C
    1111 F
    to hex: CF

    to decimal: 128+64+0+0+8+4+2+1 = 207


* Convert `4C` hex

    to binary: 1001100

    to decimal: 76


* Convert `68` decimal

    to binary: 1000100

    to hex: 44


## Architecture

Short answer:

* Explain how the CPU provides concurrency or parallelism:

    Since CPU can process only one task at the time, to provide concurrency the CPU switch processes, it saves the state in the stack, then update the state with the new instructions until it completes and in the end reprocesses the previous CPU state and resumes processing.

* Describe assembly language and machine language:

    Machine language is just binary which is the lowest level. It carries instructions for CPU.

    Assembly language carries the same instructions in a different level so humans can read nad interpret, too.

## Coding

Options for submission, whichever is easier for you:

* Copy your source into this repo, or...
* Submit a PR for the Sprint Challenge from the `Computer-Architecture` repo
  you've been using all along.

Sprint Challenge:

[See the LS-8 spec for details](https://github.com/LambdaSchool/Computer-Architecture/blob/master/LS8-SPEC.md)

Add the `CMP` instruction and `equal` flag to your LS-8.

Add the `JMP` instruction.

Add the `JEQ` and `JNE` instructions.


[Here is some code](sctest.ls8) that exercises the above instructions.
It should print:

```
1
4
5
```

```
# Code to test the Sprint Challenge
#
# Expected output:
# 1
# 4
# 5

10011001 # LDI R0,10
00000000
00001010
10011001 # LDI R1,20
00000001
00010100
10011001 # LDI R2,TEST1
00000010
00010011
10100000 # CMP R0,R1
00000000
00000001
01010001 # JEQ R2        Does not jump because R0 != R1
00000010
10011001 # LDI R3,1
00000011
00000001
01000011 # PRN R3        Prints 1
00000011

# TEST1 (19):
10011001 # LDI R2,TEST2
00000010
00100000
10100000 # CMP R0,R1
00000000
00000001
01010010 # JNE R2        Jumps because R0 != R1
00000010
10011001 # LDI R3,2
00000011
00000010
01000011 # PRN R3        Skipped--does not print
00000011

# TEST2 (32):
10011001 # LDI R1,10
00000001
00001010
10011001 # LDI R2,TEST3
00000010
00110000
10100000 # CMP R0,R1
00000000
00000001
01010001 # JEQ R2        Jumps becuase R0 == R1
00000010
10011001 # LDI R3,3
00000011
00000011
01000011 # PRN R3        Skipped--does not print
00000011

# TEST3 (48):
10011001 # LDI R2,TEST4
00000010
00111101
10100000 # CMP R0,R1
00000000
00000001
01010010 # JNE R2        Does not jump because R0 == R1
00000010
10011001 # LDI R3,4
00000011
00000100
01000011 # PRN R3        Prints 4
00000011

# TEST4 (61):
10011001 # LDI R3,5
00000011
00000101
01000011 # PRN R3        Prints 5
00000011
10011001 # LDI R2,TEST5
00000010
01001001
01010000 # JMP R2        Jumps unconditionally
00000010
01000011 # PRN R3        Skipped-does not print
00000011

# TEST5 (73):
00000001 # HLT
```

