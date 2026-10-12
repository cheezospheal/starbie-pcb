# Starbie
A custom-designed PCB for a portable, interactive pet keychain that reacts to different user actions and the environment.

I initially made it only because it was the beginner project for Half Life, but I've also always been a fan of these kinds of toys. It's not only relatively easy to make, but also teaches most of the fundamentals of PCB building, such as footprints, Silkscreen, and basic Arduino code. I'm more of a creative than technical person, but I felt that this was the perfect beginner project that enhanced both. I was already interested in exploring electronics, and, using some of my own skills and interests, I think my Starbie turned out great! :)

<img width="367" height="368" alt="image" src="https://github.com/user-attachments/assets/2c28185d-339a-410e-9c0d-e5838adbfbd9" />

## Summary
The PCB was designed with **KiCad** and the code was made with **Arduino**. To open the PCB yourself, install both KiCad and Arduino, then import the respective files (see below).

|File|What's Inside?|
|---|---|
|starbie_pcb.kicad_pcb|contains the PCB layout, including the routing, footprints, and edge cuts
|starbie_pcb.kicad_pro|contains the project settings and configuration
|starbie_pcb.kicad_sch|contains the schematic and connections
|Starbie.ino|contains the code used to run the micrcontroller
|starbie_pcb_gerbers.zip|contains several gerber files
|bom.csv|bill of materials

## Features
* An OLED screen that displays a small Jolteon that you can interact with
* Pet actions, including sleeping, playing, petting, and jumping
* Button controls that allow the user to trigger animations
* Custom PCB shape of a star
* Customizable interactions in the Arduino code

## Schematic
To see the schematic, open up the kicad_sch file. In the schematic, there'll be some main parts:
* XIAO-ESP32-C3-SMD: The microcontroller of the project, interpreting and executing the code
* DHT11: A sensor for temperature and humidity for interactions with the pet
* R1 10k: A 10k Ohm resistor for the DHT11
* Conn_01x08_Pin and Conn_01x04_Pin: A connector pin that links each pin to its matching circuit trace
* SW_Push: A switch/button that will control actions for the pet

The way they are connected is either through wires or through net labels (which connect parts without having to draw long wires). 

<img width="319" height="355" alt="image" src="https://github.com/user-attachments/assets/b81eed3a-ebad-4eee-8d0b-804f3ee9d2fc" />


## Routing & Customization
After that, take a look at the routing by opening up the kicad_pcb file.

The red lines represent the copper traces on the front of the board, while the blue lines represent the copper traces on the black of the board. These copper lines allow the microcontroller to transmit and receive data to interpret, which will then be used for the pet. Furthermore, the red overlay on top of the PCB is the GND pour. Another thing you'll notice is the customization of the PCB, including the text, images, and shape of the PCB. The shape was made using the Edge Cuts layer. To edit it, draw your own lines or move the existing vertices. Just note that you'll have to edit the GND pour as well and refill it by pressing B. I also added an extra switch, which you can see in the bottom right corner of the star. To add images, use the image converter to turn the image into a bitmap, then into a footprint, and add it on as a footprint by pressing A. KiCad has a built-in text function, so you can use that as well. Also, make sure to put the layer for both images and text as F.Silkscreen!

For my images, I uploaded a sprite of Jolteon, an apple core, and some sparkles using the method above. Just make sure that, if you are using a sprite for a game, find a scaled-up version rather than the original sprites. I also added a keychain hole as a mounting hole. KiCad will scale-up the sprite into a blurry mess that looks nothing like the original sprite. I used Wingdings for my font because it looks more interesting than just a basic readable font. 

<img width="472" height="425" alt="image" src="https://github.com/user-attachments/assets/f41999bb-8fcc-43a1-8371-c7b77d358d65" />

KiCad also has a 3D viewer so you can see what your PCB will probably eventually look like!

## Customizing Firmware
After making the PCB, move on to the firmware in Arduino. The code was very easy to customize, so here's the things I did to change it up and make it my own. (to change it yourself, find the specific functions)

