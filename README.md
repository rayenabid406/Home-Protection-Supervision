Project Overview:

Supervising electrical systems is essential for safety and efficiency. Monitoring voltage, current, and power helps to:

Ensure the safety of electrical installations

Optimize energy use

Prevent overloads and damage

This project uses an Arduino to create a simple and cost-effective system that measures AC voltage and current in real time, detects overvoltage and overcurrent, alerts the user, and performs automatic protection.

Applications:

Residential buildings: prevent electrical fires and equipment damage

Industrial environments: monitor machinery and optimize energy usage

Power distribution networks: support network stability

System Features:

Real-time measurements

Voltage sensor for AC voltage

ACS712 sensor for AC current

Automatic anomaly detection

Detects overvoltage (OV)

Detects overcurrent (OC)

User notifications:

LCD display shows voltage, current, and power

LEDs and buzzer for alerts

Active protection:

Relay disconnects the load automatically if an anomaly is detected

Hardware Components:

Arduino UNO

ACS712 current sensor

Voltage sensor

16x2 LCD display

Buzzer and LEDs

Electromechanical relay

Supporting components (resistors, capacitors, wires)

System Architecture:

1. Measurement:

Voltage: Transformer → Voltage Divider → RC Filter → Arduino A0

Current: ACS712 → Arduino A1

2. Processing:

Calculate RMS voltage, current, and power

Compare values to predefined safety thresholds

Decide in real time if action is needed

3. Action:

Normal mode: display values on LCD

Alert mode:

LED indicators for OV/OC

Buzzer alert

Relay disconnects load

Advantages:

Fast reaction time (milliseconds)

Dual protection: alert + automatic disconnection

Simple and easy-to-use interface

Affordable solution

How to Use:

Connect sensors and components to the Arduino as described.

Upload the Arduino code.

Power the system to monitor voltage and current.

In case of overvoltage or overcurrent, the system triggers alerts and disconnects the load automatically.

Test & Simulation:

Simulated overvoltage and overcurrent conditions

Verified fast response and accurate RMS calculations

Confirmed proper relay operation for load protection

Conclusion:

This project demonstrates a home electrical supervision system that monitors and protects electrical networks in real time. It is suitable for domestic use and small industrial applications.

Further improvements could include remote monitoring, data logging, or mobile alerts for a more advanced smart home system.
