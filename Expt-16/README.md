# Experiment 16: Frequency Shift Keying (FSK)

## 🎯 Objectives
* To generate a Frequency Shift Keying (FSK) signal using a VCO.
* To observe the relationship between a digital signal and its FSK-modulated carrier.
* To demodulate an FSK signal using a tuneable low-pass filter and envelope detector.
* To restore a recovered digital signal using a comparator.
* To understand the concepts of Mark and Space frequencies.

---

## 🛠 Materials and Components Used
| Item | Description |
| :--- | :--- |
| **Trainer** | Emona Telecoms-Trainer 101 (plus power-pack) |
| **Oscilloscope** | Dual-channel 20MHz oscilloscope |
| **Modules** | Master Signals, Sequence Generator, VCO, Tuneable Low-pass Filter, Rectifier, Comparator (Utilities), Variable DCV |
| **Leads** | Three oscilloscope leads and assorted patch leads |

---

## 📘 Preliminary Discussion

Frequency Shift Keying (FSK) is a digital modulation technique in which digital information is transmitted by shifting the frequency of a carrier signal between two discrete values. Unlike Amplitude Shift Keying (ASK), where amplitude changes represent binary data, FSK encodes information by varying the carrier frequency.

In FSK systems, the frequency corresponding to logic-1 is called the **Mark frequency**, while the frequency corresponding to logic-0 is called the **Space frequency**. Typically, the Mark frequency is higher than the nominal carrier frequency, and the Space frequency is lower. These two frequencies alternate according to the digital data sequence.

FSK is highly resistant to noise because most noise affects amplitude rather than frequency. During demodulation, one frequency can be isolated using filtering, and the resulting signal can then be processed using an envelope detector and comparator to recover the original digital data.

---

## 🔌 Procedures

---

### Part A: Generating an FSK Signal

1. Gather a set of the equipment listed above.
2. Set up the scope per the instructions in Experiment 1.
3. Set the scope's **Trigger Source** control to the **EXT** position.
4. Set the scope's **Trigger Source Coupling** control to the **HF REJ** position.
5. Set the scope's **Channel 1** and **Channel 2 Input Coupling** controls to the **DC** position.
6. Set the **VCO Gain** control to about half of its travel.
7. Set the **VCO Frequency Adjust** control to about the 9 o’clock position.
8. Set the VCO module's **Range** control to the **LO** position.
9. Set the Sequence Generator dip-switches to **00** (both up).
10. Connect the set-up so that:
   - The Sequence Generator **SYNC** output connects to the Scope **EXT** trigger.
   - The Sequence Generator **OUT** connects to the **VCO IN**.
   - The **VCO OUT** connects to Scope **Channel 2**.

### Block Diagram
<img src="./docs/FIGURE 3.JPG" width="600" alt="Expt 15 Figure 3">

### Output
<img src="./images/FIGURE 2.JPG" width="600" alt="Expt 15 Figure 2">

11. Set the scope’s **Timebase** control to **0.5ms/div**.
12. Set the scope’s **Mode** control to the **DUAL** position to view both the digital signal and the FSK signal.
13. Compare the signals and observe how the carrier frequency shifts according to the digital data.

---

### Part B: Demodulating an FSK Signal

14. Turn the VCO’s **Frequency Adjust** control to approximately the 2 o’clock position.
15. Turn the Tuneable Low-pass Filter module’s **Cut-off Frequency Adjust** control fully clockwise.
16. Turn the Tuneable Low-pass Filter module’s **Gain** control fully clockwise.
17. Modify the set-up by routing the **VCO OUT** through the **Tuneable Low-pass Filter**.

### Block Diagram
<img src="./docs/FIGURE 5.JPG" width="600" alt="Expt 15 Figure 5">

### Output
<img src="./images/FIGURE 4 (2).JPG" width="600" alt="Expt 15 Figure 4">

18. Slowly turn the LPF **Cut-off Frequency Adjust** control counter-clockwise until the higher frequency component of the FSK signal is suppressed.
19. Compare the original digital signal with the filter’s output.
20. Modify the set-up by adding the **Rectifier** after the filter to form an envelope detector.
21. Connect Scope **Channel 2** to the envelope detector output.

### Block Diagram
<img src="./docs/FIGURE 7 (1).JPG" width="600" alt="Expt 15 Figure 7">

### Output
<img src="./images/FIGURE 6 (1).JPG" width="600" alt="Expt 15 Figure 6">

22. Compare the original digital signal with the recovered signal.

---

### Part C: Restoring the Recovered Digital Signal Using a Comparator

23. Modify the set-up by connecting the envelope detector output to the **Comparator IN**.

### Block Diagram
<img src="./docs/FIGURE 9.JPG" width="600" alt="Expt 15 Figure 9">

### Output
<img src="./images/FIGURE 8 (1).jpg" width="600" alt="Expt 15 Figure 8">

24. Observe and note the amplitude of the filtered signal (varies between 0V and a maximum value).
25. Set the **Variable DCV** module’s output to approximately half of the maximum amplitude noted in step 24 and connect it to the **Comparator REF** input.
26. Compare the original digital signal with the recovered digital signal from the Comparator output.

---

## ❓ Questions and Answers

**Question 1: What’s the name for the VCO output frequency that corresponds with logic-1s in the digital data?**  
**Answer:** The Mark frequency.

**Question 2: What’s the name for the VCO output frequency that corresponds with logic-0s in the digital data?**  
**Answer:** The Space frequency.

**Question 3: Based on your observations of the FSK signal, which of the two is the higher frequency? Explain your answer.**  
**Answer:** The Mark frequency is typically the higher frequency. On the oscilloscope, the waveform corresponding to logic-1 appears with cycles that are closer together, indicating a higher frequency.

**Question 4: Which of the FSK signal’s two sinewaves is the filter picking out?**  
**Answer:** The filter picks out the Space frequency (the lower frequency) by attenuating the higher frequency component.

**Question 5: What does the filtered FSK signal look like?**  
**Answer:** It appears as bursts of sinewaves during logic-0 intervals, separated by near-zero voltage during logic-1 intervals where the higher frequency has been filtered out.

**Question 6: What can be used to “clean-up” the recovered digital signal?**  
**Answer:** A comparator circuit (or Schmitt trigger).

**Question 7: How does the comparator turn the slow rising voltages of the recovered digital signal into sharp transitions?**  
**Answer:** The comparator compares the input signal to a fixed reference voltage. When the input exceeds the reference, the output switches to its maximum level; when it falls below the reference, the output switches to minimum level. This produces sharp digital transitions.

---

## 💡 Summary and Reflection

In this experiment, an FSK signal was generated by using a digital sequence to control a Voltage Controlled Oscillator (VCO), causing the carrier frequency to shift between Mark and Space frequencies. The relationship between digital data and frequency variation was observed on the oscilloscope.

The FSK signal was demodulated by filtering out one frequency component and applying envelope detection. Although the recovered waveform showed gradual transitions, the comparator successfully restored the sharp edges required for digital processing. This experiment demonstrated how digital information can be transmitted using frequency modulation and reliably reconstructed at the receiver.