The pet comes with basic hearts, so I decided to replace it with a lightning bolt instead. I first drew it in Piskel (or use whatever sprite art app you have), and then just wrote the code to draw it by hand. The drawPixel function works as if you were drawing pixels relative to a certain point. So, if you wanted to draw a pixel 1 pixel left of the "anchor point", you would use x - 1. 

<img width="314" height="257" alt="image" src="https://github.com/user-attachments/assets/573171f2-9c7c-4cee-8c45-5d057ebec59f" /> <img width="7" height="7" alt="New Piskel-1 png (1)" src="https://github.com/user-attachments/assets/f9c4f528-b833-4160-8375-0013c75f8aa7" />

I also used the same logic to write some code for the sparkle trail, which I just replaced with a slightly bigger sparkle that I liked better.

<img width="240" height="185" alt="image" src="https://github.com/user-attachments/assets/c2a79023-34e3-496c-8fce-7debf09bc09b" />

The biggest part was designing the pet sprite, which I have as a Jolteon. Simply draw your creature in a 32x32 size, and upload it to an image2cpp converter. I find it best to draw your own sprite. Though Jolteon already exists and there are sprites of it, it's way more personal making your own! 

the sprite I made -> <img width="48" height="48" alt="image" src="https://github.com/user-attachments/assets/53e2f84c-0a87-4b8c-941b-834d473e91e5" />

## Bill of Materials
After completely designing the PCB and finishing your code, start planning for when you actually build your PCB by ordering the parts! I created a Bill of Materials (BOM), which lists the specific names, quantities, and prices for the parts of the PCB. Use the collection of gerber files, starbiepcb_gerbers.zip, when manufacturing the PCB. It is both below and in bom.csv.

