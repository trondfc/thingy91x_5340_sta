# WiFi sta on thingy91x_nRF5340
Setup for running the WiFi station example on the Thingy91x with nRF5340 while the nRF9151 is on.

## User Configurations
The settings for this demo are defined in the `prj.conf` file.

To necessary settings to run the demo:
- Enter your Wi-Fi credentials (SSID and Password) in `prj.conf`


**prj.conf changes**
```Cmake
CONFIG_WIFI_CREDENTIALS_STATIC_SSID="YourSSID"
CONFIG_WIFI_CREDENTIALS_STATIC_PASSWORD="YourPassword"
```

## Building and Running the Project
#### nRF9151
To build the project for the nRF9151 with the external flash disabled, use the nrf9151dk target to avoid the static partitioning setup for the thingy91x.

Because we are using the nrf9151dk target instead of the thingy91x target, we need to make necessary changes in the board overlay file `boards/nrf9151dk_nrf5340_ns.overlay`. In this sample only the configuration for the leds, button and uart0 are modified to work on the thingy91x.

Before flashing the nRF9151, ensure that switch 2 is set to the nRF9151 target.
```
west build -p -b nrf9151dk/nrf9151/ns
west flash --erase
```


Before flashing the nRF5340, ensure that switch 2 is set to the nRF5340 target.
```
west build -p -b thingy91x/nrf5340/cpuapp
west flash --erase
```