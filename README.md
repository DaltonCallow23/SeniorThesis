# RF Telemetry Communication System Specification

**Author:** Dalton Callow

## Introduction

The RF Telemetry Communication System is a senior thesis project designed to facilitate two-way communication between a rocket and a ground station. Employing Radio Frequency (RF) technology, this system enables the real-time collection of vital information such as altitude, location, temperature, and more. Its primary objective is to ensure the continuous acquisition of flight-related data, even in the event of a mission failure when other data collection systems may become inoperative.

## Use Cases

### Actor: Rocket

#### Use Case 1: Transmit Telemetry Data

**Overview:** The rocket transmits telemetry data to the ground station.

**Main Success Scenario:**

1. The rocket initiates the telemetry data transmission.
2. The RF Telemetry Communication System establishes a connection with the ground station.
3. Telemetry data, including altitude, location, and temperature, is transmitted to the ground station.

**Extensions:**

**Connection Failure**
  - If the RF communication link cannot be established, the system retries the connection three times before generating an error report.

#### Use Case 2: Receive Commands

**Overview:** The rocket receives commands from the ground station.

**Main Success Scenario:**

1. The ground station initiates a command transmission.
2. The RF Telemetry Communication System receives the command.
3. The rocket executes the received command.

**Extensions:**

**Invalid Command**
  - If an invalid or unrecognized command is received, the rocket sends an acknowledgment of receipt but takes no further action.

### Actor: Ground Station

#### Use Case 3: Receive Telemetry Data

**Overview:** The ground station receives telemetry data from the rocket.

**Main Success Scenario:**

1. The ground station awaits incoming telemetry data.
2. The rocket transmits telemetry data.
3. The ground station receives and stores the telemetry data for analysis.

**Extensions:**

**Data Loss**
  - In the event of data loss during transmission, the ground station requests a retransmission of missing data segments from the rocket.

#### Use Case 4: Send Commands

**Overview:** The ground station sends commands to the rocket.

**Main Success Scenario:**

1. The operator at the ground station initiates the command transmission.
2. The RF Telemetry Communication System transmits the command to the rocket.
3. The rocket receives and executes the command as instructed.

**Extensions:**

**Communication Error**
  - If a communication error occurs during command transmission, the ground station retries sending the command and logs the issue.

#### Use Case 5: Process Data

**Overview:** The ground station processes and saves received data.

**Main Success Scenario:**

The ground station successfully receives telemetry data from the rocket.
The received data is prepared for storage, including data validation and formatting.
The processed telemetry data is saved to a CSV (Comma-Separated Values) file in the designated storage location.

**Extensions:**

**Invalid Data**
-If telemetry data received is found to be invalid or corrupted during processing:
The ground station logs the discrepancy or error for further analysis.
The system discards the invalid data to prevent its inclusion in the saved CSV file.
Processing continues with the next valid data packet received.
### Actor: Mother Board

### Use Case 6: Sensor Data Collection

**Overview:** 
The Motherboard is responsible for collecting data from an assortment of sensors and preparing it for transmission.

**Main Success Scenario:**

The Motherboard is connected to various sensors as per project requirements.
Periodically, at predefined intervals, the Motherboard initiates the collection of sensor data.
The Motherboard retrieves data from all connected sensors.
The collected sensor data is processed and formatted for transmission.

**Extensions:**
None

## Technology Overview

### Hardware Components:

1. **RF Transceivers:** Select RF transceivers capable of both sending and receiving radio signals, tailored to the project's frequency bands and communication range requirements.

2. **Microcontrollers/Embedded Systems:** Utilize microcontrollers (e.g., Arduino, Raspberry Pi) or custom-designed boards to control and interface with RF transceivers, manage data processing, implement protocols, and interface with sensors.

3. **Sensors:** Incorporate various sensors, including altitude sensors, GPS modules, temperature sensors, accelerometers, and gyroscopes, for telemetry data collection.

4. **Battery Power Supply:** Ensure a reliable and rechargeable battery power supply to sustain continuous operation during the rocket's flight.

5. **Antennas:** Select antennas meticulously to optimize signal transmission and reception.

### Software Components:

1. **Communication Protocol:** Employ a suitable communication protocol for RF transceivers, such as UART, SPI, or custom protocols tailored to project requirements.

2. **Embedded Software:** Develop firmware for microcontrollers or embedded systems to control RF transceivers, manage sensor data, and handle data transmission and reception.

3. **Ground Station Software:** Create software for the ground station to receive, process, and store telemetry data. This may involve graphical user interfaces (GUIs) for operators.

4. **Command Handling:** Implement code to interpret and execute commands received from the ground station, ensuring the system handles valid commands and responds appropriately to errors.

5. **Retransmission Mechanism:** Incorporate a retransmission mechanism to guarantee the reliability of telemetry data by retransmitting missing or corrupted data segments.
