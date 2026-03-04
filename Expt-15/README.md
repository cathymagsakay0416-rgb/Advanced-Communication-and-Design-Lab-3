```markdown
# Experiment 15: Amplitude Shift Keying (ASK)

## 🎯 Objectives
* To generate an Amplitude Shift Keying (ASK) signal.
* To observe the relationship between a digital signal and its ASK-modulated carrier.
* To demodulate an ASK signal using an envelope detector.
* To restore a recovered digital signal using a comparator.
* To understand the principles of On-Off Keying (OOK).

---

## 🛠 Materials and Components Used
| Item | Description |
| :--- | :--- |
| **Trainer** | Emona Telecoms-Trainer 101 (plus power-pack) |
| **Oscilloscope** | Dual-channel 20MHz oscilloscope |
| **Modules** | Master Signals, Sequence Generator, Dual Analog Switch, VCO, Rectifier, Tuneable Low-pass Filter, Comparator (Utilities), Variable DCV |
| **Leads** | Three oscilloscope leads and assorted patch leads |

---

## 📘 Preliminary Discussion

In telecommunications systems, physical transmission media are limited resources. Because of this, multiple users must share a single channel. Two common methods are **Time Division Multiplexing (TDM)**, where users transmit in separate time slots, and **Frequency Division Multiplexing (FDM)**, where users transmit simultaneously at different carrier frequencies.

Amplitude Shift Keying (ASK) is a digital modulation technique that allows digital data to be transmitted over a bandpass channel. ASK works by switching a carrier wave on and off according to the digital data stream. When the digital signal is logic high (1), the carrier is transmitted. When the digital signal is logic low (0), the carrier is suppressed.

Because the carrier is either present or absent, ASK is also called **On-Off Keying (OOK)**. This experiment demonstrates how an ASK signal is generated, demodulated using an envelope detector, and restored using a comparator.

---

## 🔌 Procedures

---

### Part A: Generating an ASK Signal

1. Gather a set of the equipment listed above.
2. Set up the scope per the instructions in Experiment 1.
3. Set the scope's **Trigger Source** control to the **EXT** position.
4. Set the scope's **Trigger Source Coupling** control to the **HF REJ** position.
5. Set the scope's **Channel 1** and **Channel 2 Input Coupling** controls to the **DC** position.
6. Set the scope's **Timebase** control to the **1ms/div** position.
7. Connect the set-up where the Master Signals module’s **2kHz Digital** output clocks the Sequence Generator and the **2kHz Sine** output is connected to the Dual Analog Switch module.

### Block Diagram
<img src="./docs/FIGURE 3.JPG" width="600" alt="ASK Generation Block Diagram">

### Output
<img src="./images/FIGURE 2.JPG" width="600" alt="Initial ASK Generator Wiring">

8. Set the scope's **Mode** control to the **DUAL** position to view the Sequence Generator output and the ASK signal from the Dual Analog Switch module.
9. Compare the signals.
10. Locate the **VCO** module and set its **Frequency Adjust** control to about the middle of its travel.
11. Set the VCO module's **Range** control to the **HI** position.
12. Modify the set-up by replacing the 2kHz sine carrier with the VCO’s high-frequency carrier (approximately 100kHz).

### Block Diagram
<img src="./docs/FIGURE 5.JPG" width="600" alt="ASK Generation with VCO Block Diagram">

### Output
<img src="./images/FIGURE 4 (2).JPG" width="600" alt="VCO Carrier Connection Setup">

13. Compare the signals.
14. Use the scope's **Channel 1 Vertical Position** control to overlay the digital signal with the ASK signal’s envelopes and compare them.

---

### Part B: Demodulating an ASK Signal Using an Envelope Detector

15. Locate the **Tuneable Low-pass Filter** module and turn its **Gain** control fully clockwise.
16. Turn the Tuneable Low-pass Filter module's **Cut-off Frequency Adjust** control fully clockwise.
17. Modify the set-up by adding the **Rectifier** followed by the **Low-pass Filter** to form an envelope detector.

### Block Diagram
<img src="./docs/FIGURE 7 (1).JPG" width="600" alt="Envelope Detection Block Diagram">

### Output
<img src="./images/FIGURE 6 (1).JPG" width="600" alt="Demodulator and Filter Wiring">

18. Compare the original digital signal with the recovered digital signal.

---

### Part C: Restoring the Recovered Digital Signal Using a Comparator

19. Modify the set-up by connecting the filter output to the **Comparator** module.

### Block Diagram
<img src="./docs/FIGURE 9.JPG" width="600" alt="Full ASK Restoration Block Diagram">

### Output
<img src="./images/FIGURE 8 (1).jpg" width="600" alt="Final Comparator Restoration Setup">

20. Set the **Variable DCV** module's **Variable DC** control to about the middle of its travel.
21. Compare the signals. If they are not the same, vary the Variable DCV module's **Variable DC** control until they match.

---

## ❓ Questions and Answers

**Question 1: What is the relationship between the digital signal and the presence of the carrier in the ASK signal?**  
**Answer:** The carrier is transmitted when the digital signal is logic high (1) and is suppressed when the digital signal is logic low (0).

**Question 2: What is the ASK signal’s voltage when the digital signal is logic-0?**  
**Answer:** Approximately 0V (zero amplitude).

**Question 3: What feature of the ASK signal suggests that it’s an AM signal?**  
**Answer:** The amplitude of the carrier wave changes according to the digital signal; the envelope of the carrier follows the digital data pattern.


**Question 4: Why is the recovered digital signal not a perfect copy of the original?**  
**Answer:** The low-pass filter cannot pass all high-frequency components of the square wave, resulting in rounded edges and slight distortion.


**Question 5: What can be used to “clean-up” the recovered digital signal?**  
**Answer:** A comparator circuit.


**Question 6: How does the comparator turn the slow rising voltages of the recovered digital signal into sharp transitions?**  
**Answer:** The comparator compares the signal to a reference threshold. If the input exceeds the threshold, it outputs a maximum voltage; if it is below, it outputs minimum voltage. This clipping action produces sharp transitions and restores the square wave shape.


## 💡 Summary and Reflection

In this experiment, an ASK signal was generated by gating a high-frequency carrier with a digital data stream. The presence and absence of the carrier represented logic 1 and logic 0, respectively. The ASK signal was then demodulated using an envelope detector composed of a rectifier and low-pass filter.

Although the recovered digital signal exhibited distortion due to filtering limitations, the comparator successfully restored the signal by acting as a decision threshold device. This experiment demonstrated how digital signals can be transmitted over analog channels and reliably reconstructed, highlighting the robustness of digital communication systems.
```

