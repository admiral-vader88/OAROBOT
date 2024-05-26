# Obstacle Avoidance Robot
Obstacle Avoidance Robot using Arduino
An obstacle avoidance robot is an autonomous robot designed to navigate its environment while avoiding collisions with obstacles. Here's a detailed description of such a robot using an Arduino, an L298N motor driver, two DC motors, and two Li-ion batteries:

### Components:
1. **Arduino Uno**: The microcontroller that serves as the brain of the robot, processing sensor data and controlling the motors.
2. **L298N Motor Driver**: A dual H-Bridge motor driver that allows control of the speed and direction of two DC motors.
3. **Two DC Motors**: These provide the movement for the robot, typically attached to wheels for mobility.
4. **Ultrasonic Sensor**: Used to detect obstacles in the robot's path by emitting sound waves and measuring the time it takes for the echo to return.
5. **Two Li-ion Batteries**: Provide power to the Arduino and the motors, ensuring sufficient energy for prolonged operation.
6. **Chassis**: The frame of the robot, which holds all components together.
7. **Wiring and Connectors**: To connect all components, ensuring proper communication and power distribution.

### Working Principle:
1. **Power Supply**: The two Li-ion batteries are connected in series or parallel, depending on the required voltage and current, to power both the Arduino and the motors via the L298N motor driver.
2. **Motor Control**: The L298N motor driver is connected to the Arduino, which sends PWM (Pulse Width Modulation) signals to control the speed and direction of the DC motors. The motors are attached to wheels, enabling the robot to move forward, backward, and turn.
3. **Obstacle Detection**: The ultrasonic sensor is mounted on the front of the robot. It continuously emits sound waves and listens for their echo. The Arduino calculates the distance to an obstacle based on the time taken for the echo to return.
4. **Decision Making**: When the ultrasonic sensor detects an obstacle within a predefined distance threshold, the Arduino processes this information and decides on the action to take (e.g., stop, turn left, or turn right).
5. **Navigation**: The robot moves forward until an obstacle is detected. Upon detection, the Arduino commands the L298N motor driver to stop the motors and then change their direction to avoid the obstacle. This might involve reversing slightly and turning before proceeding forward again.

### Example Flow:
1. **Initialization**: The Arduino initializes the motor driver and the ultrasonic sensor.
2. **Movement**: The robot moves forward, with the motors powered by the L298N driver.
3. **Detection**: The ultrasonic sensor continuously checks for obstacles. If an obstacle is detected within 20 cm:
   - The Arduino stops the motors.
   - The Arduino decides on a new direction (e.g., turn right).
   - The motors are activated to turn the robot.
4. **Avoidance**: After turning, the robot resumes forward movement, continuing to check for obstacles and repeating the process as needed.

### Circuit Connections:
- **Arduino to L298N**:
  - `IN1, IN2, IN3, IN4` pins on the L298N connected to four digital pins on the Arduino (e.g., 8, 9, 10, 11).
  - `ENA, ENB` pins on the L298N connected to two PWM pins on the Arduino (e.g., 5, 6) to control speed.
  - `VCC` and `GND` of L298N connected to the batteries for motor power.
  - `5V` and `GND` from the Arduino to the L298N for logic power.
- **Motors to L298N**:
  - Two DC motors connected to the `OUT1, OUT2` and `OUT3, OUT4` terminals of the L298N.
- **Ultrasonic Sensor to Arduino**:
  - `Trig` pin to a digital pin on the Arduino (e.g., 7).
  - `Echo` pin to another digital pin on the Arduino (e.g., 6).
  - `VCC` and `GND` to the Arduino's `5V` and `GND`.
