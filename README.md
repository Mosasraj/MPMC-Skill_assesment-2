# Skill_assesment-2
# 8051 Microcontroller: Generate 500 µs Delay Using Timer 0 in Mode 2 and Toggle P1.3
## Aim:
To generate a 500 µs delay using Timer 0 in Mode 2 (8-bit auto-reload) on the 8051 microcontroller and toggle the output on Port 1.3, producing a square wave.
## Apparatus / Software Required:
+Keil µVision IDE
## Algorithm:
1.Start the program 

2.Configure Timer 0 in Mode 2:

  Mode 2 is 8-bit auto-reload.

  Load TH0 with the value CEH for 500 µs delay.

3.Load TL0 for initial count with the same value as TH0.

4.Start Timer 0 by setting TR0.

  Monitor Timer Overflow (TF0):

  Wait until TF0 becomes high.

5.Clear TF0 after overflow.

6.Toggle P1.3 after each timer overflow using CPL P1.3.

7.Repeat the process indefinitely to generate a continuous square wave.


# Program
```asm
ORG 0H          ; Program start

START: 
    MOV TMOD, #02H    ; Timer0, Mode2 (8-bit auto-reload)
    MOV TH0, #0CEH    ; Load TH0 for 500 µs delay
    MOV TL0, #0CEH    ; Load TL0 for first delay
    SETB TR0          ; Start Timer0

HERE: 
    JNB TF0, HERE     ; Wait until Timer0 overflows
    CLR TF0           ; Clear overflow flag
    CPL P1.3          ; Toggle P1.3
    SJMP HERE         ; Repeat loop

END

  
```
## Output
![WhatsApp Image 2025-10-25 at 11 39 40_a7e42377](https://github.com/user-attachments/assets/af34556d-781b-484e-b7ce-dab03562c7a3)

![WhatsApp Image 2025-10-25 at 11 40 09_4c2c4b3d](https://github.com/user-attachments/assets/d087208c-7f2a-42b6-b598-f13a8a4dbf67)

## Result
Successfully generated a 500 µs delay using Timer 0 in Mode 2.
