# HE Synth

## About
A custom, compact velocity-sensitive digital synthesizer, made with Hall-Effect keyswitches and DaisySeed. I want to make music and I do not have money but I do have blood, sweat, and many, many tears. This is also a proof of concept towards bigger projects I want to make in the future!
- synth with trackballs for keys! like a roli seaboard but weird and isomorphic! what if piano could vibrato!!
- bigger modular midi (repeating pcb boards in series one for each octave) keyboard with keycaps like piano keys!
- sampler! vocoder! etc!

## Features
- Velocity-sensitive!
- Two/three/more octaves!
- In-build audio! 3.5 mm headphone jack or speaker. 
- Different presets! Different sound envelopes!
- There's even a looper!
- And a display!

## Schematic
So much time off-camera spent on research and hunting down parts. This was a shockingly massive undertaking. I really should have learned signals & systems before doing this. Or maybe taken apart an existing synth. Or maybe tried something smaller. Oh well!

Five main problems for the schematic:
- Not enough pins. 24 hall-effect keys all need ADC (analog to digital) pins. 6 rotary encoders. A display. Some pins also have specialized functions, so not all pins are interchangeable. 
- Different demands on power supply. Linear hall-effect sensors run on 3V3. Sound systems generally run on 5V. LiPo Batteries supply 3.7V - 4.2V. The daisy seed can supply 3V3 but I don't think it has enough to power all the systems that need it, and it definitely doesn't have 5V. 
- Enough power?? This might take a lot of power? 
- Hall-effect switches. Getting all of the specifications and all that jazz. Never worked with them before! Should be fun!
- Signal integrity & latency. This is probably my biggest concern. I don't care that much about polling rate, but I do need the synth to not have noticable lag. The solutions to "not enough pins" also tends to collide with this problem. And I need the data from the keys to be coherent by the time the daisy seed processes it. 

Tentative solutions:
- I first thought about using analog multiplexers, but those scan too slowly, and that would require the Daisy to process all Hall-Effect inputs, both which would probably introduce lag to the keyboard. 
- Second solution --> make it modular. This was a much better idea. 
    1. It's going to save a bit in cost! the main pcb board is probably going to be 4 layers just because I don't want to deal with muddled signals, but the keyboard PCBs don't have to be! You also have to order at least 5 PCBs in one batch so that works well with this.
    2. It's modular! You can add more octaves to the synth without having to rehaul the entire thing or design a new PCB!
    3. Saves on processing time! Probably reduces latency! Each octave board has an onboard MCU chip that processes sensor information and returns velocity. 
    4. Cleaner signals!

So the PCB design is going to be divided into three parts:
1. Main Board
    - Contains the Daisy Seed!
    - switches, rotary encoders, and potentiometers!
    - display with microSD!
    - ports!
        - MIDI IN
        - MIDI OUT
        - AUDIO IN
        - AUDIO OUT
        - 3.5mm Headphone Jack
        - microUSB for programming the Daisy
2. Power Distribution Board (PDB)
    - USB-C charging
    - Battery management
    - Boost to 5V
    - Buck-Boost to 3V3
3. Octave PCBs
    - 12 Hall-Effect Keyswitches
    - STM32 MCU Chip
    - UART connected in series


## PCB

## CAD

## Firmware

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
- 1x Optocoupler
- 1x Speaker

### Octave PCB 
- 12x Gateron Jade Magnetic Switches
- 12x Linear Hall-Effect Sensors
- 1x STM32
- x Capacitors
- 

### Power Distribution Board
- 1x USB Receptacle
- 


Three of these for this particular iteration!