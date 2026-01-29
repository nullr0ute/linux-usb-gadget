# A generic Linux USB Gadget service

This enables you to turn your SBC into a USB Gadget providing Ethernet and Console over a USB cable. A number of devices have a UDC (USB Device Controller) enabling the device to appear as Gadget/Device on a USB bus. There are a number of examples of similar tools available but all are specific to one device, provide one service, or work with one Linux distro. Hopefully this is designed to be agnostic to all, but it's still early days.

Linux has USB device capabilities enabling a number of virtual devices to be presented to the host. This service currently provides options to use the USB-CDC `/dev/ttyACM0` and USB Ethernet (USB-ECM), it doesn't currently support the legacy RNDIS interface, enabling serial consoles and ssh over the USB cable for headless devices. In the future it's possible we could add other options such as storage.

The current version provides a service that runs with the systemd usb-gadget.target once the UDC hardware is available in Linux. As a result you don't currently get firmware or early boot output. The intention is to eventually provide the ability to have a USB-CDC `/dev/ttyACM0` from within firmware that supports it (U-Boot) and have a USB Console available from firmware right through to console login.
