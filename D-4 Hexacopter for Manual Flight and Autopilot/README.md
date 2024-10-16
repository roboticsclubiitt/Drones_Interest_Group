# Shatayan

Shata(meaning “hexa” or “six”) yan(meaning “vehicle”)  
  
## Introduction:

Welcome to the documentation of our hexacopter project. Our hexacopter, known as "Shatayan," is a cutting-edge UAV (Unmanned Aerial Vehicle) that combines the F550 frame with the Pixhawk flight controller. This documentation provides an overview of our project, highlighting key features, versatility, and safety measures. It's structured to guide you through assembly, configuration, flight operations, and future enhancements, making it a valuable resource for both enthusiasts and learners in the world of aerial robotics  
  
## Components:

1. 1 x Frame F550 (700gm)
1. 6 x BLDC motor A2212 13T 1000KV
1. 6 x Simonk 30A ESC
1. 6 x Propeller 1045 (3xCW , 3xCCW)
1. 1 x Pixhawk 2.4.8 Kit with Buzzer and Safety switch
1. 1 x APM/Pixhawk Power Module
1. 1 x GPS Module
1. 1 x FS-i6X Transmitter
1. 1 x FS-iA10B Receiver
1. 2 x 433MHz Telemetry Transceivers
1. 1 x 3S 35C 5200 mah LiPo Battery
1. 1 x LiPo Battery Voltage Tester
1.  Essential -  M2 M3 screw,XT60 female connector ,T connector ,zip ties ,soldering iron ,Allen keys(2.5 ,2.0, 1.5),Motor Prop Adapter 

## Procedure

The hexacopter was assembled and configured with the following steps:
  
1. Assembly of frame
1. Soldering of ESCs and XT60 Connector of battery
1. Installation of all components on frame (FC, Receiver, Motor, Telem, GPS, Buzzer, Safety Switch, Power Module, Battery, Voltage Tester)
1. Connection of motors with ESC
1. Binding of receiver and controller
1. Installation of MissionPlanner
1. Flashing firmware
1. Setup and Calibration of PixHawk via MissionPlanner
1. Testing
1. Lift Off!
1. Setting modes: Manual, Loiter, RTL (explanation of modes given later)
1. Installation of CMOS FPV Camera
1. Setting up autopilot with Mission Planner
1. Test flight
1. Lift Off! v2

### Assembly of Frame  
  
The frame can be prebought on robu.in and it includes 6 arms, an upper plate and a lower plate. The lower plate has a built in power distributer soldered into it so you just need to solder on the battery and PCB on the plates as indicated, make sure of polarity.  
  
