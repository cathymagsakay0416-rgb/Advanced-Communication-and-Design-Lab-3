# Experiment 12: PCM Encoding

## 🎯 Objectives
* To observe the conversion of an analog message signal into a serial stream of 0s and 1s.
* To investigate the process of **sampling**, **quantisation**, and **encoding** using the Emona Telecoms-Trainer 101.
* To identify the relationship between input analog voltages and their corresponding **8-bit binary numbers**.
* To examine the effect of **quantisation error** and the role of the **Frame Synchronisation (FS)** signal.

---

## 🛠 Materials and Components Used
| Item | Description |
| :--- | :--- |
| **Trainer** | Emona Telecomms-Trainer 101 (plus power-pack) |
| **Oscilloscope** | Dual-channel 20MHz oscilloscope |
| **Modules** | Master Signals, PCM Encoder, Variable DCV, VCO |
| **Leads** | Three scope leads and assorted patch leads |

---

## 🔌 Procedures

### Part A: An introduction to PCM encoding using a static DC voltage
1. Gather a set of the equipment listed above.
2. Set up the scope per the instructions in Experiment 1. Ensure that the **Trigger Source** is set to **CH1** and **Mode** is set to **CH1**.
3. Locate the **PCM Encoder** module and set its **Mode** switch to the **PCM** position.
4. Connect the set-up where the PCM Encoder module is clocked by the Master Signals module’s **8kHz DIGITAL** output and its analog input is connected to **0V DC**.
### Output
![Figure 3](Expt%2012/images/PAGE%2012-5%20FIGURE%203.JPG)
5. Adjust the scope's **Timebase** control to view three pulses of the PCM Encoder module's **FS** output.
6. Set the scope's **Slope** control to the **"-"** position to start the sweep when the FS signal goes from high to low.
7. Adjust the scope’s **Horizontal Position** control so that the start of the trace aligns with the left-most vertical line on the screen.
8. Set the scope's **Timebase** control to the **0.1ms/div** position.
9. Adjust the scope's **Variable Sweep** control until the FS signal matches the required reference.
### Output
![Figure 4](Expt%2012/images/PAGE%2012-6%20FIG%204.JPG)
10. Set the scope's **Mode** control to the **DUAL** position to view the PCM Encoder module’s **CLK** input as well as its **FS** output.
11. Draw the two waveforms to scale, leaving enough room for a third digital signal.
12. Connect the scope's **Channel 2** input to the PCM Encoder module's output.
### Output
![Figure 5](Expt%2012/images/FIGURE%205%20-%20Page%2012-7.jpg)
13. Draw the resulting waveform (10 bits of data) to scale on the graph paper.

### Block Diagram
![Part A Block Diagram](./docs/FIGURE%203%20PAGE%2012-5.JPG)

![Part A 2 Block Diagram](./docs/FIGURE%206%20Page%2012-7.JPG)


### Part B: PCM encoding of a variable DC voltage
14. Set the scope's **Mode** control to the **CH1** position.
15. Set the scope's **Trigger Source** control to the **EXT** position.
16. Set the scope's **Trigger Source Coupling** control to the **HF REJ** position.
17. Modify the set-up to include the **Variable DCV** module to change the DC voltage on the PCM Encoder module's input.
### Output
![Figure 7](Expt%2012/images/FIGURE%207%20-%20Page%2012-10.jpg)
18. Set the scope's **Channel 1 Vertical Attenuation** control to the **1V/div** position.
19. Set the scope's **Channel 1 Input Coupling** control to the **GND** position.
20. Use the scope's **Channel 1 Vertical Position** control to align the trace with a horizontal line (zero volt reference).
21. Set the scope's **Channel 1** and **Channel 2 Input Coupling** controls to the **DC** position.
22. Set the scope's **Mode** control to the **DUAL** position.
23. Adjust the Variable DCV module's **Variable DC** control until the PCM Encoder module outputs the 0V code.
24. Measure the Variable DCV module's output voltage (should be close to 0V).
25. Turn the Variable DCV module's **Variable DC** control clockwise.
26. Continue turning clockwise until the PCM Encoder module's output is **11111111**.
27. Record the input voltage in Table 1.
28. Devise a method (using a Buffer or Adder) to reach the upper and lower limits of the input range if necessary.
29. Adjust the setup for a small negative input voltage.
30. Increase the negative voltage and observe the binary number output.
31. Continue until the output is **00000000**.
32. Measure and record this value in Table 1.