Part|Quantity|Price (USD)|Vendor|Link
|---|---|---|---|---|
XIAO ESP32C3|1|$10.11|Amazon|https://www.amazon.ca/MiiElAOD-High-Performance-Cost-Effective-1PCS-Kit/dp/B0GDG7YRGW/ref=asc_df_B0GDG7YRGW?mcid=c3c8863449923deb82a1a4779cbbab0e&tag=googleshopc0c-20&linkCode=df0&hvadid=803091086323&hvpos=&hvnetw=g&hvrand=8414720962410478217&hvpone=&hvptwo=&hvqmt=&hvdev=c&hvdvcmdl=&hvlocint=&hvlocphy=9000910&hvtargid=pla-2493221044780&hvocijid=8414720962410478217-B0GDG7YRGW-&hvexpln=0&gad_source=1&th=1
"OLED 0.96"" I2C display"|1|$3.50|Universal Solder|https://www.universal-solder.ca/product/oled-i2c-0-96-inch-128x64-pixel-ssd1306-sh1106-3-5v/
MPU6050 motion sensor|1|$3.69|Universal Solder|https://www.universal-solder.ca/product/invensense-mpu-6050-6-axis-gyro-accelerometer-module/
10k Resistor|1|$2.07|Sayal Electronics|https://secure.sayal.com/STORE4/prodetails.php?SKU=199179
DHT11 temperature sensor|1|$2.80|BC Electronics|https://bc-robotics.com/shop/dht11-temperature-humidity-sensor/?srsltid=AU7gw4ULU6YRGfsQBjuDnRTJuYX4SkghHcUgPcuIQJyEpNFTL2x4pbFyWcQ
MX Switches|1|$1.83|Amazon|https://www.amazon.ca/Generic-Mechanical-Replacement-Transparent-Experience/dp/B0GLHJQGD3/ref=sr_1_22?crid=1N8868XKKIUWJ&dib=eyJ2IjoiMSJ9.ZpmPzv0I6Ilteff9dFWN4NrcibU4l4RNK3l0ejiIi1fe5Z9izVKID2l5ML8P-Zh-qx9M7m6GS1BwTNYGjuMuoQUiomnBASgPFnM346gCD0M0Gr7ZHteRaXSSOxE6mx5UP36czPogMunnKkvJVZ0kVUY-rNlidTh7pt058naK8sQlQbCbPAhXv2xE_Occ2JLEH74Jlooi-ykvYvcHwkTBVsQRnQ73PgBn6NclhZN5sDXbEJwv9wQVq0LXx4d0aIY916GQEiCXIJ31wq70dm3ONwAdQlrSiuj9f6kdXsisOds.OqesYboksp47K2TkGj2qZPaHTt9My65icp_2Y1-FLL0&dib_tag=se&keywords=mx+key+switches&qid=1791756158&refinements=p_36%3A-1000&rnid=12035759011&sprefix=mx+key+switche%2Caps%2C159&sr=8-22&qty=1&psc=1&sbo=RZvfv%2F%2FHxDF%2BO5021pAnSA%3D%3D
MX Switch Keycaps|1|$6.01|Amazon|https://www.amazon.ca/Profile-Mechanical-Keyboard-Installation-Sublimated/dp/B0D1FSFG37/ref=sr_1_8?crid=32AZNZJ6HC2VP&dib=eyJ2IjoiMSJ9.M1aJJ4SDWbSbarTmmhVoX_OSvyKJGZH3Io6A3D3g2lkaNKds4tSyoKL3NsBRJJaVLYPcI-mSI8HIrpkp7DlXMo_uT3zxMyMb-PmTEmFrrMNIhKMtCo60_Th9nMHQylEY9pXecA4352OuV5zBExydxYPKX4vCqc6YtayF9UyR0gBekyN8QJgGQvW2s12Qtfzy2DyRWE1LPRzV42bWGfB3TmTe6BOtw39t2lB2afE4jnpcIO7WPwvNblqQl_bEikbem1rIs8m43OsXU2y3NiUu5CDMTB8qiWmHbwTFUvc8Lc8.UrV5txzs9T_ENm9jfr3SZ0UiVQLqVuGu6cEPNW6-8Yw&dib_tag=se&keywords=OEM%2BProfile%2BWhite%2BBlank%2BKeycaps%2BPBT%2BMaterial%2B1U%2BR4%2BKeycap%2Bfor%2BMX%2Bswitches%2BMechanical%2BKeyboard%2B(White%2C%2B20pcs)&qid=1791692286&sprefix=oem%2Bprofile%2Bwhite%2Bblank%2Bkeycaps%2Bpbt%2Bmaterial%2B1u%2Br4%2Bkeycap%2Bfor%2Bmx%2Bswitches%2Bmechanical%2Bkeyboard%2Bwhite%2C%2B20pcs%2B%2Caps%2C147&sr=8-8&th=1
PCB|1|$4.00|JLCPCB|https://cart.jlcpcb.com/quote?stencilLayer=2&stencilWidth=100&stencilLength=100&stencilCounts=5&plateType=1&spm=Jlcpcb.Homepage.1010
Shipping & Taxes|-|$39.11|-|-

## Extra Notes
When reviewing the BOM, note that, for some vendors, I had specific promotions/coupons that helped reduce the shipping price. For example, there is a light-package promotion for BC Robotics that allow for free shipping during the fall. This is why my BOM fits under $30 in BOM.md even though the shipping is almost $40 in bom.csv. These promotions may not be applicable to everybody. Furthermore, the shipping and taxes are based on Ontario GST and HST, and it ships to an Ontario address. Therefore, prices may vary based on your location. I am also going to be buying some parts out of my own pocket (not with the grant), which have a price of $0.01 in the BOM.

The cart screenshots submitted on the Half-Life website are in CAD, not USD. The links also lead to Canadian websites that are in CAD. Each individual item in BOM.md was converted from CAD to USD. Because of this, there is a small rounding error due to the exchange rate. As a result, if you add up the cart totals together and convert to USD, it will be slightly off from the BOM, though I will be able to purchase the rest of the routing if necessary. 

I had so much fun creating my Starbie and I can't wait to get into the other projects! ☆



