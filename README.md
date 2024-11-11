# FRSKY_Tracker
Tracking and observing FRSKY telemetry data via Bluetooth
It allows the reception of telemetry data from FRSKY transmitters with Bluetooth, for example X20, Horus, etc.
It allows real-time tracking of an RC plane and the observation of telemetry data on an Android tablet.

The application has a home screen with several options.

1 .- Activate tracking on map (internet connection required)

2 .- Connect via Bluetooth to your transmitter

3.- Telemetry signal configuration. Initially, the signals are already pre-set by FRSKY, but these can be modified and others added.

4 .- Change font size, this allows viewing on a phone or tablet with a different font size.

5 .- This button initializes the Height reference for both the barometer and the GPS and GPS-Cumulative_distance.



When you press the tracking option, a map of the location where the screen is started appears. A blue dot will appear, representing the GPS position (airplane) and the position of the tablet or smartphone.
The map is centered on the location of the Android device. This map can be rotated and zoomed. If you press the location indicator and drag it to another point, the map will be centered on that point. This allows you to better select the flight area within the map.
![Screenshot_2024-11-08-15-26-16-229](https://github.com/user-attachments/assets/53390c08-be95-4282-96f6-b3dbff2950ff)

On this screen, the Bluetooth name that you have set for your transmitter appears and MAC-Address. To set the name , you mast enter the transmitter and modify it in the Bluetooth settings. This appears as Local Name in the Bluetooth settings.
The GPS Lat and Long location, time provided by the GPS, and GPS speed are also displayed. The altitude can be given by either the GPS or the Barometer, if available.

![Screenshot_2024-11-08-15-26-35-243](https://github.com/user-attachments/assets/ab8b06f4-a7b0-45a1-9265-77c1009dee36)

When you press the navigation option again you return to the data display screen.

Next is the Bluetooth connection and disconnection option. It allows you to reconnect or disconnect from your transmitter.
You can also see the option to change the font size, which is useful when installing on a smartphone, since the application is designed to be viewed from a tablet. With a large font size.
You can also see the reset option, which is useful before starting the flight, since it is interesting to take the altitude value as a reference to see the differential height at which the plane is flying. This option also resets the accumulated distance to zero, since you can make a second flight without stopping the plane, which would make this distance continue to increase.
The signal configuration option allows you to define new signals not previously configured by the FRSKY protocol. We have taken as a reference the work of oXs_on_rp2040 in his document https://github.com/mstrens/oXs_on_RP2040/blob/test/doc/fields%20per%20protocol.txt . Based on this work, we define these signals in the original database of the application. But you can create new signals, you just have to maintain the criteria we indicate.
The identifiers must be four digits (hexadecimal) the first digit if it is zero is not represented.
The signal descriptions 25 digits without spaces.
The conversion factors in some cases such as Latitude, Longitude, Time and Speed ​​are represented but are fixed. In the rest of the cases they can be modified.

![Screenshot_2024-11-08-15-26-42-618](https://github.com/user-attachments/assets/3f815183-74fb-420b-bd85-88e3f1ac6ae0)


The data you see in the image are taken from an Archer+ GR8 receiver that has a Bariometer and a GPS manufactured with the technique described in the mstrens/oXs_on_RP2040 repository ( https://github.com/mstrens/oXs_on_RP2040 ) . The results of this are excellent and we recommend its use.

Install the application.
-Download the application and install it, then you must activate your MAC-Address with the following instructions:

In order to continue with the work of developing applications on FRSKY radio telemetry, we ask the collaboration of the users a contribution of 10 €, that you can make effective by paypal to the  paypal.me/matorra . Additionally, we need you to send us via email ma.torra@telefonica.net the Local address, which you can find in your radio in the Telemetry option of your model. I will send you a QR code to activate your app for your radio station, the app only works with your radio, it guarantees that it only connects with your radio station and not others in your area. This payment is one-time and is not required for future updates and improvements to the app.

The app will ask for permission to access the camera by scanning the QR code. It will then ask for Bluetooth access and must have access to the location to position the pilot. It has no other permissions and does not have advertising.

![20241107_171816](https://github.com/user-attachments/assets/493d327e-3ed5-46c9-bbc7-dcc3d3eb300b)

Notes on FRSKY bluetooth telemetry.
The bluetooth option of FRSKY telemetry mirrors the communication bus of the receiver and transmitter. This is s.port communication.
This data is not affected by any modifications you make to your transmitter, anything you do to your transmitter in relation to telemetry only affects the telemetry display on it.
Except for some signals such as GPS Latitude and Longitude, time, rx battery voltage. Almost all signals are transmitted as integer values ​​for greater accuracy they are multiplied by a factor of 100 or 10 etc. It is also possible that the signal transmission is done in units other than the metric system. For example GPS speed is transmitted in knots multiplied by 100 so we have to put a conversion factor to display it as K/h.
This can be changed in the configuration screen where you can even create new signals. To do this, once you have entered the screen, enter the number that appears in the signal telemetry as the ID, which is a four-digit hexadecimal number (if the first one is zero, it is not entered) and complete the configuration data. Once modified, when you return to the data screen, it will appear in the list of received data.
