# Experiment 14: Bandwidth Limiting and Restoring Digital Signals

## 🎯 Objectives
* To observe the effect of bandwidth limiting on a PCM communication system.
* To model a communication channel using a low-pass filter.
* To examine the effect of bandwidth limiting on digital signal shape.
* To investigate the effect of increasing bit-rate.
* To restore a bandwidth-limited digital signal using a comparator and observe its limitations.

---

## 🛠 Materials and Components Used
| Item | Description |
| :--- | :--- |
| **Trainer** | Emona Telecoms-Trainer 101 (plus power-pack) |
| **Oscilloscope** | Dual-channel 20MHz oscilloscope |
| **Modules** | Variable DCV, PCM Encoder, PCM Decoder, Tuneable Low-pass Filter, Sequence Generator, VCO, Utilities (Comparator) |
| **Accessories** | Three oscilloscope leads, assorted patch leads, stereo headphones |

---

## 📘 Preliminary Discussion

In the classical communications model, intelligence (the message) moves from a transmitter to a receiver over a channel. A number of transmission media can be used for the channel including: metal conductors (such as twisted-pair or coaxial cable), optical fibre and free-space (what people generally call the "airwaves").

Regardless of the medium used, all channels have a bandwidth. That is, the medium lets a range of signal frequencies pass relatively unaffected while frequencies outside the range are made smaller (or attenuated). In this way, the channel acts like a filter.

This issue has important implications. Recall that the modulated signal in analog modulation schemes (such as AM) consists of many sinewaves. If the medium's bandwidth isn't wide enough, some of the sinewaves are attenuated and others can be completely lost. In both cases, this causes the demodulated signal (the recovered message) to be distorted.

Similarly, recall that digital signals are also made up of many sinewaves (called the fundamental and harmonics). Again, if the medium's bandwidth isn't wide enough, some of them are attenuated and/or lost and this can change the signal's shape.

To illustrate this last point, Figure 1 shows what happens when all but the first two of a squarewave's sinewaves are removed. As you can see, the signal is distorted.

Making matters worse, like a filter the channel shifts the phase of sinewaves by different amounts. Figure 2 shows the signal in Figure 1 but with one of its two sinewaves phase shifted by 40°.

Imagine the difficulty a digital receiver circuit such as a PCM decoder would have trying to interpret the logic level of a signal like Figure 2. Some, and possibly many, of the codes would be misinterpreted and incorrect voltages generated. This makes the recovered message "noisy" which is obviously a problem.

---

## 🔌 Procedures

---

### Part A: The effects of bandwidth limiting on PCM decoding

1. Gather a set of the equipment listed above.
2. Set up the scope per the instructions in Experiment 1.
3. Set the scope's **Mode** control to the **DUAL** position.
4. Set the scope's **Channel 1** and **Channel 2 Input Coupling** controls to the **DC** position.
5. Set the scope's **Channel 1** and **Channel 2 Vertical Attenuation** controls to the **1V/div** position.
6. Locate the **Variable DCV** module and set its **VDC** control to about the middle of its travel.
7. Locate the **PCM Encoder** module and set its **Mode** switch to the **PCM** position.
8. Connect the set-up where the PCM Encoder module’s **PCM DATA** output is connected to the PCM Decoder module’s **PCM DATA** input.

### Block Diagram
<img src="./docs/Figure%204%20(1).JPG" alt="Figure 4: PCM Encoding/Decoding Block Diagram" width="600">

### Ouput
<img src="./images/FIGURE%204.JPG" alt="Figure 4: Initial PCM Setup" width="600">

9. Vary the **Variable DCV** module’s **VDC** control left and right.
10. Locate the **Tuneable Low-pass Filter** module and set its **Gain** control to about the middle of its travel.
11. Turn the **Tuneable Low-pass Filter** module’s **Cut-off Frequency Adjust** control fully clockwise.
12. Modify the set-up so that the low-pass filter is inserted between the PCM Encoder and PCM Decoder.

### Block Diagram
<img src="./docs/Figure%206.JPG" alt="Figure 6: Bandwidth Limited Channel Model" width="600">

### Output
https://github.com/user-attachments/assets/c2059e15-49ad-40dc-b2a1-22fe10070231


13. Vary the **Variable DCV** module’s **VDC** control left and right while slowly turning the **Cut-off Frequency Adjust** control anti-clockwise.
14. Stop turning once the PCM Decoder module’s output becomes corrupted.

---

### Part B: The effects of bandwidth limiting on a digital signal’s shape

15. Completely dismantle the previous set-up.
16. Set the scope's **Mode** control to the **CH1** position.
17. Set the scope's **Trigger Source** control to the **EXT** position.
18. Set the scope's **Trigger Source Coupling** control to the **HF REJ** position.
19. Set the **Tuneable Low-pass Filter** module's **Gain** control to about the middle of its travel.
20. Turn the **Tuneable Low-pass Filter** module's **Cut-off Frequency Adjust** control fully clockwise.
21. Locate the **Sequence Generator** module and set its dip-switches to 00.
22. Connect the set-up where the Sequence Generator output passes through the Tuneable Low-pass Filter.

