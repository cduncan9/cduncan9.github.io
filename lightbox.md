# Light Box
| ![](https://github.com/cduncan9/cduncan9.github.io/blob/main/finalproduct.jpg?raw=true) |
|:------:|
| Final working light box|
## User Needs
This project was meant to serve as a final skills assessment for Medical Device Design I, the first class in a two semester design clourse taught by Dr. Mark Palmeri meant to introduce students to all of the aspects of the medical device industry. All of the skills learned throughout the class would be used to contruct a final design that met many user design needs. These needs were kept in mind throughout the enire design process and final product assembly. The user needs as specified in the rubric for this project are listed below:

* Switch to turn device on/off
* Rotary knob to linearly modulate the brightness of the light
* Switch to toggle from a continuous to a 2 Hz blinking mode (50% duty cycle)
* Use a 9V battery
* Battery must be easily replaceable
* Battery life of at least 4 hours
* Single-sided printed circuit board
* Weigh less than half a pound
* All dimensions must be less than 3 inches
* Enclosure must be sealed
* It must cost less than $20 to replicate the unit
* It must be able to survive a 3 ft drop test

## Design Process

### Mechanical

| ![](https://github.com/cduncan9/cduncan9.github.io/blob/main/exploded-view-onshape.jpg?raw=true) |
|:------:|
| Exploded view of light box assembly |

The enclosing of the light box was designed in Onshape. Throughout the entire design process, specific decisions were made to successfully meet all of the user needs. The light box enclosing was designed in three parts consisting of a top piece, bottom piece, and battery cover. This three piece design was meant to improve the ease of access to the internal components of the lightbox for quick battery replacement and electrical troubleshooting. When fully assembled, the body of the light box would have a width of 2.4 inches, a length of 3 inches and a height of 2.4 inches, leaving room for the switches to protrude from the top of the light box while still having dimensions under 3 inches in all directions. 

| ![](https://github.com/cduncan9/cduncan9.github.io/blob/main/top-piece-image.jpg?raw=true) |
|:------:|
| Top piece of the light box|

The top piece of this box was designed to have openings for the light and the switch hardware to protrude from. On the top face of the box there are three holes that are 0.3 inches in diameter. These holes enable the user to see the light from the LED and to control the settings of the light through the switch and potentiometer knob. 

The top piece also has 4 holes at the corners where M2 screws are inserted to screw together the top and bottom pieces.

On the bottom of the top piece there is a 0.1 inch inner ridge where extrusions of the bottom piece will fit to help align the pieces.

The mechanical drawing for the top piece can be found [here](https://github.com/cduncan9/cduncan9.github.io/blob/main/Top%20Piece%20Drawing%20(1).pdf).

| ![](https://github.com/cduncan9/cduncan9.github.io/blob/main/bottom-piece-image.jpg?raw=true) |
|:------:|
| Top side of the bottom piece |

The bottom piece of the light box is where most of the features for the user needs are kept. The bottom piece has features for the storage of the battery, mounting of the PCB, and connecting the bottom and top pieces together.

Around the rim of the lightbox are four 0.1 inch tall protrusions. These protrusions couple with the inside of the rim of the top piece to guide the pieces together during assembly. 

Inside of the top part of the bottom piece are 4 holes for the PCB to be mounted onto. There is enough clearence underneath the holes for the bottom side of the PCB to fit without touching the battery compartment. Space is left on the sides of the PCB for the battery wires.

| ![](https://github.com/cduncan9/cduncan9.github.io/blob/main/bottom.jpg?raw=true) |
|:------:|
| Battery compartment |

Within the bottom piece is a battery compartment. The rectangluar compartment is open to the bottom of the bottom piece and is capable of fitting a 9V battery and a head to attach to the battery. On the side of the battery compartment is a 0.4 in by 0.5 in opening so that wires can connect the battery to the PCB.

The mechanical drawing for the bottom piece can be found [here](https://github.com/cduncan9/cduncan9.github.io/blob/main/Bottom%20Piece%20Drawing%20final.pdf).

| ![](https://github.com/cduncan9/cduncan9.github.io/blob/main/battery-cover-image.jpg?raw=true) |
|:------:|
| Battery compartment cover |

The Battery cover was designed so that the battery compartment could be sealed shut while still easily accessible. The battery cover is attached to the light box through two M2 screws.

The mechanical drawing for the battery cover can be found [here](https://github.com/cduncan9/cduncan9.github.io/blob/main/Battery%20Cover%20Drawing%20(2).pdf).

The overall assembly for the light box was designed to be sturdy and ergonomic. A 0.3 inch fillet was applied to all edges of the lightbox to reduce the stress on the edges during the drop test. The lightbox also has a uniform wall thickness of 0.2 inches to frotect its internals during a fall. 

The mechanical drawing for the light box assembly can be found [here](https://github.com/cduncan9/cduncan9.github.io/blob/main/assembly-drawing.pdf).

### Electrical

For designing the electrical components of the lightbox, I used Autodesk EAGLE to first design a schematic that could meet the specified user needs. Then I tested the schematic by running a SPICE simulation and I finally created a printed circuit board that would fit within the bottom piece of my light box as described in the mechanical section above. 

The final circuit schematic is shown below: 

| ![](https://github.com/cduncan9/cduncan9.github.io/blob/main/circuit.jpg?raw=true) |
|:------:|
| Final circuit schematic |






## Assembly and Modifications

| ![](https://github.com/cduncan9/cduncan9.github.io/blob/main/bottom-piece-image.jpg?raw=true) | ![](https://github.com/cduncan9/cduncan9.github.io/blob/main/assembled%20bottom%20piece.jpg?raw=true) |
|:---:|:---:|

| ![](https://github.com/cduncan9/cduncan9.github.io/blob/main/assembly.jpg?raw=true) | ![](https://github.com/cduncan9/cduncan9.github.io/blob/main/assembled%20box%20image.jpg?raw=true) |
|:---:|:---:|

| ![](https://github.com/cduncan9/cduncan9.github.io/blob/main/batt.jpg?raw=true) | ![](https://github.com/cduncan9/cduncan9.github.io/blob/main/bottom-with-battery.jpg?raw=true) |
|:---:|:---:|

## Testing

#### Switch to turn device on/off
#### Rotary knob to linearly modulate the brightness of the light
#### Switch to toggle from a continuous to a 2 Hz blinking mode (50% duty cycle)

#### Use a 9V battery
#### Battery must be easily replaceable
#### Battery life of at least 4 hours
To calculate the run time of my circuit, I am going to divide the amphours of my battery by the current being drawn by the blinking and constant modes at the brightest and darkest levels of the potentiometer. For this test, I will be using a battery amphour of 

| Mode | Current Draw | Calculated Battery Life |
|------|------|------|
|Blinking with Brightest Light| 0.2 mA||
|Blinking with Darkest Light|0 mA (smaller than meter can detect)||
|Constant with Brightest Light|25 mA||
|Constant with Darkest Light|0.1 mA||
#### Weigh less than half a pound
The final weight of the box is 171.82 grams which is 0.38 lbs. I was able to make this box both light and sturdy by minimizing the size of the elecrical components. A smaller PCB and smaller switch reduced the size of the box, significantly reducing the weight.
#### All dimensions must be less than 3 inches

#### Enclosure must be sealed
#### It must cost less than $20 to replicate the unit

#### It must be able to survive a 3 ft drop test
This test is still to be performed by Dr. Palmeri.

## Future Improvements
