# IoT Temperture Monitoring System
IoT-Based Temperature monitoring system using MQTT protocol and Flask Micro-Framework for visualisation.<br>
**The project is deployed on Heroku, you can check it out from here: [IoT temperture Monitor](https://temp-monitoring-iot-system.herokuapp.com/)**

## Overview
This project presents a standalone web server with a Raspberry Pi MQTT server that displays temperature readings with a DHT22/DHT11 sensor.
In order to create the web server we will be using a Python microframework called Flask. Here’s the high level overview of the system:

<p align="center">
  <img src="https://user-images.githubusercontent.com/41004675/77822722-b25d9f80-70f5-11ea-95c5-583a72d961c0.PNG" />
</p>

The MQTT client publisher is a NodeMCU Arduino compatible ESP8266 based micro controller with on-board WiFi. It is great for IoT projects or just as an Arduino replacement.
Three BreadBoard are used, each of which, houses the ESP8266 micro controller, the DHT11 temperture & humidity sensor, and three LEDs(Red, Orange, Green), that light up when a threshold temperture is bypassed. The following schema describes the various components on each BreadBoard:

<p align="center">
  <img src="https://user-images.githubusercontent.com/41004675/77823036-51839680-70f8-11ea-8dcb-a713c598e5a1.PNG" />
</p>

**Devices & Components used:**
- Raspberry PI 3 B+
- 3 temperture modules each composed of
  - ESP8266
  - Red/Orange/Green LED
  - DHT11 sensor
- A Web Server (using Flask MicroFramework)

## Setup
**1. Raspberry PI Setup:**<br>
  Using a software such as Putty would be great to connect to the raspberry PI.<br>
  First run the commands:<br>
  `sudo apt-get update`<br>
  `sudo apt-get upgrade`<br>
  Then you need to install mosquitto on the raspberry using the command:<br>
  `sudo apt install -y mosquitto mosquitto-clients`<br>
  Check mosquitto version with `mosquitto -v` and let it run on background using `mosquitto -d` command.<br>
  You can also check the status of mosquitto at any time using:<br>
  `systemctl status mosquitto.d`
<br><br>
**2. Setup the web server:**<br>
  On your computer, you need to install Flask micro framework using the commands:<br>
  `pip install flask`<br>
  `pip install flask-socketio`<br>
  You also need mqtt package, just run:<br>
  `pip install paho-mqtt`<br>
  `pip install mqtt-client`<br>

## Testing
Clone my repository using: `git clone https://github.com/fahdarhalai/IoTTempMonitoringSystem`. Run the project with `python app.py` then go to `http://localhost:8181`.<br>
The project is also deployed on Heroku, it uses Eclipse public mqtt Broker for publishing/subscribing to topics, you can view it at [IoT temperture Monitor](https://temp-monitoring-iot-system.herokuapp.com/). Each client publishing temperture values to a specific topic used throughout the development of the project, will eventually make the application running in real time. I wrote a shell script too, that simulates the three NodeMCU modules, publishing temperture readings to Eclipse MQTT Broker, you can run it in git bash(For windows users).
![Screenshot](https://user-images.githubusercontent.com/41004675/77823485-c6a49b00-70fb-11ea-92cd-4c45831eeaaa.png)

