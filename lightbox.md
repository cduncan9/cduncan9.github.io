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

In order to meet all of these user requirements, I created a spreadsheet to keep track of the marginal and ideal specifications that I would follow in the design process. The spreadsheet can be downloaded [here](https://github.com/cduncan9/cduncan9.github.io/blob/main/MedicalDeviceDevelopmentDuncan.xlsx).

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

For designing the electrical components of the lightbox, I used Autodesk EAGLE to first design a schematic that could meet the specified user needs. Then I tested the schematic by running a SPICE simulation and then by breadboarding the circuit. Finally I created a printed circuit board that would fit within the bottom piece of my light box as described in the mechanical section above. 

The final circuit schematic is shown below: 

| ![](https://github.com/cduncan9/cduncan9.github.io/blob/main/circuit.jpg?raw=true) |
|:------:|
| Final circuit schematic |

This circuit has two settings, a continuous mode and a 2 Hz blinking mode with a 50% duty cycle. The mode of the LED is dictated by a switch at the very beginning of the circuit. When the circuit is in continuous mode the current travels directly to the potentiometer. When the circuit is in blinking mode it travels to a 555 timer which controls the blinking. The values of R1, R2 and C1 for the 555 timer were calculated to be 1 kOhm, 301 kOhm, and 1.2 uFarads respectively. The math to check the values is shown below:

![](https://github.com/cduncan9/cduncan9.github.io/blob/main/theoreticalcalcs.jpg?raw=true)

The output of the 555 timer then goes through a transistor to amplify the current produced by the timer before it reaches the potentiometer.

The potentiometer used in my circuit design has two purposes. Two pins on the potentiometer can be used to switch the circuit on/off by breaking the connection when the potentiometer knob is turned off. The potentiometer is also used to linearly modulate the brightness of the LED. the output of the 555 timer/continuous mode is connected to one pin of the potentiometer, and another pin of the potentiometer is then connected to a resistor which is then connected to the LED. When the potentiometer knob is turned, the resistor value within the potentiometer changes, and a larger resistance will lead to a dimmer light.

There are two capacitors in the circuit, one after the battery and one after the voltage regulator, which are meant to prevent the negative effects of fluctuations from the power source. There are also 5 test pins in the circuit which are meant to ease the debugging of the PCB if problems happen during assembly.

After designing the circuit, I ran a SPICE simulation on the 555 timer to check to see if the frequency and duty cycle of the timer were correct. I had to simplify the circuit to get the SPICE simulator working, so I used the following 555 timer circuit:

![](https://github.com/cduncan9/cduncan9.github.io/blob/main/spice-circuit.jpg?raw=true)

This circuit produced the following SPICE simulation:

![](https://github.com/cduncan9/cduncan9.github.io/blob/main/SPICE.jpg?raw=true)

As seen above, the rising and falling periods of the output are both around 0.25s each, producing a 50% duty cycle and a frequency of 2 Hz.

After running the SPICE simpulation, I wired the circuit on a breadboard so that I could physically test the circuit. When making the breadboard, I found that the frequency of the 555 timer was too slow. Because of this, I ended up changing the value of the capacitor to 2.35 uFarads. Later in this report I will talk about how that was actually the wrong decision and that I should have stuck with a capacitance of 1.2 uFarads as the Frequency of the final light box is too slow and it fails the 2 Hz test. I believe that I got the wrong result while breadboarding the circuit by misreading the capacitor or resistor values. The breadboarded circuit is shown below:

![](https://github.com/cduncan9/cduncan9.github.io/blob/main/breadboard.jpg?raw=true)

Once the circuit was completed I created a single-sided PCB layout in EAGLE. The final layout is shown below:

![](https://github.com/cduncan9/cduncan9.github.io/blob/main/final-pcb.jpg?raw=true)

The final dimensions of the PCB are 2.4 inches by 1.6 inches. The holes of the PCB are large enough for M2 screws, and were placed to align with the holes of the PCB mount in the bottom piece of the light box. 

Adding the test pins introduced a lot of air wires to the PCB and it was difficult to connect them all with a single sided PCB. I was able to connect all but one of the air wires without havaing to use vias, the one air wire that I connected with several vias I ended up not soldering which I will discuss later in the assembly section.

## Assembly and Modifications

Once I had tested my circuit with a SPICE simulation and by breadboarding it, I printed a single sided PCB so that I could begin to sauter the board. In designing the circuit, I left 5 test pins that would help with debugging the circuit. These test pins when printed however were too large and overlapped, so I had to cut the traces to the test pins as shown below: 

![](https://github.com/cduncan9/cduncan9.github.io/blob/main/MicrosoftTeams-image.png?raw=true)

Once this was done I began the process of soldering my parts to the PCB. I had to make several fixes in the process of soldering my board. When one of the lines of copper came up I had to solder on a wire so that the current line was not cut. A picture of this fix is shown below:

![](https://github.com/cduncan9/cduncan9.github.io/blob/main/IMG_9584.jpg?raw=true)

I also ened up replacing the 1kOhm resistor that is connected in series in the continuous mode with a wire as the resistor was unnecessary. As seen in the image above, I also made the mistake of not using a mirror image of the 555 timer for my board. Because of this I had to solder the 555 timer on the same side of the copper lines.

After soldering the board I moved onto printing the lightbox enclosure. To print the enclosure I used soluble supports, so I had to soak the prints overnight in a water bath to clear the supports.

For the holes for the PCB and the connection to the top piece I added threaded heat inserts so that the screws could be rescrewed without worrying about messing up the plastic of the box. To be able to add the heat inserts, I had to make the holes larger, which I did with a power drill. I added the heated inserts using a soldering iron. Below you can see a comparison of the 3D CAD design of the bottom piece with the final physical model.


| ![](https://github.com/cduncan9/cduncan9.github.io/blob/main/bottom-piece-image.jpg?raw=true) | ![](https://github.com/cduncan9/cduncan9.github.io/blob/main/assembled%20bottom%20piece.jpg?raw=true) |
|:------:|:------:|
| 3D CAD Design | Final Model |

Once I had the heated inserts set in the bottom piece of the enclosure I began the assembly of the PCB in the lightbox. When screwing in the PCB, I found that the heated inserts must have changed the alighnment of the holes, and I was only able to screw in two of the PCB holes. During the process of mounting the PCB some of the wires connected to the LED and the potentiometer came loose. To fix this problem from happening again I soldered female header pins to the board so that now the wires connected to the potentiometer and the LED are detachable. 

![](https://github.com/cduncan9/cduncan9.github.io/blob/main/IMG_9587.jpg?raw=true)

I then put the LED and switches through the holes in the top piece of the light box. For the LED I used a rubber sleve to seal the hole and for the toggle switch I used a nut to secure the switch to the top piece. With a small amount of force I closed the light box and screwed in the M2 screws.

| ![](https://github.com/cduncan9/cduncan9.github.io/blob/main/assembly.jpg?raw=true) | ![](https://github.com/cduncan9/cduncan9.github.io/blob/main/assembled%20box%20image.jpg?raw=true) |
|:------:|:------:|
| 3D CAD Design | Final Model |

The 9V battery that powers the light box snugly fits inside the battery compartment.

| ![](https://github.com/cduncan9/cduncan9.github.io/blob/main/batt.jpg?raw=true) | ![](https://github.com/cduncan9/cduncan9.github.io/blob/main/bottom-with-battery.jpg?raw=true) |
|:------:|:------:|
| 3D CAD Design | Final Model |

## Testing 

#### Switch to turn device on/off
#### Rotary knob to linearly modulate the brightness of the light
#### Switch to toggle from a continuous to a 2 Hz blinking mode (50% duty cycle)

#### Use a 9V battery
#### Battery must be easily replaceable
#### Battery life of at least 4 hours
To calculate the run time of my circuit, I am going to divide the amphours of my battery by the current being drawn by the blinking and constant modes at the brightest and darkest levels of the potentiometer. For this test, I will be using a battery amphour of 

| Mode | Current Draw | Calculated Battery Life |
|:------:|:------:|:------:|
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
