## Initial Setup

To enable use of the sensor on your machine, you will first have to add the sensor device type to your **udev rules**. This process **only needs to be done once**, unless your reinstall or modify your OS. Do the following:

-  Open a terminal 

-  Navigate to **/etc/udev/rules.d** directory
	`cd /etc/udev/rules.d`
	
-  Create a file named **99-ftdi.rules**
	`sudo touch 99-ftdi.rules`
	
- Paste the following line into the file:
	`SUBSYSTEMS=="usb",ATTRS{idProduct}=="6014",ATTRS{idVendor}=="0403",GROUP="plugdev",MODE="666"
`
- Save the file, and **reload udev rules** using the following command
	```sudo udevadm trigger```

## On every launch

To prepare the environment for the device drivers, you will need to run the following command, before opening the application:

```
sudo rmmod ftdi_sio
```

This command should be run **every time the sensor is plugged in** to your computer, after it has been plugged in. This will enable data acquisition from the sensor.

Alternatively, this command could be put into a script that runs your CalyoSensus executable (or ROS2 node), or added to your bashrc file, which runs automatically whenever a terminal is opened.