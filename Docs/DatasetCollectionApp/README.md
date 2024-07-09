# DatasetCollector

A command line app to collect signal datasets from a CalyoPulse device, allowing you to specify device parameters as cmdline arguments. 

Upon launch, the app will try to open a connected sensor with the provided serial number. If the device cannot be opened, the app will close with the return code ```1```. Remember: on linux, driver setup needs to be done once, and ```sudo rmmod ftdi_sio``` needs to be run every time the device is connected.

Upon successful opening of the device, the app will proceed to acquire the number of frames of raw signal data specified and write xml datasets (see DatasetLib) to the directory specified by the user. Each of the datasets will be named by their timestamps. 

Once all datasets have been collected, the app will close with return code ```0```.

## Dependencies

- DatasetLib
- DeviceLib

## Arguments

Launch the application with the following commandline arguments (in order):
- Device serial number (str)
- Number of pulse cycles (uint)
- Max distance (float)
- Path to directory (str)
- (optional) Number of frames to collect (default = ~infinite)

