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

Once this was done I began the process of soldering my parts to the PCB. I had to make several fixes in the process of soldering my board. I had planned on using a 2.35 uFarad capacitor in my design but there were none of those in lab. Instead I ended up using a 2.2 uFarad capacitor. When one of the lines of copper came up I had to solder on a wire so that the current line was not cut. A picture of this fix is shown below:

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

It is important to note here that I was unable to perform some of the tests that I devised due to problems with timing and getting into lab. Nevertheless I do have some videos which are meant to represent the light box's functionality where I was unable to perform the test.

#### Switch to turn device on/off `Passed`

For this user need I created marginal and ideal values for the current flow out of the battery when the curcuit is switched on and off. These values can be seen in the table below:

|  | Marginal | Ideal |
|:------:|:------:|:------:|
| On |0 mA < current < 25 mA|current > 25 mA|
| Off |0 mA < current < 1 mA|0 mA|

I hoped to be able to test these values using a multimeter but was unable to. Instead I am forces to go off of a visual test, and by switching the circuit on and off I can confirm that this test passes.

#### Rotary knob to linearly modulate the brightness of the light `Passed`

For this user need I devised a test that would involve comparing the brightness of the LED in three different modes of the potentiometer. I planned on building a test circuit that used a phototransistor. I would then compare the output of this circuit when the potentiometer was at a low, medium, and high setting. For the marginal and ideal values of the low, medium, and high brightnesses I created the following table:

||Low|Medium|High|
|:------:|:------:|:------:|:------|
|Marginal| low| 1.5 * low |2 * low| 
|Ideal| low| 2 * low | 3 * low |

