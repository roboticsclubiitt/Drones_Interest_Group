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
1. Wiring the components with FC
1. Binding of receiver and controller
1. Installation of MissionPlanner
1. Connection of PixHawk with MissionPlanner (with USB or Telem)
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