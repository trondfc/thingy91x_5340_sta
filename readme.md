# WiFi sta on thingy91x_nRF5340
Setup for running the WiFi station example on the Thingy91x with nRF5340.

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
Before running the project the **nRF9151** must be wiped to free up the external flash and the nRF7002.
To do this, connect the power and debuggers to the Thingy:91x, ensure switch 2 is set to the nRF91 target, and erase the flash using erase all in nrf connect programmer.

Before flashing the project, ensure that switch 2 is set to the nRF5340 target.
```
west build -p -b thingy91x/nrf5340/cpuapp
west flash --erase
```