### Block Diagram
<img src="./docs/Figure%208.JPG" alt="Figure 8: Digital Signal Modeling Diagram" width="600">

### Output
<img src="./images/FIGURE%207.JPG" alt="Figure 7: Sequence Generator Connection" width="600">

23. Set the scope's **Timebase** control to the **1ms/div** position to view about twenty bits of data.
24. Set the scope's **Mode** control to the **DUAL** position and compare the signals.
25. Turn the **Cut-off Frequency Adjust** control anti-clockwise to narrow the bandwidth and observe the signal shape.

---

### Increasing Bit-Rate

26. Turn the **Tuneable Low-pass Filter** module’s **Cut-off Frequency Adjust** control fully clockwise.
27. Turn the **VCO** module’s **Frequency Adjust** control to about a quarter of its travel.
28. Set the **VCO** module’s **Range** control to the **LO** position.
29. Modify the set-up so that the Sequence Generator module’s clock is provided by the VCO module’s **DIGITAL** output.

### Block Diagram
<img src="./docs/Figure%2010.JPG" alt="Figure 10: Variable Bit-Rate Modeling" width="600">

30. If the scope’s display is unstable, adjust the VCO frequency slightly until it settles.
31. Continue turning the **VCO** module’s **Frequency Adjust** control clockwise to increase the transmission bit-rate while observing the scope display.

---

### Part C: Restoring digital signals

32. Set the scope’s **Timebase** control to the **0.5ms/div** position.
33. Set the **Variable DCV** module’s **Variable DC** control to about the middle of its travel.
34. Insert the comparator from the **Utilities** module after the Tuneable Low-pass Filter.

### Block Diagram
<img src="./docs/Figure%2012.JPG" alt="Figure 12: Signal Restoration Block Diagram" width="600">

### Output
<img src="./images/FIGURE 11.jpg" width="600" alt="Expt 14 Figure 11">

35. Compare the original digital signal and the restored digital signal.
36. Slowly turn the **Variable DCV** module’s **DC Voltage** control fully clockwise and fully anti-clockwise and observe the effect.
37. Return the **Variable DCV** control to about the middle of its travel.
38. Slowly narrow the channel’s bandwidth by turning the **Cut-off Frequency Adjust** control anti-clockwise and observe the effect.
39. Turn the **Cut-off Frequency Adjust** control clockwise and stop when the comparator’s output matches the original digital signal (ignoring phase shift).
40. Compare the restored digital signal with the bandwidth-limited digital signal.

---

## ❓ Questions and Answers

**Question 1: Why does bandwidth limiting of the channel cause the PCM Decoder module to output incorrect voltages as well as the correct one?**  
**Answer:** Because bandwidth limiting attenuates higher-frequency harmonics and introduces phase shifts, distorting the digital waveform so the decoder misinterprets logic levels.

---

**Question 2: If this were a communications system transmitting speech, what would these errors sound like when the message is reconstructed?**  
**Answer:** The reconstructed speech would sound noisy, distorted, or contain audible glitches.

---

**Question 3: What two things are happening to cause the digital signal to change shape?**  
**Answer:** Attenuation of higher-frequency harmonics and phase shifting of frequency components.

---

**Question 4: What other change to your communication system distorts the digital signal in the same way as increasing its bit-rate?**  
**Answer:** Reducing the channel bandwidth produces the same distortion effect.

---

**Question 5: Although the restored digital signal is almost identical to the original digital signal, there is a difference. Can you see what it is?**  
**Answer:** There is a phase shift between the original and restored signals.

---

**Question 6: Can this difference be ignored? Why?**  
**Answer:** It may be ignored if logic levels are correct, but excessive phase shift can cause timing errors in digital systems.

---

**Question 7: Why do some DC voltages cause the comparator to output the wrong information?**  
**Answer:** Because the threshold voltage does not match the signal’s switching point, causing incorrect logic detection.

---

**Question 8: Why does the comparator begin to output the wrong information when this control is turned far enough?**  
**Answer:** Because excessive distortion prevents the comparator from correctly detecting signal transitions.

---

## 💡 Reflection and Learning Summary

In this experiment, I observed how bandwidth limiting affects digital communication systems. I learned that digital signals require sufficient harmonic content to preserve their square shape. When bandwidth is restricted or bit-rate increases, distortion occurs due to attenuation and phase shift.

I also learned that comparators can restore distorted digital signals by re-squaring them, but this method has limitations. Excessive distortion and improper threshold settings lead to errors. This demonstrates the importance of adequate bandwidth and proper signal conditioning in communication systems.
