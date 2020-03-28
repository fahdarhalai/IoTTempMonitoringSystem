# IoT Temperture Monitoring System
IoT-Based Temperature monitoring system using MQTT protocol and Flask Micro-Framework for visualisation.

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
1. Raspberry PI Setup:
Using a software such as Putty would be great to connect to the raspberry PI.
First run the commands:
`sudo apt-get update
sudo apt-get upgrade`
Then you need to install mosquitto on the raspberry using the command:
`sudo apt install -y mosquitto mosquitto-clients`
Check mosquitto version with `mosquitto -v` and let it run on background using `mosquitto -d` command.
You can also check the status of mosquitto at any time using:
`systemctl status mosquitto.d`
2. Setup the web server:
On your computer, you need to install Flask micro framework using the commands:
`
pip install flask
pip install flask-socketio
`
You also need mqtt python package, just run:
`pip install paho-mqtt`

