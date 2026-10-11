# Making a Starbie!
A compilation of all the files for the Starbie PCB project on Half Life!

## Summary
Starbie is a custom-designed PCB for a portable, interactive pet keychain (inspired by Tamagotchi), including a pet that reacts to different actions by the user (shaking, pressing buttons, etc.) and the environment (temperature).

The PCB was designed with **KiCad** and the code was made with **Arduino**. I initially made it only because it was the beginner project for Half Life, but I've also always been a fan of these kinds of toys. It's not only relatively easy to make, but also teaches most of the fundamentals of PCB building, such as footprints, Silkscreen, and basic Arduino code. I'm more of a creative than technical person, but I feel that this is the perfect beginner project that enhances both. I was already interested in exploring electronics, and, using some of my own skills and interests, I think my Starbie turned out great. 

Here is a list of what each file does:
|File|What's Inside?|
|---|---|
|starbie_pcb.kicad_pcb|contains the PCB layout, including the routing, footprints, and edge cuts
|starbie_pcb.kicad_pro|contains the project settings and configuration
|starbie_pcb.kicad_sch|contains the schematic and connections
|Starbie.ino|contains the code used to run the micrcontroller
|starbie_pcb_gerbers.zip|contains several gerber files
|bom.csv|bill of materials

## Schematic
The first step of creating Starbie was creating the schematic in KiCad's PCB Schematic editor. To see the schematic, open up the kicad_sch file. In the schematic, there'll be some main parts:
* XIAO-ESP32-C3-SMD: The microcontroller of the project, interpreting and executing the code
* DHT11: A sensor for temperature and humidity for interactions with the pet
* R1 10k: A 10k Ohm resistor for the DHT11
* Conn_01x08_Pin and Conn_01x04_Pin: A connector pin that links each pin to its matching circuit trace
* SW_Push: A switch/button that will control actions for the pet

The way they are connected is either through wires or through net labels (which connect parts without having to draw long wires). 

<img width="388" height="419" alt="image" src="https://github.com/user-attachments/assets/504e8148-447d-47d0-afa7-975daf2d96a8" />

## Routing & Customization
After that, take a look at the routing by opening up the kicad_pcb file.

The red lines represent the copper traces on the front of the board, while the blue lines represent the copper traces on the black of the board. These copper lines allow the microcontroller to transmit and receive data to interpret, which will then be used for the pet. Furthermore, the red overlay on top of the PCB is the GND pour. Another thing you'll notice is the customization of the PCB, including the text, images, and shape of the PCB. The shape was made using the Edge Cuts layer. To edit it, draw your own lines or move the existing vertices. Just note that you'll have to edit the GND pour as well and refill it by pressing B. To add images, use the image converter to turn the image into a bitmap, then into a footprint, and add it on as a footprint by pressing A. KiCad has a built-in text function, so you can use that as well. Also, make sure to put the layer for both images and text as F.Silkscreen!

For my images, I uploaded a sprite of Jolteon, an apple core, and some sparkles using the method above. Just make sure that, if you are using a sprite for a game, find a scaled-up version rather than the original sprites. I also added a keychain hole as a mounting hole. KiCad will scale-up the sprite into a blurry mess that looks nothing like the original sprite. I used Wingdings for my font because it looks more interesting than just a basic readable font.

<img width="479" height="433" alt="image" src="https://github.com/user-attachments/assets/dddfa2d5-8472-44e5-b999-9d2271f5fd2d" />

KiCad also has a 3D viewer so you can see what your PCB will probably eventually look like!

<img width="431" height="393" alt="image" src="https://github.com/user-attachments/assets/f63e5f11-6177-4ac2-9410-b27e193c56ed" />

## Customizing Firmware
After making the PCB, move on to the firmware in Arduino. The code was very easy to customize, so here's the things I did to change it up and make it my own. (to change it yourself, find the specific functions)

The pet comes with basic hearts, so I decided to replace it with a lightning bolt instead. I first drew it in Piskel (or use whatever sprite art app you have), and then just wrote the code to draw it by hand. The drawPixel function works as if you were drawing pixels relative to a certain point. So, if you wanted to draw a pixel 1 pixel left of the "anchor point", you would use x - 1. 

<img width="314" height="257" alt="image" src="https://github.com/user-attachments/assets/573171f2-9c7c-4cee-8c45-5d057ebec59f" /> <img width="7" height="7" alt="New Piskel-1 png (1)" src="https://github.com/user-attachments/assets/f9c4f528-b833-4160-8375-0013c75f8aa7" />

I also used the same logic to write some code for the sparkle trail, which I just replaced with a slightly bigger sparkle that I liked better.

<img width="240" height="185" alt="image" src="https://github.com/user-attachments/assets/c2a79023-34e3-496c-8fce-7debf09bc09b" />

The biggest part was designing the pet sprite, which I have as a Jolteon. Simply draw your creature in a 32x32 size, and upload it to an image2cpp converter. I find it best to draw your own sprite. Though Jolteon already exists and there are sprites of it, it's way more personal making your own! 

the sprite I made -> <img width="48" height="48" alt="image" src="https://github.com/user-attachments/assets/53e2f84c-0a87-4b8c-941b-834d473e91e5" />

## Bill of Materials
After completely designing the PCB and finishing your code, start planning for when you actually build your PCB by ordering the parts! I created a Bill of Materials, which lists the specific names, quantities, and prices for the parts of the PCB. Use the StarbieGerberArchive.zip when manufacturing the PCB. It is both below and in the bom.csv. 








