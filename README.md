# Up-Down Counter (0-9) using VHDL and FPGA

**Project Title:**
Up-Down Counter (0-9)

**Development Tools:**

- Quartus Prime Software (Intel FPGA)
- FPGA Board (Cyclone IV, DE1-SoC, or similar)

---

## Project Description

This project is an **Up-Down Counter** that counts between 0 and 9 using **VHDL** and is implemented on an **FPGA**. The counter's direction (up or down) is controlled by an input signal, and it can be reset to zero via a reset input

---

## Features

- **Up and Down Counting**: The counter increments or decrements depending on the control signal.
- **Range**: Counts from 0 to 9 and wraps around when it reaches the limits.
  - Counts up from 0 to 9, then resets to 0.
  - Counts down from 9 to 0, then resets to 9.
- **Clock-driven**: The counter operates on the rising edge of the clock.
- **Reset Functionality**: The counter can be reset to 0 using an external input.
- **Output**: The current count is displayed on a 4-bit output, suitable for connection to a 7-segment display or LEDs.

---

## Requirements

You will need the following to complete the project:

- **Software:**
  - Quartus Prime (for design entry, synthesis, and FPGA programming)
  - ModelSim (for simulation and waveform generation)
- **Hardware:**
  - FPGA Development Board (Cyclone IV, DE1-SoC, or similar)
  - Push-buttons or switches (for control inputs like `clk`, `reset`, and `up_down`)
  - 7-segment display or LEDs (to visualize the count output)
- **Additional Files:**
  - `*.qpf`: Quartus Project File
  - `*.vhd`: VHDL source files
  - `*.vwf`: Vector Waveform File for simulation

---

## RTL Schematic

After compiling the design in **Quartus Prime**, the **RTL Viewer** can be used to inspect the architecture of the counter. This schematic shows the internal components like registers, logic gates, and how they are connected.

Steps to view the RTL:

1. In Quartus Prime, go to **Tools** → **Netlist Viewer** → **RTL Viewer**.
2. The RTL Viewer will display a graphical representation of the counter’s internal design.

---

## Simulation and Verification

### Functional Simulation

To verify the functionality of the counter, you can simulate the design using a **Vector Waveform File (VWF)** in Quartus Prime or use **ModelSim** for more advanced simulations.

#### Generating a VWF:

1. Open Quartus Prime, go to **File** → **New** → **University Program VWF**.
2. Add the input signals (`clk`, `reset`, `up_down`) and output signals (`count_out`) to the waveform.
3. Set up the timing for the clock signal and other control inputs.
4. Run the simulation to observe the counter's behavior over time.

The expected output will show the counter incrementing or decrementing based on the control signal (`up_down`) and resetting correctly when the `reset` signal is applied.

### Example Test Scenario:

- At time `t=0`, the counter is reset (`reset=1`), and `count_out` should be `0000`.
- At time `t=50ns`, the clock pulses, `up_down=1` and `reset=0`, the counter starts counting up: `0001`, `0010`, ..., until it reaches `1001` (decimal 9).
- At time `t=500ns`, change `up_down=0` and observe the counter counting down from 9 to 0.

---

## FPGA Implementation

### Steps for FPGA Synthesis:

1. **Compile the VHDL Code**:

   - In Quartus Prime, go to **Processing** → **Start Compilation**. Ensure there are no errors in the compilation process.

2. **Pin Assignment**:

   - Open the **Pin Planner** tool in Quartus to map the input (`clk`, `reset`, `up_down`) and output (`count_out`) signals to the FPGA’s physical pins.
   - Assign `count_out` to LEDs or a 7-segment display.

3. **Program the FPGA**:

   - Use the **Quartus Programmer** to download the compiled design onto the FPGA board.

4. **Testing on FPGA**:

   - Verify that the counter operates as expected when controlled via physical push-buttons or switches for `up_down` and `reset`.

---

## Conclusion

This **Up-Down Counter** project provides a practical example of designing a basic digital counter in **VHDL** and implementing it on an **FPGA**. The project covers:

- **Design Entry**: Using VHDL for modeling digital logic.
- **Simulation**: Verifying functional behavior with waveform analysis.
- **Synthesis**: Compiling the design for FPGA hardware implementation.
- **Testing**: Observing the correct operation on an FPGA development board.

### Future Enhancements:

- Extend the counter range beyond 0-9.
- Add debounce circuitry to eliminate noise from mechanical buttons.
- Implement additional features such as pause, hold, or synchronous counting.
