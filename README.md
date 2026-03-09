# Arduino Yun MQTT Example

Example project demonstrating how to connect an **Arduino Yún** to an **MQTT broker** and exchange messages using the MQTT publish/subscribe protocol.

This project shows a simple IoT architecture where an Arduino device publishes and receives messages through an MQTT messaging server.

## Overview

MQTT (Message Queue Telemetry Transport) is a lightweight messaging protocol designed for machine-to-machine (M2M) communication and Internet of Things (IoT) devices.

It works using a **publish/subscribe model** where devices send messages to a central server called a **broker**.

Key advantages of MQTT:

- Very lightweight protocol
- Low bandwidth usage
- Low power consumption
- Fast communication
- Reliable message delivery
- Ideal for embedded and wireless environments

## Architecture

Arduino Yun → MQTT Broker → Subscriber / Other systems

The Arduino acts as a **client** that can:

- Publish messages to a topic
- Subscribe to topics
- Receive messages from other systems

## Repository Structure

Arduino-Yun-MQTT.ino   # Arduino sketch
MQTT.js                # Node.js MQTT client example
README.md              # Project documentation

## Requirements

Before running the project you need:

- Arduino IDE
- Node.js
- MQTT Broker (Mosquitto recommended)
- Arduino PubSubClient library

## Installation

### 1. Install MQTT broker (Mosquitto)

Example on Linux:

sudo apt install mosquitto mosquitto-clients

### 2. Install Node.js MQTT client

npm install mqtt --save

### 3. Install Arduino MQTT library

Install **PubSubClient** in the Arduino IDE.

## Example Node.js Client

var mqtt = require('mqtt')
var client  = mqtt.connect('mqtt://localhost:1883')

client.on('connect', function () {
  client.subscribe('outTopic')
  client.publish('inTopic', 'Hello Arduino')
})

client.on('message', function (topic, message) {
  console.log(message.toString())
})

## Example Use Cases

This project can be used for:

- IoT device communication
- Sensor data transmission
- Home automation
- Remote monitoring systems
- Embedded device messaging

## Author

**Sergio Marín Boza**  
Software Architect | Backend & Enterprise Systems  

GitHub  
https://github.com/Gazu  

Website  
https://smb-tech.cl/