[Here is where you should solder. The plate has + and - indicators](https://imgur.com/a/LuGpqaD)  
  
Use M3 screws to join the arms of hexacopter to its plates, and M2 screws to join the motors to the arms. The BLDC motors have a [specific layout](https://cdn.shopify.com/s/files/1/2024/0305/files/A2212-980_03.jpg?v=1497237935) you need to screw the bolts in.  
  
### Soldering of ESCs and XT60 Connector
  
Make sure to use plenty of solder because it gives the least contact resistance and thus evenly distributes voltage across all the motors. Red = +ve Black = -ve end. The ESCs must be ziptied below the arm because the wind from the wing can cool the ESC. The XT60 connector also requires a lot of solder as its a very thick wire. You will also need to attach a [power module](https://robu.in/wp-content/uploads/2017/05/APM-Pixhawk-Power-Module-V6.0-Output-BEC-3A-XT60-Plug-28V-90A2.png) with your battery to modulate power to and from the pixhawk.  
  
### Installation of all components on frame (FC, Receiver, Motor, Telemetry etc)  
  
The FC must be in the center of the system. The forward arrow must point towards your forward position. If you have a [PPM](https://circuitglobe.com/difference-between-pam-pwm-and-ppm.html) receiver, it can be connected to the RCIN port of the port rail at the top. Signal PIN is at the bottom, voltage wires are at the top. This convention is the same for all connections to the ESC. The data-ground-voltage pins of the ESC are connected to the MAIN OUT 1-6 according to the layout you flash on the Pixhawk (more on that later). The GPS will be connected with [DF-13 pins](https://www.lambdrive.com/depot/Robotics/Controller/PixhawkFamily/Connector/). The GPS will connect to an I2C port (this is for voltage, as its a 2-wire-4-pin connection only). The data of the GPS is transferred through the GPS port of the Pixhawk with a 4-wire-6-pin connection. Buzzer and Safety Switch will be connected as per the notation on the Pixhawk. The Voltage Tester is basically a voltmeter which will directly connect to the battery with its data wires. It will tell the voltage of every cell of the battery.  

### Connection of Motors with FC  

When motors are screwed on the arms, the wires must be pointing inwards. The banana pin of the ESC can be connected in any order. Upon later testing if you find that the motor is spinning in the opposite direction than it should then you can switch direction of the outer 2 banana pins of the BLDC motor.  

### Binding transmitter and receiver  

Connect ESC data pins to CH1 of the transmitter. Connect the battery to the ESC. Now, short the transmitter by connecting the signal pin of the BAT channel to GND. This will put it in bind mode. After that, press and hold the BIND key on your transmitter. This will put the transmitter in bind mode too. Then it will bind to the closest receiver in bind mode.  

### Installation of Mission Planner  

If you are on Windows, Mission Planner is very easy to install from [here](https://ardupilot.org/planner/docs/mission-planner-installation.html)  
If you are on Linux, Mission Planner can run from Mono (instructions given on the mission planner documentation), or you can use [QGroundControl](http://qgroundcontrol.com/)  

### Flashing firmware on PixHawk  

First you need to connect the PixHawk to MissionPlanner (MP) [using MAVLink Protocol via USB Cable](https://ardupilot.org/copter/_images/pixhawk_usb_connection.jpg)  
Simply connect the micro USB to your PC and select the correct COM port and click connect. The rest will happen automatically. If you have any errors, refer to the Mission Planner Documentation.  
[Here is what the Mission Planner screen should look like after connection](https://ardupilot.org/planner/docs/mission-planner-overview.html) To flash the neccessary firmware on your pixhawk first go on Setup -> Install Firmware.  
Choose Hexacopter from the menu screen. Use the Pixhawk-1 board.  

### Setup and calibration of Pixhawk  
  
Go to the **setup** tab. click on "Mandatory Hardware". You need to follow the instructions given on the Mission Planner UI, alternatively you can follow the video linked here made by the Techmaniacs team. The setups you need are: accelerometer, compass, battery, radio, flight modes, motors, esc. There are some other setup and calibrations as well, which can easily be followed on [this website](https://george-hawkins.github.io/arf-drone/docs/pixhawk-setup).  
  
Tips:  
1. If you can buy 433MHz radio telemetry then accel and compass calibration is a lot easier  
1. For Hexacopter we are using the 10000 mAh 35c Orange Battery. The charge rating x c rating of the battery is its max optimum current output (ex: 10,000 * 35 = 350 mA). Make sure this is higher than the total current demanded by escs.  
1. In radio calibrations, check if all the channels are working to your preference. Always push the sticks to their maximum value to set the correct min/max points  
1. Usually, the modes Stabilize (Manual), Loiter (GPS- assisted stable flight) and Auto (programmed flight mode) are put.  
1. Motors can take a while to set up, if they are acting up in the motor test then try to replace/recalibrate them. If you are having too many issues then contact the club.  
  
Here are some videos to help:  
1. [Loading Firmware](https://drive.google.com/file/d/1tkC9xu2rq5P5uMSHTJJpcLtjN3YlWZqm/view?usp=drive_link)  
1. [Acceleration Calibration](https://drive.google.com/file/d/1dMRHs9OxpNX8nZRfqG4Pr-94_BGuvyis/view?usp=drive_link)  
1. [Compass Calibration](https://drive.google.com/file/d/1OHofWVJugcSTIvYxe1xmSL4FSvQT5UX-/view?usp=drive_link)
1. [Radio calibration](https://drive.google.com/file/d/1nvhGLdIiS273es1NOmGbTZt9S1Cg70QQ/view?usp=drive_link)
1. [Motor Test](https://drive.google.com/file/d/1yEVil0lTvRaCfc6eVQNDdxCvhjUP6esX/view?usp=drive_link)  
1. [ESC Calibration](https://drive.google.com/file/d/10Asm9Zohenm_TqoBq88DooqRjY5BS_7P/view?usp=drive_link)  
1. [Final Check](https://drive.google.com/file/d/12Awy3K_IShCmI1_yHmOxF_lt7djYtKKd/view?usp=drive_link)
  
### Testing   
   
The Stabilize and Loiter modes must be tested manually. Auto mode can be tested by uploading a custom flight path and seeing how it follows that path.  
  
#### 1) Stabilize  
  
We need to test if the tilt is happening in the same direction as your intention and to the scale neccessary. If any movement is happening in the opposite direction to your intented direction of stick movement then change the RCX_REVERSED parameter by using the Config tab. 

1. Arm the drone by moving the throttle stick down and right.  
1. Hold the drone over your head.  
1. Move the pitch stick forward. If you feel a force forward, then the motors are calibrated in the correct direction. If not, then change the RCX_REVERSED parameter. Do the same for the back direction  
1. Move the roll stick leftwards. If you feel a force leftwards, then the motors are calibrated in the correct direction. Do the same for the right direction.  
1. Move the yaw stick leftwards. If you feel a torque leftwards, then the motors are calibrated in the correct direction. Do the same for the right direction.  
1. Get a feel for the throttle by changing the throttle mode while someone is holding onto the drone. Don't worry as long as you don't hold it to your head the drone can not lift anyone up. Refer to the documentation of your motors to see how much payload the drone can lift. The payload to drone weight ratio is usually near 2:1  
  
### 2) Loiter  
  
Loiter is a very useful mode as the drone uses GPS assist to stay stable in exactly one place. We can save a drone from a crash by putting it in loiter and it will stay stable.