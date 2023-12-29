# Damn Vulnerable Drone

Damn Vulnerable Drone is an intentionally vulnerable drone hacking simulator based on the popular ArduPilot/MAVLink architecture, providing a realistic environment for hands-on drone hacking.

<p align="center">
  <img src="https://github.com/nicholasaleks/Damn-Vulnerable-Drone/blob/master/simulator/static/images/Damn-Vulnerable-Drone-Banner.png?raw=true" alt="DVD"/>
</p>

# Table of Contents

* [About Damn Vulnerable Drone](#about)
  * [Features](#features)
  * [Architecture](#architecture)
  * [Flight States](#flight-states)
* [Attack Scenarios](#attack-scenarios)
* [Operating Modes](#operating-modes)
* [Installation](#installation)
  * [Installation - Docker](#docker)
  * [Installation - Kali](#kali)
* [Management Console](#management-console)
  * [Beginner/Advanced Modes](#changing-modes)
  * [Changing Flight States](#changing-flight-states)
* [Screenshots](#screenshots)
* [Maintainers](#maintainers)
* [Contributors](#contributors)
* [Mentions](#mentions)
* [Disclaimer](#disclaimer)
* [License](#license)

# About Damn Vulnerable Drone

Damn Vulnerable Drone (DVD) was built to provide offensive security professionals with safe virtualized environment to practice a wide range of drone hacking techniques.

The Damn Vulnerable Drone was designed to replicate a small UAV (Unmanned Aerial Vehicle) that has a low endurance and small Line-of-Sight (LOS) operating radius based on a WiFi data-link. The Drone uses [MAVLink](https://mavlink.io/en/) (a lightweight messaging protocol) to communicated with a simulated Ground Control Station (GCS) using [QGroundControl](http://qgroundcontrol.com/). The Drone also uses [ArduPilot](https://ardupilot.org/) (an open source autopilot system) to manage autonomous flight controls and Software-in-the-Loop (SITL) to emulate real-world drone behaviours by running actual flight code and telemtry, typically found in drone hardware, within [Gazebo](https://gazebosim.org/home) (a visual world physics simulator).

While the Damn Vulnerable Drone setup doesn't mirror every drone architecture or configuration, the integrated tactics, techniques and scenarios are broadly applicable across various drone systems, models and communication protocols.

Damn Vulnerable Drone also contains a Simulatior Management Console (SMC), to help provide users with full control of the simulator and guide the their learning experience.

## Features

- **Realistic Drone Simulation**: Utilizes the popular drone technologies and architectures to mimic real-world behaviors and vulnerabilities.
- **Virtualized Environment**: Runs in a completely virtualized setup, making it accessible and safe for experimentation.
- **Simulated Wireless Networking**: Simulated Wifi (802.11) interfaces to practice wireless drone attacks.
- **Simulator Management Console**: Simple to use simulator management web console used to trigger scenarios and drone flight states.
- **Comprehensive Hacking Scenarios**: Ideal for practicing a wide range of drone hacking techniques, from basic reconnaissance to advanced exploitation.

## Architecture

Damn Vulnerable Drone uses a Docker environment to encapsulate several containers which represent components that can be found in most drone-stacks.
- *Drone Flight Control Unit (FCU)*: Controls the drone's flight mechanisms and autopilot.
- *Drone Companion Computer*: Simulates the drone's onboard computer.
- *Ground Control Stations (GCS)*: Acts as the command and control center for the drone.
- *Simulator*: Uses Gazebo to provide a realistic drone flight simulator

The above four containers make up the simulated drone-stack. This stack is intended to be built and run with docker on a Kali VM.
You can manage the simulated environment by using the built-in DVD Management Console.

## Flight States

Damn Vulnerable Drone simulates various drone states for a realistic testing environment. Users can manage the drone states in real-time by using the Management Console.
1. Initial Boot & Configuration
2. Idle Standby
3. Active Flight
4. Autopilot Flight
5. Emergency, Return-To-Home (RTH) Landing
6. Post-Flight Data Processing
7. Shutdown

# Attack Scenarios

The list of attack scenarios below is organized by stages. Note that some attacks are only possible during certain flight states.

* **Reconnaissance**
  * Drone Discovery
  * Ground Station Discovery
  * Network Fingerprinting
* **Wireless Network Attacks**
  * WEP Network Cracking - using Aircrack-ng
  * Man-in-the-Middle Eavesdropping - using Wireshark
* **Denial of Service**
  * Ground Control DeAuth - using Airodump
  * Drone Computer Process Killing
  * Mid-flight Drone Shutdown
  * MAVLink Router Table Overflow 
**Reverse Engineering**
  * Telemtry Analysis
  * Decompling Firmware
* **Protocol Spoofing**
  * MAVLink Message Replaying
  * GPS Spoofing
  * Drone Telemtry Data Spoofing - Tricking the GCS
* **Command Injection & Hijacking**
  * MAVLink Message Command Injection
  * Drone Hijacking via Ground Control Station Spoofing
  * Ground Control Station Hijacking via Drone Laterl Movement
* **Firmware Attacks**
  * Malicious Firmware Upload
  * Jailbreaking Parameter Tampering
* **Data Collection & Exfiltration**
  * Onboard SD Card Data Collection
  * Flight Data Log Collection
  * AWS Secrets Extraction
  * Drone Wifi Client Data Leakage
  * Live Drone Video Camera Streaming

# Operating Modes

**Full Deploy Mode**

`Full Deploy Mode` allows for Damn Vulnerable Drone to use a virtually simulated wifi network as the drones data-link connection between its Ground Station and Companion Computer.
The system requirements to run `Full Deploy Mode` a Kali VM with the following minimum requirements:
* Kali Linux VM (Ubuntu 22.04 is also supported)
  * 8-16 GB RAM
  * 2-4 Processor Cores
  * 100 GB Disk Storage
  * Docker
  * Docker Compose

To install the `full deploy mode` see installation details below.

**Half-Baked Mode (Docker-Only)**

`Half-Baked Mode` essentially only runs the Damn Vulnerable Drone docker containers.
Unlike `Full Deploy Mode` you are not limited to only running half-baked mode within a Kali Linux VM.
However, half-baked mode does not support wifi simulations and you will need to assume that you have an established foothold on the drones data-link connection.

To install the `half-baked mode` see installation details below.

# Installation

`sudo ./start.sh`

# License

It is distributed under the MIT License. See LICENSE for more information.

