# Cat Laser Toy 2.0 Part 4

This part of the series continues how to separate the original cat laser code into
two parts, one that runs on the Raspberry Pi and controls the laser and another
that runs on a server (in this case an Ubuntu virtual machine running in Vagrant/VirtualBox)
to provide laser control for many users.  This video explores the following topics:

-   Modifying the original cat laser server code (from the RaspberryPi/LaserServer
    folder) so that it can run on the cloud server and send target commands to
    the Pi over the MQTT broker.

The following code is in this repository:

-   RaspberryPi/LaserDriver - This is the Python 3 code which runs on the Pi and connects
    to the cloud server's MQTT broker allowing remote control of the laser targeting.

-   RaspberryPi/LaserServer - This is the original cat laser project code and is used
    to calibrate the laser so that it can turn screen clicks into servo positions.
    Note that this is NOT the server users will access to control the laser!  Instead
    this is purely for admin/internal use.  Users will access the cloud server and
    special code it's running to control the laser.

-   RaspberryPi/mjpeg-streamer - Instructions and a systemd service to run the
    mjpeg-streamer tool to serve a MJPEG video stream of the Pi camera.

-   CloudServer - This is a Vagrant configuration file for the cloud server.

-   CloudServer/CloudLaserServer - This is the cloud laser server code that will
    allow users to connect to the cloud server and control the laser.

-   CloudServer/mjpeg-proxy - Instructions on how to setup mjpeg-proxy on the
    cloud server so it can relay the Pi's video stream to multiple users.
