# SeniorThesis
RF Telemetry Communication System
RF Telemetry Communication System Specification

Author: Dalton Callow

Introduction

The RF Telemetry Communication System is a senior thesis project aimed at facilitating two-way communication between a rocket and a ground station. This communication system utilizes Radio Frequency (RF) technology to transmit data between two modules, enabling the real-time collection of critical information such as altitude, location, temperature, and more. The primary objective of this system is to ensure the continuous acquisition of flight-related data, even in the event of a mission failure, where other data collection systems may become inoperative.

Use Cases

Actor: Rocket

Use Case 1: Transmit Telemetry Data

Overview: The rocket transmits telemetry data to the ground station.

Main Success Scenario:

1\. The rocket initiates the telemetry data transmission.

2\. The RF Telemetry Communication System establishes a connection with the ground station.

3\. The telemetry data, including altitude, location, and temperature, is transmitted to the ground station.

Extensions:

Connection Failure

  - If the RF communication link cannot be established, the system retries the connection three times before generating an error report.

Use Case 2: Receive Commands

Overview: The rocket receives commands from the ground station.

Main Success Scenario:

1\. The ground station initiates a command transmission.

2\. The RF Telemetry Communication System receives the command.

3\. The rocket executes the received command.

Extensions:

Invalid Command

  - If an invalid or unrecognized command is received, the rocket sends an acknowledgment of receipt but takes no further action.

Actor: Ground Station

Use Case 3: Receive Telemetry Data

Overview: The ground station receives telemetry data from the rocket.

Main Success Scenario:

1\. The ground station awaits incoming telemetry data.

2\. The rocket transmits telemetry data.

3\. The ground station receives and stores the telemetry data for analysis.

Extensions:

Data Loss

  - In the event of data loss during transmission, the ground station requests a retransmission of missing data segments from the rocket.

Use Case 4: Send Commands

Overview: The ground station sends commands to the rocket.

Main Success Scenario:

1\. The operator at the ground station initiates the command transmission.

2\. The RF Telemetry Communication System transmits the command to the rocket.

3\. The rocket receives and executes the command as instructed.

Extensions:

Communication Error

  - If a communication error occurs during command transmission, the ground station retries sending the command and logs the issue.

Technology Overview

Hardware Components:

1\. RF Transceivers: RF communication relies on transceivers that can both send and receive radio signals. These should be selected based on the frequency bands appropriate for your project and the range required for rocket-ground station communication.

2\. Microcontrollers/Embedded Systems: Microcontrollers or embedded systems like Arduino, Raspberry Pi, or custom-designed boards may be used to control and interface with the RF transceivers. These systems will handle data processing, protocol implementation, and interfacing with sensors.

3\. Sensors: Various sensors will be needed to gather telemetry data, such as altitude sensors, GPS modules, temperature sensors, accelerometers, and gyroscopes.

4\. Battery Power Supply: Reliable and rechargeable battery power supply will be essential to ensure continuous operation during the rocket's flight.

5\. Antennas: Carefully chosen antennas are critical for optimizing signal transmission and reception.

Software Components:

1\. Communication Protocol: A communication protocol suitable for your RF transceivers is needed. Common options include UART, SPI, or custom protocols tailored to your project's needs.

2\. Embedded Software: Develop firmware for the microcontroller or embedded system to control the RF transceivers, manage sensor data, and handle data transmission and reception.

3\. Ground Station Software: Create software for the ground station to receive, process, and save telemetry data. This may involve graphical user interfaces (GUIs) for operators.

4\. Command Handling: Develop code to interpret and execute commands received from the ground station. Ensure that the system can handle valid commands and respond appropriately to errors.

6\. Retransmission Mechanism: Implement a retransmission mechanism for missing or corrupted data segments to ensure the reliability of telemetry data.
