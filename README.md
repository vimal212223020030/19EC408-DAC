# INTERFACING DAC WITH 8086 KIT AND GENERATING SAWTOOTH AND SQUARE WAVEFORMS

## AIM
To write an assembly language program in 8086 to generate Sawtooth and Square waveforms using DAC.

---

## APPARATUS REQUIRED

| S. No | Item              | Specification   | Quantity |
|-------|------------------|-----------------|----------|
| 1     | Microprocessor kit | 8086            | 1        |
| 2     | Power Supply      | +5 V DC, +12 V DC | 1      |
| 3     | DAC Interface board | -              | 1        |

---

## ALGORITHM

### Measurement of Analog Voltage
1. Send the digital value to DAC.  
2. Read the corresponding analog value at its output.  

### Waveform Generation

#### Square Waveform
1. Send low value (00) to the DAC.  
2. Introduce suitable delay.  
3. Send high value to DAC.  
4. Introduce delay.  
5. Repeat the above procedure.  

#### Sawtooth Waveform
1. Load low value (00) to accumulator.  
2. Send this value to DAC.  
3. Increment the accumulator.  
4. Repeat step (ii) and (iii) until accumulator value reaches FF.  
5. Repeat the above procedure from step 1.  

---

## PROGRAMS

# 8086 Assembly Programs – DAC Interfacing

## Program: Square Wave

| Memory Location | Opcode   | Program     | Comments                          |
|-----------------|----------|-------------|-----------------------------------|
| 1000            | C6 C0 36 | MOV AL,36H  | Load 36H in Accumulator           |
| 1003            | E6 CC    | OUT 0CCH,AL | Send through output port          |
| 1005            | C6 00 0A | MOV AL,10H  | Load 10H in Accumulator           |
| 1008            | E6 C8    | OUT 0C8H,AL | Send through output port          |
| 100A            | C6 C0 00 | MOV AL,00H  | Load count value in AL register   |
| 100D            | E6 C8    | OUT 0C8H,AL | Send through output port          |
| 100F            | F4       | HLT         | Stop                              |

### Assembly Code

```asm
MOV AL,36H        ; Load 36H in Accumulator
OUT 0CCH,AL       ; Send through output port

MOV AL,10H        ; Load 10H in Accumulator
OUT 0C8H,AL       ; Send through output port

MOV AL,00H        ; Load count value in AL register
OUT 0C8H,AL       ; Send through output port

