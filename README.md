# HE Synth

## About
A custom, compact velocity-sensitive digital synthesizer, made with Hall-Effect keyswitches and DaisySeed. I want to make music and I do not have money but I do have blood, sweat, and many, many tears. This is also a proof of concept towards bigger projects I want to make in the future!
- synth with trackballs for keys! like a roli seaboard but weird and isomorphic! what if piano could vibrato!!
- bigger modular midi (repeating pcb boards in series one for each octave) keyboard with keycaps like piano keys!
- sampler! vocoder! etc!

## Features
- Velocity-sensitive!
- Two octaves!
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
- I first thought about using analog multiplexers 

## PCB

## CAD

## Firmware

## BOM