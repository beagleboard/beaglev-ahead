# Debug port

To debug the board we have two options,
1. UART
2. JTAG

Below are the details on how to use these interfaces.

## UART debug port

With `v0.2 (DVT)` of BeagleV Ahead board you have BeagleBone Black style header pins but due to some unknown reason it's not compatible with the usual FTDI debug cable like [this](https://www.adafruit.com/product/70). To make the connection, you can use FTDI module like [this](https://www.amazon.in/HiLetgo-Ft232rl-Serial-Adapter-Arduino/dp/B00IJXZQ7C/) to only make the connections listed below:

1. Connect `TXD` pin of FTDI module to `RX` pin of BeagleV Ahead.
2. Connect `RXD` pin of FTDI module to `TX` pin of BeagleV Ahead.
3. Connect `GND` pin of FTDI module to `GND` pin of BeagleV Ahead.

After making the connections, you can use serial communication tools like `tio` to see the boot log and get access to the shell. Using `tio` is very simple, you just have to know the serial port of the FTDI module. To identify the serial port of your FTDI module you can see [this](https://www.mathworks.com/help/supportpkg/arduinoio/ug/find-arduino-port-on-windows-mac-and-linux.html) simple guide. Now execute the command below to make the connection:

```
[lorforlinux@fedora ~] $ tio /dev/ttyUSB0
```

I am using Linux and serial port for my FTDI module is thus I used `/dev/ttyUSB0` as port name you may have different name so please update the command accordingly.

## JTAG

