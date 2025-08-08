
This Arduino sketch creates a security system using a keypad, servo motor, buzzer, LED, and a distance sensor. It simulates a door lock system that triggers an alarm when an object comes too close and allows access only after entering the correct password via the keypad.

Hardware Used:
Keypad (4x4) – For entering the password

Servo motor – Acts as a door lock mechanism

LED (pin 13) – Indicates an alarm state

Buzzer (pin 12) – Sounds during an alarm

Analog Distance Sensor (A0) – Detects proximity

Serial Monitor – Outputs keypad entries and status messages

Program Behavior:
Startup (setup()):

Sets pin modes.

Attaches the servo and locks it (servo at 180°).

Starts serial communication.

Main Loop (loop()):

Continuously checks for:

Proximity alarm condition: If an object is detected within a certain range (analogRead(dist) > 90) and the alarm is active:

The LED turns on.

The buzzer sounds.

Servo stays locked.

Keypad input:

Each key press is logged via Serial.

If 4 digits are entered, they're compared to the correct password ("1319"):

If correct: Servo unlocks (set to 90°), LED and buzzer turn off, alarm is deactivated.

If incorrect: Alarm remains active.

The input buffer resets after every 4 characters.

Key Features:
Password Protection: Uses a hardcoded password to unlock.

Intrusion Detection: Monitors distance and triggers alarm if someone approaches while system is locked.

Manual Input Reset: Input clears after every 4 entries (whether correct or incorrect).

