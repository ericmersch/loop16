For live performances, I built a custom DIY asynchrone loop station based on an Arduino and Raspberry Pi.

1. DIY USB MIDI interface

In the context of a performance, I want to avoid having complex interface on the table. I prefer a discrete and minimalist interface in order to let the audience understand my actions as much as I can.
I built this MIDI interface out of a wooden squared box, which I find esthetically consistent with the other objects that I use in performance.
I wanted to have a visual feedback of the looper, so I used a 4x4 RGB NeoTrellis pad: the color is green or blue when playing the loops and red or orange when recording, with a blink each time a loop starts.
All the code concerning the MIDI interface is included in the file Neotrellis_MIDI_ctrl.ino

2. Pure data loop station

This pure data patch is meant to be used with the DIY USB MIDI interface described before and a USB audio interface to record the sounds.
In order to minimise my setup during performance and avoid the presence of screens, I use this code within a Raspbeyy Pi 5 with 8 Gb memory, but it's also working fine with a laptop.
Each of the 16 buttons is assigned to a loop.
At first press of any button of the MIDI controller, a reconding starts.
At second press, the recording ends and the loop starts.
At third press, the loop is played for the last time untill the end and then stops.

The main code is contained in the abstraction 1loop.pd
This abstraction is duplicated 16 times in the code 16loops.pd and this code also makes the link with the audio interface and a small reverb is added.
The reverb uses the abstraction reverbA~.pd and setThreshold.pd

A maximum of 16 loops can be played at the same time. Each of these loops have its own duration. Therefore, I speak of asynchrone loops, which are less predictible then traditional loops.
