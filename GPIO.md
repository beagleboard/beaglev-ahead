# GPIO

BeagleV Ahead has cape header pins similar to BeagleBone Black. You can check the documentation page below to know the pin connection to TH1520 SoC:

https://beaglev-ahead.beagleboard.io/docs/latest/boards/beaglev/ahead/connectros.html

To test the GPIO functionality of the pins you can follow steps below:

## Clone BeagleBoard-DeviceTrees

1. Access the shell with the help of [debug.md](debug.md)
2. Connect to WiFi usig [WiFi.md](WiFi.md)
3. Change directory to home using like below:

    ```
    beagle@BeagleV:~$ cd
    ```

4. Clone the repo using command below:

    ```
    beagle@BeagleV:~$ git clone https://git.beagleboard.org/beaglev-ahead/BeagleBoard-DeviceTrees.git
    ```

    Provide your credentials and the wait for cloning to complete.

## Teset gpio-leds with BONE-LED

Follow the steps below to test,

1. change the directory to home,

        ```
        beagle@BeagleV:~$ cd
        ```

2. If not already cloned clone the BeagleBoard-DeviceTrees repo,

    ```
    beagle@BeagleV:~$ git clone https://git.beagleboard.org/beaglev-ahead/BeagleBoard-DeviceTrees.git
    ```

3. Change directory to the repo,

    ```
    beagle@BeagleV:~$ cd BeagleBoard-DeviceTrees/
    ```

4. This step is not required for the first run but handy for further debugging,

    ```
    beagle@BeagleV:~$ make clean
    ```

5. make all the devicetree files and overlays for riscv

    ```
    beagle@BeagleV:~$ make all_riscv
    ```

6. Until uboot overlays support is functional you can use this command to update the base device tree file to include our overlay,

    ```
    beagle@BeagleV:~$ fdtoverlay \
    -i src/riscv/light-beagle.dtb \
    -o src/riscv/light-beagle.dtb \
    src/riscv/overlays/BONE-LED_P8_03.dtbo
    ```

7. Install all the files to your board,

    ```
    beagle@BeagleV:~$ sudo make install_riscv
    ```

8. Reboot your board,

    ```
    beagle@BeagleV:~$ sudo reboot
    ```

9. You should see LED blinking if connected to `P8_03`.

## Testing other pins

The overlay can be updated for other header pins and same steps can be used to test the pins as well. 

You'll have to change [this](https://git.beagleboard.org/beaglev-ahead/BeagleBoard-DeviceTrees/-/blob/v5.10.x-ti-unified/src/riscv/overlays/BONE-LED_P8_03.dts#L26) line according to the pin you want to use.

```
NOTE: It's okay if you don't change anything else like file name and other parts of the overlay to test other pins, you just have to change the reference according to the pin you want to test.
```

For `P8_03` the reference used is `bone_led_P8_03` for other pin like `P8_04` you need to change it to `bone_led_P8_04`. For example, testing `P8_22` will require you to make the change below:

```
&bone_led_P8_22 {
    status = "okay";
    // access: sys/class/leds/led_P8_22
    label = "led_P8_22";
    linux,default-trigger = "heartbeat";
    default-state = "on";
};
```

please note that this is only the portion of the code we need to edit, everything else can be exactly the same unless you really see the need to change it for yourself because it will not affect the testing procedure of the pin.

## Capes

Overlays for LOAD cape and Relay cape are also available to test under overlays folder,

https://git.beagleboard.org/beaglev-ahead/BeagleBoard-DeviceTrees/-/tree/v5.10.x-ti-unified/src/riscv/overlays