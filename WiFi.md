# Connecting to Wifi

To connect to wifi we will be using `wpa_cli` tool, first we need to set the credentials for the wifi and then we will initialize the connection by reconfiguiring the wlan0 interface to use new credentials.

```
NOTE: To access the shell you can see the [debug.md](debug.md) documentation file.
```

## Using wpa_cli tool 

1. Open `wpa_supplicant-wlan0.conf` file by using command below: 

    ```
    beagle@BeagleV:~$ sudo nano /etc/wpa_supplicant/wpa_supplicant-wlan0.conf
    ```

2. Now update the `ssid` to your WiFi SSID name (ex: MyWiFI) and `psk` to your WiFI password (ex: passoword)like shown below:

    ```
    ctrl_interface=DIR=/run/wpa_supplicant GROUP=netdev
    update_config=1
    p2p_disabled=1
    #country=US

    network={
            ssid="MyWiFI"
            psk="password"
    }
    ```

3. Save the file using `CTRL + O` then `ENTER` and close the `nano` editor using `CTRL + X` then `ENTER`.
4. To initialize the connection execute the command below:

    ```
    beagle@BeagleV:~$ wpa_cli -i wlan0 reconfigure
    OK
    ```
5. To check the connection you can use `ping` command as shown below:

    ```
    beagle@BeagleV:~$ ping 8.8.8.8
    PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
    64 bytes from 8.8.8.8: icmp_seq=1 ttl=118 time=11.5 ms
    64 bytes from 8.8.8.8: icmp_seq=2 ttl=118 time=8.79 ms
    64 bytes from 8.8.8.8: icmp_seq=3 ttl=118 time=5.13 ms
    ```

    type `CTRL + C` to stop this.


Your BeagleV Ahead is not connected to WiFi and you can start working on your projects.