### Output
![Figure 7](Expt%2012/images/FIGURE%207%20-%20Page%2012-10.jpg)
### Block Diagram
![Part B Block Diagram](./docs/FIGURE%208.JPG)

### Part C: Quantisation
33. Return to the basic variable DC setup and set the control to the middle of its travel.
34. Vary the control left and right slightly to observe that the output code remains unchanged until a quantisation threshold is crossed.

### Part D: PCM encoding of continuously changing voltages
35. Return the scope's **Trigger Source** control to **CH1** and **Trigger Source Coupling** to **AC**.
36. Set the scope's **Vertical Attenuation** for both channels to **2V/div**.
37. Locate the **VCO** module and set its **Range** control to the **HI** position.
38. Turn the VCO module's **Frequency Adjust** control fully anti-clockwise (for approx. 50kHz clock).
39. Disassemble the current set-up.
40. Connect the setup where the VCO clocks the PCM Encoder and a sinewave is applied to the input.
41. Set the scope's **Timebase** control to the **50µs/div** position.
### Output
![Figure 9](Expt%2012/images/FIGURE%209%20-%20Page%2012-16.JPG)
42. Watch the PCM Encoder module's **PCM DATA** output change continuously on the scope.
43. Return the scope's **Variable Sweep** control to the locked position.
    
### Output
![Figure 9](Expt%2012/images/FIGURE%209%20-%20Page%2012-16.JPG)
---

## 📉 Results and Discussion

### Table 1: PCM Encoder’s output code vs input voltage
| PCM Encoder's output code | PCM Encoder's input voltage |
| :--- | :--- |
| **11111111** | [Insert Measurement] |
| **00000000** | [Insert Measurement] |

---

## ❓ Questions and Answers

**Question 1: Indicate on your drawing the start and end of the frame.**
**Answer:** The frame starts at the beginning of Bit-7 (MSB) and ends after Bit-0 (LSB).

**Question 2: Indicate on your drawing the start and end of each bit.**
**Answer:** Each bit period is defined by one period of the 8kHz clock signal.

**Question 3: Indicate on your drawing which bit is bit-0 and which is bit-7.**
**Answer:** Bit-7 is transmitted first; Bit-0 is transmitted last and coincides with the FS signal.

**Question 4: What is the binary number that the PCM Encoder module is outputting at 0V?**
**Answer:** Typically 10000000, representing the midpoint of the bipolar range.

**Question 5: Why does the code change even though the input voltage is steady?**
**Answer:** This is caused by analog noise; if the voltage is at a quantisation threshold, noise makes the bit toggle.

**Question 6: Why does the PCM Encoder module output this code for 0V DC and not 00000000?**
**Answer:** Because the system is bipolar; 00000000 is for the most negative voltage, and 0V is the center.

**Question 7: What happens to the Variable DCV module's output?**
**Answer:** The DC voltage level increases.

**Question 8: In what way does the binary number change?**
**Answer:** The binary value increases as the input voltage becomes more positive.

**Question 9: Explain why you were unable to obtain 11111111.**
**Answer:** The Variable DCV's max output may be lower than the encoder's required reference for that code.

**Question 10: Devise a method of obtaining a variable DC voltage that can reach the limits.**
**Answer:** Use an Adder module to add a DC offset or a Buffer with gain to boost the signal.

**Question 11: What happens to the binary number as the size of the negative input voltage increases?**
**Answer:** The binary number decreases toward 00000000.

**Question 12: What is the maximum allowable amplitude (peak-to-peak) for an AC signal?**
**Answer:** Approximately 4Vpp (the difference between the max and min recorded voltages).

**Question 13: What's the name for the difference between a sampled voltage and its closest quantisation level?**
**Answer:** Quantisation Error.

**Question 14: Calculate the difference between the quantisation levels.**
**Answer:** Step Size ($\Delta$) = $(V_{max} - V_{min}) / 256$.

**Question 15: To reduce quantisation error it's better to have:**
**Answer:** [X] **more** quantisation levels between ±2.5V.

**Question 16: Why does the PCM DATA change continuously?**
**Answer:** Because the analog input (sinewave) is constantly changing, each sample taken results in a different binary code.

---

## 💡 Reflection and Learning Summary
In this experiment, I learned that PCM encoding involves more than just sampling; it requires assigning discrete levels via quantisation. By observing the bitstream react to DC and AC signals, I understood how analog signals are accurately represented as serial data frames.
