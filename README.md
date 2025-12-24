📌 Overview

This project implements a single-user elevator controller for a 3-floor building using Verilog HDL.
The elevator serves Floor 0 (Idle Floor), Floor 1, and Floor 2, following realistic elevator behavior:

Accepts inside (cabin) and outside (hall) button requests
Moves to the requested floor
Opens doors for a fixed duration
Automatically returns to Floor 0 after dropping the passenger

The design is based on a Finite State Machine (FSM) and uses counters to model travel time and door open time.

🏢 Floor & Button Configuration
Outside (Hall) Buttons
Floor	Buttons Available
Floor 0	UP
Floor 1	UP, DOWN
Floor 2	DOWN
Inside (Cabin) Buttons

Only one request is handled at a time, reflecting the single-user assumption.

⚙️ Functional Behavior

Elevator idles at Floor 0
A request is made via:
Inside cabin button OR
Outside hall button
Elevator moves up or down to the requested floor
Doors open for a fixed duration
After servicing the request, the elevator returns to Floor 0
Elevator re-enters IDLE state

🧠 Design Architecture
The elevator does not use sensors. Instead:
Travel time between floors is modeled using counters
Door open time is also counter-based

These values are parameterized and can be adjusted easily.
parameter CLK_FREQ_HZ     = 50_000_000;
parameter TRAVEL_TIME_MS  = 2000;
parameter DOOR_OPEN_MS    = 1500;


🧪 Testbench

A dedicated testbench is included to simulate:

Selecting floors from inside the elevator
Calling the elevator from Floor 1
Automatic return to Floor 0
Simulation outputs can be viewed using GTKWave via the generated .vcd file.

🚧 Assumptions & Limitations

Single user only (no request queue)
No emergency handling
No door obstruction logic
No button debouncing (assumed ideal inputs)
No floor sensors (time-based movement only)

🔮 Possible Extensions

Multi-request queue
Priority scheduling
Emergency stop
Door obstruction detection
Floor sensors instead of timers
Seven-segment floor display
