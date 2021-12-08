.._usb_dongle

Bluetooth: CENTRAL UART WITH USB_ACM_CDC
#########################################

.This file contains the source code for a sample application that uses the Nordic UART service Client
and USBD CDC ACM library for use with the PCA10059 Dongle
It uses the NUS service to send data back and forth between a USB (Virtual Com Port) connection and a Bluetooth® LE connection, emulating a serial port over Bluetooth LE.
This Project was completed using NRF5 SDK V17.1.0

Overview
********

This project uses the CDC ACM USB class, commonly known as Virtual COM port with the Central Nordic UART Service (NUS). After plugging the PCA10059 Dongle into the USB Port, the PCA10059 Dongle will enumerate as a COMx port on Windows hosts or as a /dev/ttyACMx device on Linux/Unix hosts. The port can be opened and closed just like a traditional serial port.

The Nordic UART Service (NUS) Client Application implements the Nordic UART Service Client over BLE. In this project, the PCA10059 board serves as a GAP central and a GATT client.

The application scans peripheral devices and connects to a device that advertises with the NUS UUID in its advertisement report. After connecting, the application enables notifications on the device that delivers the Nordic UART Service.

Testing
********
Two boards are needed to perform this test:

Central board: nRF5 PCA10059 board containing the SoftDevice S140.
Peripheral board: nRF5 development board containing the SoftDevice and the UART peripheral application provided with the nRF5 SDK.
The application running on the Peripheral board is intended to serve as a peer (for example, in the Nordic UART Service (NUS) Application role) to this NUS Client application.

Test the BLE NUS Client Example application by performing the following steps:

1. Compile the usb_dongle Example application and program both the SoftDevice and the application on the Central board.
2. On the Central board, observe that the BSP_INDICATE_SCANNING state is indicated. This shows that the application is scanning for a NUS service Peripheral.
3. Compile the NUS application and program both the SoftDevice and the application on the Peripheral board.
4. Observe that the NUS Peripheral is advertising.
5. Once the connection is established, the BSP_INDICATE_CONNECTED state is indicated on both boards.
6. Now it is possible to send data between the two boards. To do so, send data to one of the boards using the serial port.
7. Observe that the data is displayed on the Terminal window on the other board.
8. Disconnect the devices, for example by pressing the Reset Button on the Central board. Observe that the boards automatically reconnect and that it is again possible to send data between the two boards.

