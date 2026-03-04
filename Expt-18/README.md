# Experiment 18: Quadrature Phase Shift Keying (QPSK)

## 🎯 Objectives
* To generate a Quadrature Phase Shift Keying (QPSK) signal.
* To observe how a serial data stream is split into even and odd bit streams.
* To modulate two orthogonal carriers (I and Q channels) using BPSK.
* To combine two BPSK signals to form a QPSK signal.
* To demodulate QPSK using phase discrimination and a product detector.
* To understand the bandwidth advantage of QPSK over BPSK.

---

## 🛠 Materials and Components Used
| Item | Description |
| :--- | :--- |
| **Trainer** | Emona Telecoms-Trainer 101 (plus power-pack) |
| **Oscilloscope** | Dual-channel 20MHz oscilloscope |
| **Modules** | Master Signals, Sequence Generator, Divider, Serial-to-Parallel Converter, Multiplier (Product Modulator), Adder, Tuneable Low-pass Filter, Phase Shifter, Comparator (Utilities), Variable DCV |
| **Leads** | Three oscilloscope leads and assorted patch leads |

---

## 📘 Preliminary Discussion

Quadrature Phase Shift Keying (QPSK) is an advanced digital modulation technique derived from Binary Phase Shift Keying (BPSK). While BPSK transmits one bit per symbol, QPSK transmits two bits per symbol, effectively doubling data capacity without increasing bandwidth.

In QPSK, the incoming serial data stream is split into two parallel streams: even bits and odd bits. Each stream modulates a carrier of the same frequency, but the carriers are 90° out of phase with each other. These are known as the In-phase (I) and Quadrature (Q) channels. Each channel performs BPSK modulation, and the two resulting signals are added together to produce a single QPSK waveform.

Because two bits are transmitted per symbol, QPSK requires only half the bandwidth of BPSK for the same bit rate. However, proper demodulation requires accurate phase alignment in the receiver to isolate the I and Q components.

---

## 🔌 Procedures

---

### Part A: Generating a QPSK Signal

<img src="./images/FIGURE 2 (3).jpg" width="600" alt="Expt 18 Image Figure 2">

1. Gather a set of the equipment listed above.
2. Set up the scope per the instructions in Experiment 1.
3. Set the scope's **Trigger Source** control to the **EXT** position.
4. Set the scope's **Trigger Source Coupling** control to the **HF REJ** position.
5. Set the scope's **Channel 1** and **Channel 2 Input Coupling** controls to the **DC** position.
6. Set the scope's **Timebase** control to the **0.5ms/div** position.
7. Locate the **Divider** module and set it to divide by 2 (left switch UP, right switch DOWN).
8. Connect the set-up as shown in the lab manual (Serial-to-Parallel configuration).

### Block Diagram
<img src="./docs/FIGURE 4 (5).JPG" width="600" alt="Expt 18 Figure 4">

### Output
<img src="./images/FIGURE 5 (3).jpg" width="600" alt="Expt 18 Image Figure 5">

9. Set the scope’s **Mode** control to the **DUAL** position to view the even and odd bit streams.
10. Compare the signals (Even bits on Ch1, Odd bits on Ch2).
11. Modify the set-up by connecting the **Multiplier** modules for I and Q modulation.

### Block Diagram
<img src="./docs/FIGURE 4 (5).JPG" width="600" alt="Expt 18 Figure 4">

### Output
<img src="./images/FIGURE 5 (3).jpg" width="600" alt="Expt 18 Image Figure 5">

12. Compare the even bits with the Multiplier output (PSK_I).
13. Set the scope’s **Timebase** to **0.2ms/div**.
14. Activate the scope’s **Sweep Magnifier**.
15. Use the **Horizontal Position** control to observe a transition in the data sequence.
16. Examine how the carrier changes at the transition.
17. Deactivate the **Sweep Magnifier**.
18. Move the scope connections to observe the Q-channel output (PSK_Q).

### Block Diagram
<img src="./docs/FIGURE 6 (3).JPG" width="600" alt="Expt 18 Figure 6">

### Output
<img src="./images/FIGURE 7 (4).jpg" width="600" alt="Expt 18 Image Figure 7">

19. Activate the **Sweep Magnifier** and observe a transition.
20. Examine how the quadrature carrier changes.
21. Deactivate the **Sweep Magnifier** and return the timebase to **0.5ms/div**.
22. Modify the set-up by adding the **Adder** module.


