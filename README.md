## Hot Rod Project

Revisit and iterate on the old Barbie Jeep project.
The focus will be on robustness over breadth. The Barbie Jeep was a demo project,
and made to look good for presentation, but never to be used beyond demo and IGVC.

I will need to repurchase all of the equipment, and make some adjustments to the 
design. I will also need to secure a place to work and store the Hot Rod.

### Mechanical / Power
The idea is to lengthen the wheel base, increase the power, and make it more safe for operation.
To do this, I will replace the front casters with an extra set of motors and a driver
It may be worth it to look into Ackermann steering, but for now, just assume differential steering.
I will also add a bucket seat and a leg well for safer riding, as well as a dedicated wiring bay in the undercarriage
to manage wires cleanly, probably with a hatch door for maintenance.
The Barbie Jeep has a 25.6v 50ah LiFePO4 battery, it may be a good idea to split it into two 25ah batteries
to spread the weight across the body. The regenerative braking seems to be very strong, that will need to be implemented.

The screws and brackets will be revisited as well, I'm not sure what I will do, but i'm 80% it will
involve a whole fuckton of loctite. Maybe suspension. Who knows.

### Plastic Body Shell

I want a brand new shell design, modeled to look like a classic car
maroon glossy paint. Maybe vacuformed? Maybe painstakingly 3d printed?
This is a later problem.


### Sensors
I want to reimagine the sensor stack, the Barbie Jeep has a fancy set of sensores, 
but the sensors were not utilized well, and the code was rushed and messy. Here's the new plan.

Focus on wheel encoders as an absolute baseline.
 GPS and IMU are supplemental to the wheel encoders.
With this stack, the focus will be put on Position and Velocity estimation using 
filters and dead reckoning, and world frame transformation

LIDAR and Camera are extra. I can buy them, but not putting much focus here.


### Compute Hardware and Software
A 24v to 12v DC-DC Converter will be installed, along with an industrial 12v Mini-PC that will run Ubuntu 20.04
A TI C2000 Series Microcontroller will run off the PC's 5v line.
The C2000 will be responsible for estimating position/velocity
The Mini PC will run a Telemetry Front End in python that will display to the screen
Everything will communicate via IoT Ethernet code, likely just raw TCP with static IPs
The PC can run LIDAR/Camera code down the line.


### Controls
A PID Velocity Controller will have direct access to the wheels.
A higher level PID controller will pursue a set point, "Carrot on a Stick",  Controller.
All internal computation will be done using Unit Quaternion
All Controls will be done in X, Y components


The PC will communicate a set point to the MCU, and the MCU will execute.
LIDAR/Camera can do obstacle avoiding on the PC,
GPS/IMU can do filtered World Frame Estimation on the MCU
Motor controller will be highest compute priority, followed by Wheel Encoders

BIG WiFi Antenna for Base station Control.


### Parts
Sabertooth 2x32 Motor driver - $125 x2
    https://www.dimensionengineering.com/products/sabertooth2x32

Jazzy Wheelchair Motors and Wheels - $150 x2
    https://www.ebay.com/itm/225553112420?_trksid=p2332490.c101430.m3021&itmprp=cksum%3A2255531124200d06be731ead4cf1b8d1c21406435707%7Cenc%3AAQALAAABIEl2UmEc%252FRnpn8E7YLToBDIKeXF20n6bAUu0pLWuFMR0v3iukyhyBShhmY%252BTW91qNiiGku10PYqigv0fTqq6RtUi5sJ5MRv78D26cARNUY5NflsmB3YbfddeGzzRCPX4pD%252BiosCDaU%252Fw6GlFoIeFSBJH%252FdVpmDeCWf%252Ftf6a0HsYcWwC45qss02QuNyCJOZP38f1L%252BvIqV0c%252BI%252BRmFXfz5pmiNxZ4VICmZPPsjeLPSQpQqoYpL2AGwfVSHqrfd8ajbLjsz8YK%252FFWsVB2RsjcPZkOJ3gyLIjj0XlTv2SlEIqx4Yj6%252FY0sKOyNQgfVr0sDUyKDugviGUHu7YwcBwlOMYQqoFZPqY8hSflSk%252FkcAef%252FNMOSdIIddrZxR72%252BnXFs4mQ%253D%253D%7Campid%3APL_CLK%7Cclp%3A2332490&itmmeta=01M7N8WQA0QDQ9N4HWCYK8GKDV

Misumi 4040 Extrusion Black Anodized 

Amazon Wheel Encoders - $15 x4

Android Auto Head Unit - $140
    https://www.amazon.com/SjoyBring-QLED-Double-Din-Stereo/dp/B0CT5P32L7?crid=1V3LTL6S04SFE&dib=eyJ2IjoiMSJ9.dOzr6S4FCXqFJU-X12WbposB89tgX9bo3BWvB_OhmfUif_HjjhoIbwVSs1dyryQWshlsXomGEnUL6oFIBmUbpvQU05188ONKcofbFhMjZyZDIJ0rBDbk7vuVnr0JJgiqwKt6cJTQ4DvMzTq6yNYNIUiuH2uOuPzCm4CEzD_o82-Vu6ceq4gpQhzmj_VHu24XtJSDt6Ecn5LaPpTkD3CYMw.L7d54lhu46m8uCYRU8aXcvGH6G9ugT_QOe5vSgIDop8&dib_tag=se&keywords=android+auto+head+unit&qid=1794937454&sprefix=android+auto+head%2Caps%2C188&sr=8-3#immersive-view_1794952204715




