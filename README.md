# NVVR lighthouse tracking solution V1
## Latest update
<img src="V1.6/working1.jpg" style="height:auto;width:100%;">
Got most of the stuff working properly.

Base station remained unchanged (however i think its about time to replace it`s breadboard with a more permanent protoboard and resolve problems with high jitter, low sync pulse timing accuracy and bad PID tuning, and i noticed that sync blinker isnt powerful enough even for > 2 meters).

The tracker now uses RP2040-Zero board. Firmware utilizes 4 PIOs (2 pairs of new sensor data checker + changes time stamper) and outputs from those PIOs are sent into chained DMAs without using cpu resources, then this data is pulled from DMAs into queues and sent to the COM port by the other core.

The python program reads packets from the tracker and tries to separate sync and sweep pulses for each sensor and checks if previous frame is complete on sync pulse events. Then it calculates angle data (not the actual X and Y angles because of base station`s lenses arangement) and sends it to unity via TCP connection.

Unity reads angle data from TCP connection, then fixes the angles (lenses are rotated 45deg in relation to the base station and 90 deg from each other, and when laser lines overlap, they form an X shape) and draws them as red rays.

TODO: finally write a 6DOF position solver.

## Base station V1.6
<img src="V1.6/basestation1.jpg" style="height:auto;width:50%;">

### IR shots
<img src="V1.6/basestation2.jpg" style="height:auto;width:50%;">
<img src="V1.6/basestation3.jpg" style="height:auto;width:50%;">

### Mechanical scheme
<img src="V1.6/mech_scheme.jpg" style="height:auto;width:90%;">

### Electrical scheme
<img src="V1.6/elec_scheme.jpg" style="height:auto;width:90%;">

## Prototype htc wand inspired tracked object V1.2 (work in progress)
### Real life pictures
<img src="V1.6/irl_td18_1.1.jpg" style="height:auto;width:70%;">
<img src="V1.6/irl_td18_2.jpg" style="height:auto;width:70%;">
<img src="V1.6/irl_td18_3.jpg" style="height:auto;width:70%;">
<img src="V1.6/irl_td18_4.jpg" style="height:auto;width:70%;">

### PCB design
<img src="V1.6/td18_pcb_1.png" style="height:auto;width:50%;">

### CAD model
<img src="V1.6/cadwand122_1.png" style="height:auto;width:70%;">
<img src="V1.6/cadwand122_2.png" style="height:auto;width:70%;">
<img src="V1.6/cadwand122_3.png" style="height:auto;width:70%;">
<img src="V1.6/cadwand122_4.png" style="height:auto;width:70%;">
<img src="V1.6/cadwand122_5.png" style="height:auto;width:70%;">

### Real life pictures
<img src="V1.6/irl_wand122_1.jpg" style="height:auto;width:70%;">
<img src="V1.6/irl_wand122_2.jpg" style="height:auto;width:70%;">

### Real life valve prototypes pictures
<img src="V1.6/irlwand1.png" style="height:auto;width:70%;">
<img src="V1.6/irlwand2.jpg" style="height:auto;width:70%;">



# Old stuff
## 4-sensor tracker V1.1 (obsolete)
<img src="V1.6/tracker.jpg" style="height:auto;width:100%;">

### Sensor scheme
<img src="V1.6/sensor_scheme.png" style="height:auto;width:100%;">

### Sensor PCB
<img src="V1.6/sensor_3d.png" style="height:auto;width:50%;">

## Software
<img src="V1.6/viz.png" style="height:auto;width:80%;">

## Random data
<img src="V1.6/graph1.png" style="height:auto;width:100%;">
<img src="V1.6/graph2.png" style="height:auto;width:100%;">



## Contact
Telegram: @nvcoder

Email: nv.coder@yandex.ru