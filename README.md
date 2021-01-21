# Neato XV-11 Standalone LiDAR ROS Driver

## Nodes

### neato_laser_publisher

ROS wrapper for the xv11_laser_driver library that's also available in this package.

**Published Topics**

- scan (sensor_msgs/LaserScan)
  - Scan data from the laser. Under normal conditions, contains 360 pings at 1 degree increments.

**Parameters**

- ~port (string, default: /dev/ttyUSB0)
  - The device path
- ~baud_rate (int, default: 115200)
  - The baud rate to receive laser data. Should not be changed from 115200 unless the laser's baud rate is changed (by a firmware upgrade, for example).
- ~firmware_version (int, default: 1)
  - The firmware version that attempts to interpret the byte format of the laser. There are two known firmwares right now. One is noted for sending all 360 pings in a structure. This is probably the older firmware and is "1" for this value. The other sends the pings 4 at a time. This is probably the newer firmware and is "2" for this value. There isn't a reliable way to get the firmware version from the laser right now, so you'll have to set this and check a visualization of the pings in order to see if the driver is correctly interpreting the laser bytes.
- ~frame_id (string, default: neato_laser)
  - The laser data frame. This frame should be at the optical center of the laser, with the x-axis along the zero degree ray, and the y-axis along the pi/2 degree ray.

## Library

### XV11 Laser Driver

xv11_laser_driver is a C++ library for reading the data from the XV11's laser and packing that data into a sensor_msgs/LaserScan. As a standalone library, it has no ROS API.