### Block Diagram
<img src="./docs/FIGURE 8 (3).JPG" width="600" alt="Expt 18 Figure 8">

### Output
<img src="./images/FIGURE 9 (3).jpg" width="600" alt="Expt 18 Image Figure 9">

23. Turn the Adder’s **g** control fully anti-clockwise.
24. Adjust the **g** control to obtain a 4V p-p output.
25. Disconnect the patch lead to the Adder’s **B** input.
26. Adjust the **G** control to obtain a 4V p-p output.
27. Reconnect the patch lead to the Adder’s **B** input.
28. Set the scope timebase to **0.2ms/div**.
29. Activate the **Sweep Magnifier**.
30. Examine the complete QPSK signal from beginning to end.

---

### Part B: Phase Discrimination (Demodulation)

31. Deactivate the **Sweep Magnifier** and return the timebase to **1ms/div**.
32. Locate the **Tuneable Low-pass Filter** and turn its **Cut-off Frequency Adjust** control fully clockwise.
33. Set the LPF **Gain** control to the middle of its travel.
34. Locate the **Phase Shifter** and set its **Phase Change** control to 0°.
35. Modify the set-up by adding the product detector configuration.
36. Compare the even data bits with the LPF output.

### Block Diagram
<img src="./docs/FIGURE 12 (1).JPG" width="600" alt="Expt 18 Figure 12">



37. Vary the **Phase Adjust** control until a bipolar signal is observed.
38. Set the Phase Shifter to 180° and repeat the observation.
39. Modify the set-up by adding the **Comparator** module.
40. Set the Phase Shifter to 0°.

### Block Diagram
<img src="./docs/FIGURE 14.JPG" width="600" alt="Expt 18 Figure 14">



41. Compare the even data bits with the recovered data.
42. Adjust the **Phase Adjust** control until the even bits are recovered.
43. Move Scope Ch1 to observe the odd bits.
44. Compare the odd bits with the recovered data.
45. Set the Phase Shifter to 180°.
46. Adjust the **Phase Adjust** control until the odd bits are recovered.

---

## ❓ Questions and Answers

**Question 1: What is the relationship between the bit rate of the two digital signals and the Sequence Generator output?**  
**Answer:** The two digital signals (even and odd) each have half the bit rate of the original Sequence Generator output because the data stream is divided into alternating bits.

**Question 2: What feature of the Multiplier output suggests that it is a BPSK signal?**  
**Answer:** The presence of 180° phase reversals in the carrier whenever the digital data changes logic level.

**Question 3: What type of signal is present on the Multiplier output?**  
**Answer:** A BPSK (Binary Phase Shift Keying) signal.

**Question 4: What type of signal is present on the Adder output?**  
**Answer:** A QPSK (Quadrature Phase Shift Keying) signal.

**Question 5: Why is there only one sinewave when the QPSK signal is made up of two BPSK signals?**  
**Answer:** Because adding two sinewaves of the same frequency results in a single sinewave whose amplitude and phase are determined by the vector sum of the two components.

**Question 6: What causes the 3- and 4-level signals out of the LPF during phase adjustments?**  
**Answer:** This occurs when the local carrier is not properly aligned, causing partial detection of both I and Q channels simultaneously (cross-talk).

**Question 7: What is the phase relationship required to recover the even bits?**  
**Answer:** The local carrier must be in-phase (0° or 180°) with the I-channel carrier.

**Question 8: What is the phase relationship required to recover the odd bits?**  
**Answer:** The local carrier must be shifted by 90° relative to the I-channel carrier to align with the Q-channel carrier.

**Question 9: Why is this demodulator only half of a full QPSK receiver?**  
**Answer:** A full QPSK receiver requires two parallel product detectors to simultaneously recover both I and Q channels, whereas this setup recovers only one channel at a time.

---

## 💡 Summary and Reflection

In this experiment, a QPSK signal was generated by splitting a serial digital data stream into two parallel streams and modulating them onto orthogonal carriers. The two BPSK signals were added together to form a single QPSK waveform, demonstrating improved bandwidth efficiency.

Demodulation was achieved using phase discrimination through a product detector and Low-pass Filter. Proper carrier phase alignment was critical to accurately recovering either the even or odd bit stream. This experiment demonstrated the principles of quadrature modulation and highlighted the importance of synchronization in digital communication systems.
