# Weerstation

## Introduction

I started this project in 2017 as a combination of the following items:
* Arduino with sensors to measure outside temperature / air pressure / humidity
* Arduino with an ultrasonic sensor to measure the water level in a rainwater well
* Raspberry Pi running Raspbian (now 'Raspberry PI OS')

Along the way, the following was added/changed:
* 2 indoor sensors, making use of Particle Photon boards
* A website in JS -> this was converted to a PHP version
* A very simple iOS app (I don't consider myself to be a developer)

## Component overview / details

### Housing (Stevenson Screen)

* Stevenson Screen (self-made out of wood, https://en.wikipedia.org/wiki/Stevenson_screen)
* Cabling from Arduino to breakout board: UTP (Cat 5) running through a 20 meter underground plastic tube
* The Arduino itself is placed in a garden shed (where it connects to the internet via Wi-Fi)

### Arduino-based weather station with sensors

* Board type: Arduino Uno WiFi
* Sensors: 
  * SHT-31 (temperature / humidity)
  * MPL3115A2 (air pressure / temperature)
  * MCP9808 (temperature)
* Code can be found in the following repository: https://github.com/kvandebeek/Arduino-weather

### Arduino-based water level meter with ultrasonic sensor

* Board type: Arduino Uno Wifi
* Sensors:
  * Grove Ultrasonic (this is connected to the Arduino using a 15 meter cable going through an underground plastic tube)
* Other components:
  * LCD display that shows the level (in centimeter) and the percentage relative to the maximum (which is 5000 liter)
  * LED bar with 10 LEDs ranging from 'red' to 'green' to show the level
* Code can be found in the following repository: https://github.com/kvandebeek/Waterlevel

### Raspberry PI running Raspbian

* Operating system: Raspberry PI OS (Debian 10 - Buster)
* Web server: Apache 2
* MySQL server: Ver 15.1 Distrib 10.0.28-MariaDB
* Other tasks: CRON jobs and SHELL scripts to generate weather data

- an Arduino with temperature / air pressure / humidity sensors connected, housed in a Stevenson Screen (https://en.wikipedia.org/wiki/Stevenson_screen)
- an Arduino with an ultrasonic sensor to measure the water level in a rainwater well, inspired by an article I read (https://www.automaton.be/blog/niveau-regenwater-meten/3077/)
- a Raspberry PI running Raspbian (currently at 'Debian 10', Buster - https://en.wikipedia.org/wiki/Raspberry_Pi_OS)
  - this acts as a web server (Apache) that hosts my website
  - it is also a MySQL server (MariaDB) that hosts the data
  - it runs CRON jobs and has scripts to generate data that are displayed on the website and in the iOS app

Additions/changes in 2020:
- 2 indoor sensors, making use of Particle Photon boards
- Changed the initial website which was in JS with a PHP version
- Created a simple iOS app
  - Works on iPhone (iPad not supported)
  - Shows data from the webserver
  - Uses an external chart library to show historic data
  - Is used to get more familiar with test automation
