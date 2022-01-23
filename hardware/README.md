# Development Features
Since this was the first hardware spin of this board, some
development features were included.

## Software Switching
The software switching controlled through the CP210N GPIO control
the enable lines of two high-side power switches (```U7```/```U8```).
Only one of these switches should be enabled at a time, therefore the 
complementary output of ```U10``` is used. I had concerns that there
wouldn't be enough 'downtime' during the switch event to allow the 
on-board micro-sd card to fully powerdown before switching. 

The ```U10``` mux can be bypassed by using a GPIO.1 on the CP201N as 
the complementary switching singal. 
- Remove ```R12``` and ```R23```
- Install ```R11``` and ```R22```

## DUT Connection via FFC
A Flex-Flex Cable (FFC) header (```J3```) is provided to allow connections
to the DUT via a flex cable. The other end of the cable is connected to a
micro-sd breakout board, which is provided in this repo 
[here](/microsd-breakout).

# Known Issues
- Silkscreen labels on ```S1``` and ``SW2``` are reversed.
- On-board micro-sd card in ```J4``` protrudes over the board edge
and may interfer with the DUT.
