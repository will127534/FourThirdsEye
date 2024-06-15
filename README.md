# FourThirdsEye: Opensource Micro Four Thirds camera module based on IMX294
![](https://github.com/will127534/FourThirdsEye/blob/2d40e392c67383d515081146fcd0cbcc5ac29037/PCBA.jpg)

## Introduction
Welcome to the **FourThirdsEye** project, an open-source camera board designed for Raspberry Pi 5 and Raspberry Pi Compute Module 4 boards using a Micro Four Thirds format image sensor IMX294. This project aims to provide a high-quality, affordable, and accessible camera module for advanced Raspberry Pi projects. The board is designed using KiCad v6, a popular open-source electronics design automation (EDA) software.

FourThirdsEye captures 10.7 Mpix images and 4K (4096 x 2160) videos with improved low-light performance and dynamic range (4.63 um pixel size). It's perfect for photography enthusiasts, developers, and makers who want to level up their Raspberry Pi projects with a powerful camera.

## Features
* **Open-source hardware and software**
* IMX294 sensor
* Integrated TMP117 temperature sensor
* Compatible with Raspberry Pi5 and Raspberry Pi Compute Module 4 boards with a 22-pin FPC connector and 4-lane MIPI-CSI (same pinout as Raspberry Pi Compute Module 4 IO Board)

## Notes
* Gerber, BOM and CPL file for JLCPCB is under /Gerber
* [Interactive BOM](https://htmlpreview.github.io/?https://github.com/will127534/FourThirdsEye/blob/main/ibom.html) [(provided by InteractiveHtmlBom)
](https://github.com/openscopeproject/InteractiveHtmlBom)
* Driver for Raspberry Pi: [https://github.com/will127534/imx294-v4l2-driver](https://github.com/will127534/imx294-v4l2-driver)
* 3D model and E-mount adaptor + Filter design is under /3D_model, note that you will need to grab the metal ring from a E-mount (lens extender or replacements parts) and mount it to the 3D printed adaptor.

## Sidenotes
IMX294 with CSI-2 interface mode is running at 1.78Gbps, technically breaking the spec for RPI5 (1.5Gbps) and CM4 (1Gbps?...they didn't really state it clearly) but I have tested on both platforms and are both working properly. But the one catch is that FPC cable quality/length will impact the data transmition, I've see black/bad pixel data scattering in the frames with a long 50cm cable, but it is fine with the 20cm cable. Also to actually utilized the full capacity/FPS of the sensor on RPI5, you will need to overclock RP1 (Camera Frontend) so it can handle the sensor at 60 FPS 4K. The sensor itself is also quite interesting because it is actually a quad bayer array just with subpixel combined output only, it is technically capable of sending high/low gain frame output but I'm still waiting for the HDR support on RPI5 to actually test it.

As for the PCB board design, the goal is to make a miniaturized camera board, but because of that I have to use smaller via sizes (0.2mm) and via-in-pad for the decoupling capacitors. There is also a bunch of tiny common mode CSI-2 filter that it might be hard for hand soldering so PCBA services or stencil + paste is the perfer way to build it.

Last thing is that if you are looking to capture RAW videos with Raspberry Pi 5, checkout [CinePi](https://github.com/cinepi/cinepi-sdk) from [@schoolpost](https://csabanagy.ca).

## Support
For questions, issues, or suggestions, please open an issue in the [GitHub repository](https://github.com/will127534/FourThirdsEye/issues)

## Schematic
![](https://github.com/will127534/FourThirdsEye/blob/2d40e392c67383d515081146fcd0cbcc5ac29037/SCH.jpg)

## PCB
![](https://github.com/will127534/FourThirdsEye/blob/2d40e392c67383d515081146fcd0cbcc5ac29037/PCB.JPG)
*Screw hole sizes are M3
