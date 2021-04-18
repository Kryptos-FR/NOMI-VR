# Start Building The NOMI VR Headset
<p align="center"> <img src="resources/img/open.jpg"> </p>

# Building The Hardware
The NOMI VR Headset hardware is based on the Atmel SAM3X8E ARM Cortex-M3 processor and uses an MPU-6050 as it’s IMU.
Alternatively, any processor that supports the ArduinoCore and is connected to an MPU-6050/MPU-9250 can be used as the hardware for NOMI VR. Both methods are explained below.

## Building The Motherboard
### PCB Manufacturing.

We first start with the naked PCB.

it can be manufactured and bought for around $4 on websites like <a href="https://jlcpcb.com/">jlcpcb</a>.

You’ll need to provide the Gerber file folder `NOMI-VR_Headset/nomivr_Electronics_build/GerberFiles.zip` which describes the shape of the board.


### Assembling

Soldering the components onto the naked PCB. 

You will have to buy the components listed in one of the two BOMs, depending on availability:
- `NOMI-VR_Headset/Build/nomivr_Electronics_build/Assembly/jlcpcb.com_motherboard_BOM.csv` 
- `NOMI-VR_Headset/Build/nomivr_Electronics_build/Assembly/motherboard_BOM.xlsx`

Where to position those components on the PCB is described in the file `NOMI-VR_Headset/Source/nomivr_Electronics_source/motherboard.brd` which can be opened in Eagle.

<p align="center"> <img src="resources/img/motherboard.jpg"> </p>

#### Using an Arduino

An alternative to the Motherboard is to use an Arduino Due and to connect it to an MPU-6050.
```
5V      -> VCC  
GND     -> GND  
SDA(20) -> SDA  
SCL(21) -> SCL  
PIN 2   -> INT  
```

If you are using an MPU-9250 with the alternative firmware provided the pinout is:

```
5V      -> VCC  
GND     -> GND  
SDA(20) -> SDA  
SCL(21) -> SCL   
```

Then push the `ERASE` and the `RESET` button on the Arduino Due and you’ll be able to install the NOMI VR Firmware.

#### Installing The NOMI VR Headset Firmware

<p align="center"> <img src="resources/img/cards.jpg"> </p>
You will now need to install the motherboard in the Arduino IDE. 

To do that copy that JSON URL: https://raw.githubusercontent.com/nomi-vr/NOMI-VR/NOMI-VR_Headset/Build/nomivr_Firmware/package_motherboard_index.json and open the Arduino IDE

In Arduino, Click File and then Preferences:

- If you are using the NOMI VR PCB, add the JSON URL to the `Additional Boards Manager` text box.
- Go to `Tools > Board > Board Manager` and you should see the Relativty Board, click install.
- Reboot the Arduino IDE and under Tools > Boards, select Relativty.
- You can now open `NOMI-VR_Headset/Build/nomivr_Firmware/firmware/firmware.ino` and upload it to your board.

If you are using a different board e.g. Arduino Due:

- install contents of `NOMI-VR_Headset/Build/nomivr_Firmware/motherboard` to your Arduino IDE
- if you are using MPU-6050, use `NOMI-VR_Headset/Build/nomivr_Firmware/firmware/firmware.ino`
- if you are using MPU-9250, use `NOMI-VR_Headset/Build/nomivr_Firmware/MP9250-HID.ino`



# Building The Mechanical Parts

## Assembling the HMD

All the files needed for the 3D printing can be found in the `NOMI-VR_Headset/Build/nomivr_Mechanical_build` folder and the screws needed to assemble the Headset are listed in `screws_BOM.xlsx`.

We've used parts from Aliexpress:

- <a href="https://www.aliexpress.com/item/33058848848.html">The Strap</a>, 
- <a href="https://www.aliexpress.com/item/4000199486058.html">The Foam</a>,
- <a href="https://www.aliexpress.com/item/33029909783.html">The Lenses</a> (40mm diameter/50mm focal length).

### The screen for the HMD
<p align="center"> <img src="resources/img/display.jpg"> </p>

The NOMI VR Headset runs a dual-screen at 120FPS 2K, however, because of the open nature of the NOMI VR Headset you can equip it with any screen.

Our screen model can be found on Aliexpress, but depending on the vendor similar screens can cost from $150 to $190. You'll have to hunt and maybe wait for the right vendor at the right price to get the display for cheap (or buy in bulk). 

This is [the model we used](https://www.aliexpress.com/item/32975198897.html).

Now you need to setup the drivers and software for the NOMI VR Headset