I would compare both the current and the voltage output of the phototransistor circuit, plot the values, and check if it increases linearly. I was unfortunately unable to do this so I had to test this user need with a visual eye test which can be seen in the video linked [here](https://youtu.be/Kl5_oRVEmec). As you can see, the brightness of the LED increases linearly with the turning of the potentiometer. 

#### Switch to toggle from a continuous to a linking mode `Passed`

For this user need I placed a switch at the beginning of the circuit that would direct the current either to the 555 timer or to a direct path to the potentiometer. A video of this working can be seen [here](https://youtu.be/Bkre8Up9MX0).

#### Two Hz blinking mode with 50% duty cycle `Failed`

As I discussed above, the frequency of my blinking light is wrong. When breadboarding my circuit I mixed up the capacitor and resistor values I changed the capacitance for C1 to be 2.35 uFarads. This was not a capacitance in the lab so I used a capacitance of 2.2 uFarads. bacause of this, I got a frequency of 1.33 Hz, which I found by filming a slow motion video which can be seen [here](https://youtu.be/kksQaKh8hng). 

The math to check to see if this checks out theoretically is shown below:

![](https://github.com/cduncan9/cduncan9.github.io/blob/main/mathcalc.jpg?raw=true)

From this you can see that the frequency still passes the marginal value but fails the ideal value.

#### Use a 9V battery `Passed`

The light box uses a 9V battery that is contained within the battery compartment and is sealed with the battery compartment cover. A battery header is used to connect the 9V battery to the circuit.

#### Battery must be easily replaceable `Passed`

For this test I devised the marginal and ideal replacement times of 3 minutes and 2 minutes respectively. I was able to replace the battery in under 90 seconds which is well under the ideal time. The ease in replacement comes from the fact that you only have to remove the two screws of the battery compartment cover to replace the battery.

#### Battery life of at least 4 hours 
To calculate the run time of my circuit, I am going to divide the amphours of my battery by the current being drawn by LED in the blinking and constant modes at the brightest and darkest levels of the potentiometer. For this test, I will be using a battery amphour of [311 mAh](https://rightbattery.com/279-9v-duracell-alkaline-battery-tests/).

| Mode | Current Draw of the LED | Calculated Battery Life |
|:------:|:------:|:------:|
|Blinking with Brightest Light| 0.2 mA|1555|
|Blinking with Darkest Light|0 mA (smaller than meter can detect)|x|
|Constant with Brightest Light|25 mA|12.44|
|Constant with Darkest Light|0.1 mA|3110|

From my calculations I found that the min battery life was 12.44 hours, far more than 4 hours, and therefore passing the ideal battery run time.

Note: I realized after performing the test that I should have measured the current coming out of the battery rather than the current going into the LED for my calculations. There are several 'current sinks' in the 555 timer circuit that arent represented by this calculation such as the voltage regulator, 555 timer, and transistor, which are all sources of current drain. However, I still believe that the run time would be greater than 4 hours if I used the current coming out of the battery.

#### Weigh less than half a pound `Passed`

For this user need I set the marginal weight to be 0.5 lbs and the ideal weight to be less than 0.4 lbs. The final weight of the box is 171.82 grams which is 0.38 lbs. I was able to make this box both light and sturdy by minimizing the size of the elecrical components. A smaller PCB and smaller switch reduced the size of the box, significantly reducing the weight.

#### All dimensions must be less than 3 inches `Passed`

|Length|Width|Height|
|:------:|:------:|:------:|
|![](https://github.com/cduncan9/cduncan9.github.io/blob/main/length.jpg?raw=true)|![](https://github.com/cduncan9/cduncan9.github.io/blob/main/width.jpg?raw=true)|![](https://github.com/cduncan9/cduncan9.github.io/blob/main/height.jpg?raw=true)|
|About 2.25 inches|About 3 inches|About 2.8 inches|
|Passes ideal value| Passes marginal value|Passes marginal value|


#### Enclosure must be sealed `Passed`

For this user need I said that a gap less than 1 mm would be ideal and a gap less than 3 mm would be marginally good.

The battery cover is fully sealed to the bottom piece of the box: 

![](https://github.com/cduncan9/cduncan9.github.io/blob/main/IMG_9591.jpg?raw=true)

The heated inserts for top piece bottom piece connection however stick out slightly and the top and bottom piece are not completely sealed:

![](https://github.com/cduncan9/cduncan9.github.io/blob/main/height.jpg?raw=true)

As seen from the image above, the gap between the top and bottom pieces is around 3/32 inches or 2.38 mm. This means that the box passes the marginal values for being sealed but not the ideal values.

#### It must cost less than $20 to replicate the unit `Passed`

For this test, I said that it would be ideal for the replication of the box to be less than $15 and the marginal cost would be $20. For this test I used the following costs that I found online:

|Part|Cost|Count|
|:------:|:------:|:------:|
|[Mini Toggle Switch](https://www.allelectronics.com/item/mts-4/spdt-on-on-mini-toggle-switch/1.html)| $1.25| 1 |
|[Potentiometer](https://www.adafruit.com/product/3393)| $1.75| 1 |
|[555 Timer](https://www.amazon.com/MCIGICM-ne555-Timer-Pulse-Generator/dp/B077BRB6W6/ref=sr_1_3?dchild=1&keywords=555+Timer+IC&qid=1604446628&sr=8-3)|$0.14|1|
|[LED](https://www.sparkfun.com/products/9594)|$0.35|1|
|[Transistor](https://www.amazon.com/CHANZON-100pcs-2N7000-Transistor-Channel/dp/B083TF4K6L/ref=sr_1_1_sspa?_encoding=UTF8&c=ts&dchild=1&keywords=Industrial+Electrical+Transistors&qid=1604449012&s=industrial&sr=1-1-spons&ts_id=306910011&psc=1&spLa=ZW5jcnlwdGVkUXVhbGlmaWVyPUFFNUJSVTRCRDNENTImZW5jcnlwdGVkSWQ9QTAwNzA3Mzg2WDBFUjY5RlcwOFkmZW5jcnlwdGVkQWRJZD1BMDcwODIzMUhSRE9KMzFHUjYzTiZ3aWRnZXROYW1lPXNwX2F0ZiZhY3Rpb249Y2xpY2tSZWRpcmVjdCZkb05vdExvZ0NsaWNrPXRydWU=)|$0.06|1|
|[Voltage regulator](https://www.mouser.com/ProductDetail/STMicroelectronics/LM217T?qs=DUDHuK3gDFQoaHjO14gt9A%3D%3D)|$0.77|1|
|[1 uF Capacitor](https://www.amazon.com/Pcs-MCIGICM-electrolytic-Capacitor-4%C3%977mm/dp/B07VHKWVBQ/ref=sr_1_3?dchild=1&keywords=1uF+Capacitor&qid=1604449522&sr=8-3)|$0.08|2|
|[0.01 uF Capacitor](https://www.amazon.com/Ceramic-Disk-Capacitor-10nf-0-01uF/dp/B00U5X7YZQ)|$0.18|1|
|[2.2 uF Capacitor](https://www.mouser.com/ProductDetail/AVX/08055C225KAT2A?qs=F5vmRhUsTTrD4i7cuGJbzw%3D%3D)|$1.61|1|
|[1 k Resistor](https://www.amazon.com/EDGELEC-Resistor-Tolerance-Multiple-Resistance/dp/B07QG1V4YL/ref=sr_1_1_sspa?dchild=1&keywords=1k+ohm+resistor&qid=1604449976&sr=8-1-spons&psc=1&spLa=ZW5jcnlwdGVkUXVhbGlmaWVyPUE5TzczSDVYU1JQTFomZW5jcnlwdGVkSWQ9QTA0NTcyNjUzOUEyTzE2OEEyNE1WJmVuY3J5cHRlZEFkSWQ9QTA1NDIxNTgxQkoyTU4xSFVHWjczJndpZGdldE5hbWU9c3BfYXRmJmFjdGlvbj1jbGlja1JlZGlyZWN0JmRvTm90TG9nQ2xpY2s9dHJ1ZQ==)|$0.06|3|
|[10 k Resistor](https://www.amazon.com/Projects-100EP51210K0-10k-Resistors-Pack/dp/B0185FIOTA)|$0.06|1|
|[301 k Resistor](https://vetco.net/products/301k-ohm-1-4-watt-1-metal-film-resistor)|$0.49|1|
|[M2 Screws](https://www.mcmaster.com/screws/thread-size~m2/metric-stainless-steel-pan-head-torx-screws/)|$0.05|10|
|[Heated Screw Inserts](https://www.amazon.com/Products-Insert-Length-Press-Injection/dp/B07HKSP7H1/ref=sr_1_25?dchild=1&qid=1604452005&refinements=p_n_material_browse%3A17548933011&s=industrial&sr=1-25)|$0.08|10|

From this, the parts used in the assembly of my box cost $8.30. I could not find the cost of the single sided PCB or the cost of printing the box, but I can safely assume that it is under $11.70. Therefore it passes this test. 



#### It must be able to survive a 3 ft drop test `TBD`
This test is still to be performed by Dr. Palmeri. However, I designed this box to have 0.3 inch fillets at the edges and a thickness of 0.2 inches so it should be protected in a drop.

## Future Improvements

#### Easy Improvements
There are three quick and easy changes that I discovered during the assembly process of my box:
1) Use a 1.2 uF capacitor for C1 for the 555 timer instead of a 2.2 uF capacitor. This could theoretically give the blinking mode a frequency of 2 Hz instead of 1 Hz.
2) Remove the test pads from the PCB. This would significantly remove the complexity of the PCB and also decrease the size of the PCB. The test pads also aren't necessary, I was able to debug the circuit without them.
3) Remove the 1k resistor in the constant LED path. This isn't necessary.

#### Making the continuous and blinking brightness the "same"

Several ways to make the brightness of the LED similar in the continuous and blinking mode:

1) Increase the resistance in the continuous mode. Thiw would introduce a voltage drop that could lower the brightness of the LED.
2) Introduce [pulse wave modulation](https://www.ti.com/lit/an/snva768/snva768.pdf?ts=1604381361738) in the continuous mode. If you introduce PWM (possibly with another 555 timer) and choose a frequency that is too fast for the human eye to detect, the LED will appear dimmer as it will be on for a smaller amount of time.

To test these two ways of dimming the continuous mode I would build a phototransistor circuit and compare the outputs of the circuit for both the continuous and blinking mode.
