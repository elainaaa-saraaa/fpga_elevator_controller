📌 Overview

This project implements a single-user elevator controller for a three-floor building using Verilog HDL. The elevator services Floor 0, which acts as the idle floor, along with Floor 1 and Floor 2. The system is designed to mimic realistic elevator behavior by accepting both inside (cabin) and outside (hall) button requests, moving to the requested destination floor, opening the doors for a fixed duration, and automatically returning to Floor 0 after the passenger is dropped off.

The overall control logic is based on a Finite State Machine (FSM). Counters are used to model the time taken to travel between floors as well as the duration for which the doors remain open.

🏢 Floor & Button Configuration

The building consists of three floors with a predefined set of hall buttons. Floor 0 is equipped only with an UP button, as it is the lowest and idle floor. Floor 1 contains both UP and DOWN buttons, allowing calls in either direction, while Floor 2, being the topmost floor, is provided only with a DOWN button.

Inside the elevator cabin, floor selection buttons are available for Floor 0, Floor 1, and Floor 2. The system is designed to handle only one request at a time, which reflects the single-user assumption and simplifies control logic.

⚙️ Functional Behavior

Under normal operation, the elevator remains idle at Floor 0. When a request is made, either from inside the cabin or from an outside hall button, the controller determines the direction of movement and drives the elevator upward or downward accordingly. Upon reaching the requested floor, the doors are opened for a fixed duration to allow passenger movement. Once the request has been serviced, the elevator automatically returns to Floor 0 and re-enters the idle state, ready to accept the next request.

🧠 Design Architecture

The elevator system does not rely on physical position sensors. Instead, movement between floors is modeled using counters that represent travel time, and door operation is similarly controlled using a counter-based timing mechanism. These timing parameters are configurable and can be easily adjusted to suit different clock frequencies or simulation requirements, as shown below:

parameter CLK_FREQ_HZ     = 50_000_000;
parameter TRAVEL_TIME_MS  = 2000;
parameter DOOR_OPEN_MS    = 1500;

🧪 Testbench

A dedicated testbench accompanies the design to verify correct functionality. The testbench simulates scenarios such as selecting destination floors from inside the elevator, calling the elevator from Floor 1, and observing the automatic return to Floor 0 after servicing a request. Simulation results are captured in a .vcd file, which can be viewed using GTKWave for waveform analysis.

🚧 Assumptions & Limitations

The design assumes the presence of only a single user at any given time, and therefore does not implement request queuing or prioritization. Emergency handling, door obstruction detection, and button debouncing are not included, with all inputs assumed to be ideal. Additionally, the system operates without physical floor sensors and relies solely on time-based movement modeling.

🔮 Possible Extensions

The current design can be extended to support multiple queued requests, priority-based scheduling, emergency stop functionality, and door obstruction detection. Further enhancements may include the use of floor sensors instead of timing-based movement and the integration of a seven-segment display to indicate the current floor.


>> Project by:
1. Elaina Sara Sabu
2. Meria Rachel Binu
3. Adithya Radhakrishnan
4. Sagarika Prasandan
