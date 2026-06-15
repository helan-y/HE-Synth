# journal #1: research, planning & starting on the schematic

this is going to be so long because this is planning for the whole project. this has been bouncing around my brain for a while so uh here. 

i want a compact synth! i am mildly broke and synths are expensive! i am fully willing to invest blood, sweat, and tears!

So much time off-camera spent on research and hunting down parts. This was a shockingly massive undertaking. I really should have learned signals & systems before doing this. Or maybe taken apart an existing synth. Or maybe tried something smaller. Oh well!

features (hopefully):
- - Velocity-sensitive!
- Two/three/more octaves!
- In-build audio! 3.5 mm headphone jack or speaker. 
- Different presets! Different sound envelopes!
- There's even a looper!
- And a display!

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
    - a display with microSD!
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

for this session, i worked on assembling the main schematic and arranging the PCB. 

took shockingly long. finding a display and figuring out the pins? the one specific JST connectors where the pins were just a little off on the schematic, making it basically impossible to connect nets or wires?? finding all the 3d models?? i'm glad the planning is finally over though. this has been such a long project. 

i need to finish adding the ports and figuring out if i need a mux for all the inputs, but most the parts are here!!

![image](/Journal%20Images/log_1.1.png)

# journal #2: octave PCB & research

so much research. my lord. 

so i'm planning for this synth to really be a modular midi keyboard + a daisy synthesizer. i should make one more PCB that's home to a microcontroller that processes the data from the octave PCBs and forwards it to the Main PCB (where the daisy is, or basically the synth). this way it's fully modular. if i want to swap out different midi keyboards or different synths i can quite easily. 

worked on the octave board! learned quite a lot about kicad and how to handle footprints and 3d models so hopefully my life should get easier later. found out i was editing specific footprints so the 3d models never saved :\( lesson learned !!

![image](/Journal%20Images/log_2.1.png))

have laid out the general schematic and pcb. i still need to figure out uart protocol and how to use the rs-485 to reduce interference. but that comes later

this was fairly simple ! at least this bit ! and i get a nice board to look at !

![image](/Journal%20Images/log_2.2.png)

![image](/Journal%20Images/log_2.2.png)

![image](/Journal%20Images/log_2.3.png)

# journal #3: octave PCB finished \(pain and suffering\) 

so this is unwireable. i either fix the schematic or swap the layout or this has to be a 4 layer board. four layer boards are so much more expensive.

i did not know that this would be the prelude to THREE HOURS of suffering. 

again engineering is the measure of how much you can tolerate small successive problems until you combust. 

## schematic

![image](/Journal%20Images/log_3.1.png)

this was mostly just staring at the datasheet and then the pcb to figure out which pins were available for which function, then which pin i COULD use that wouldn't ruin my life for wiring. this sounds so simple but it probably ate an hour just trying to figure out which configurations would work. thankfully i'm a bit more familiar with STM32 now, so future projects should go a little smoother.

## PCB

![image](/Journal%20Images/log_3.2.png)
![image](/Journal%20Images/log_3.3.png)

wiring this was genuinely a nightmare. one layer is reserved for the GND plane for better signal processing, so no using two layers or vias to wire. i had to shuffle around so many of the keys just to be able to wire them to the correct adc pins. plus they can't interfere with the uart OR the power OR the firmware flashing port. had to move around so many part for this to function.

## PSB render

![image](/Journal%20Images/log_3.4.png)
![image](/Journal%20Images/log_3.5.png)

I'M FREEEEE