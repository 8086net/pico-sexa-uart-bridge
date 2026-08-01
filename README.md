Raspberry Pi Pico USB-UART and I2C Bridge
=================================
This project converts the Raspberry Pi Pico/Pico 2 (or any RP2040/RP2350/RP2354) into a USB to 6 UART and I2C board with activity LEDs.

Supporting hardware, the "PicoUART6" is available on [Lectronz](https://lectronz.com/products/picouart6) and [ThePiHut](https://thepihut.com/products/picouart6).

The 6 USB UART are compatible with the builtin USB CDC class drivers in Linux, macOS, and >= Windows 10.

The I2C interface requires an i2c-tiny-usb driver. On Linux copy the "90-PicoUART6.rules" file into "/etc/udev/rules.d/", run "sudo udevadm control --reload" and then unplug/replug the Pico. Running "i2cdetect -l" will then show the i2c-tiny-usb bus you need to use in your application.

History
----------

This expands [JoeSc's](https://github.com/JoeSc/pico-sexa-uart-bridge) project to add activity LED for each UART which itself expands [Noltari's](https://github.com/Noltari/pico-uart-bridge) project to add 4 additional UARTs using the pico PIOs. And expands on [harrywalsh's](https://github.com/harrywalsh/pico-hw_and_pio-uart-gridge) project to provide better SEO and remove some data loss when using all 6 UARTs concurrently.

It then has [Nicolai-Electronics's](https://github.com/Nicolai-Electronics/rp2040-i2c-interface) project for i2c-tiny-usb support merged in.

Disclaimer
----------

This software is provided without warranty, according to the MIT License, and should therefore not be used where it may endanger life, financial stakes, or cause discomfort and inconvenience to others.

Raspberry Pi Pico Pinout
------------------------
The pinout can easily be modified in uart-i2c-bridge.c but below is the default

| Raspberry Pi Pico GPIO | Function |
|:----------------------:|:--------:|
| GPIO0 (Pin 1)          | UART0 TX |
| GPIO1 (Pin 2)          | UART0 RX |
| GPIO2 (Pin 4)          | UART0 Activity LED |
| GPIO4 (Pin 6)          | UART1 TX |
| GPIO5 (Pin 7)          | UART1 RX |
| GPIO3 (Pin 5)          | UART1 Activity LED |
| GPIO8 (Pin 11)         | UART2 TX |
| GPIO9 (Pin 12)         | UART2 RX |
| GPIO6 (Pin 9)          | UART2 Activity LED |
| GPIO12 (Pin 16)        | UART3 TX |
| GPIO13 (Pin 17)        | UART3 RX |
| GPIO7 (Pin 10)         | UART3 Activity LED |
| GPIO16 (Pin 21)        | UART4 TX |
| GPIO17 (Pin 22)        | UART4 RX |
| GPIO10 (Pin 14)        | UART4 Activity LED |
| GPIO20 (Pin 26)        | UART5 TX |
| GPIO21 (Pin 27)        | UART5 RX |
| GPIO11 (Pin 15)        | UART5 Activity LED |
| GPIO26 (Pin 31)        | I2C SDA |
| GPIO27 (Pin 32)        | I2C SCL |
| GPIO14 (Pin 19)        | I2C Activity LED |
| GPIO15 (Pin 20)        | Power LED |
