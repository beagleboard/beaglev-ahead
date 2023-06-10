# Setup Bluetooth

To connect to wifi we will be using `wpa_cli` tool, first we need to set the credentials for the wifi and then we will initialize the connection by reconfiguiring the wlan0 interface to use new credentials.
we use `brcm_patchram_plus` tool to setup bluetooth, first we need to trigger reset pin, then upload bluetooth fw.

```shell
#trigger reset pin
gpioset gpiochip2 28=0
gpioset gpiochip2 28=1

#upload fw
brcm_patchram_plus --enable_hci --no2bytes --tosleep 200000 --baudrate 3000000 --patchram /lib/firmware/BCM43013A0_001.001.006.1073.1102.hcd /dev/ttyS4 &
```

# Setup Bluetooth (with Debug)
```
#upload fw
brcm_patchram_plus -d --enable_hci --no2bytes --tosleep 200000 --baudrate 3000000 --patchram /lib/firmware/BCM43013A0_001.001.006.1073.1102.hcd /dev/ttyS4 &
```

## Check bluetooth interface

```
root@BeagleV:~# hciconfig 
hci0:	Type: Primary  Bus: UART
	BD Address: B8:13:32:EC:59:8B  ACL MTU: 1021:8  SCO MTU: 64:1
	DOWN 
	RX bytes:733 acl:0 sco:0 events:42 errors:0
	TX bytes:464 acl:0 sco:0 commands:42 errors:0
```

## Using bluetoothctl tool 


```
root@BeagleV:~# bluetoothctl 
Agent registered
[CHG] Controller B8:13:32:EC:59:8B Pairable: yes
[bluetooth]# scan on
Discovery started
[CHG] Controller B8:13:32:EC:59:8B Discovering: yes
[NEW] Device 40:97:1C:DF:8B:BD 40-97-1C-DF-8B-BD
[NEW] Device 43:07:E7:3F:85:84 43-07-E7-3F-85-84
[CHG] Device 43:07:E7:3F:85:84 RSSI: -91
[bluetooth]# quit

```
