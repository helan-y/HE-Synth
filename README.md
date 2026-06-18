# HE Synth

## About
A custom, compact, modular velocity-sensitive digital synthesizer, made with Hall-Effect keyswitches and DaisySeed. 

## Idea
I want to make music and I do not have money but I do have blood, sweat, and many, many tears. This is also a proof of concept towards bigger projects I want to make in the future!
- MIDI keyboard with trackballs for keys! like a roli seaboard but weird and isomorphic! what if piano could vibrato!!
- bigger modular midi (repeating pcb boards in series one for each octave) keyboard with keycaps like piano keys!
- sampler! vocoder! etc!

## Features
Hardware features:
- Velocity-sensitive! Aftertouch! Two/three/more octaves!
- Fully **modular**. Add more octaves, swap out MIDI controllers, swap out the synthesizer. Assembled with separate custom PCB boards for maximum customizability. 
- In-build audio! 3.5 mm headphone jack or speaker. 

Constantly updating firmware:
- Different presets! Different sound envelopes!
- There's even a looper!
- And a display!

## PCB
The PCB design is divided into four parts:
1. Main Board
2. Power Distribution Board (PDB)
3. Octave PCBs
    - 12 Hall-Effect Keyswitches
    - STM32 MCU Chip
    - UART data transmission
4. MIDI-Out PCB
    - ESP32
    - MIDI OUT
    - USB-C

### Main Board
- Contains the Daisy Seed
- Switches, rotary encoders, and potentiometers
- Display with microSD card
- Ports!
    - MIDI IN
    - AUDIO IN x2
    - AUDIO OUT x2
    - 3.5mm Headphone Jack
    - microUSB for programming the Daisy
    - USB-C for data

### PDB
- USB-C charging
- Battery management
- 6000 mAh Li-Po
- Boost to 5V
- Buck-Boost to 3V3

### Octave PCB
An octave of velocity-sensitive keys. Hall-effect sensors, processed into usable data for the Daisy Seed. 
- 12 Hall-Effect Keyswitches
- STM32 MCU Chip
- UART data transmission



### MIDI-Out PCB
- ESP32
- MIDI OUT
- USB-C


## CAD

## Firmware
Firmware coded with C++ and libraries libDaisy and daisySP. 

## BOM
### Main PCB
- 1x Electro-Smith Daisy Seed
- 2x EC11 Rotary Encoders
- 6x Cherry MX Keyswitches
- 9x Potentiometers
- 1x 3-pin Male Header JST-PH
- 1x 10-pin JST
- 1x 4-pin Male Header JST-PH
- 2x DIN-5 MIDI Jack
- 1x 3.5mm Headphone Jack
- 2x PJ-320 Jacks
- 1x Optocoupler
- 1x Speaker

### Octave PCB 
- 12x Gateron Jade Magnetic Switches
- 12x Linear Hall-Effect Sensors
- 1x STM32
- 12x 0.1uF Capacitors
- 1x 2-Pin Male Header JST-PH 
- 1x 4-Pin Male Header JST-PH
- 1x RS-485
- 1x 3-Bit DIP Switch

Three of these for this particular iteration!

### Power Distribution Board
- 1x USB-C Receptacle
- 3x 2-Pin Male Header JST-PH
- 1x 3-Pin Male Header JST-PH
- 
