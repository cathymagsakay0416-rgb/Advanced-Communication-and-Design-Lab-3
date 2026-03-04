# Experiment 13: PCM Decoding

## 🎯 Objectives
* To observe the process of converting a PCM data stream back into a Pulse Amplitude Modulation (PAM) signal.
* To understand the critical role of **clock and frame synchronization** in digital decoding.
* To reconstruct original message and speech signals using a tuneable low-pass filter.

---

## 📖 Preliminary Discussion
The previous experiment introduced the basics of pulse code modulation (PCM) which works with 8-bit binary numbers. For numbers in between, the output is a proportional voltage between $\pm 2\text{V}$. For example, the number $10000000$ is halfway between $00000000$ and $11111111$; for this input, the module outputs $0\text{V}$.

### The Decoding Process
At its simplest, decoding involves:
1. Identifying each new frame in the data stream.
2. Extracting the binary numbers from each frame.
3. Generating a voltage that is proportional to the binary number.
4. Holding the voltage on the output until the next frame has been decoded (forming a **PAM** version of the original message signal).
5. Reconstructing the message by passing the PAM signal through a low-pass filter.



### Synchronization and TIMS PCM Decoder
The PCM decoder's clock frequency is crucial. If it is not the same as the encoder's clock, bits are read twice or missed, causing incorrect interpretation and audible errors. The decoder must also detect the beginning of each frame. The **TIMS PCM Decoder** module is not self-clocking and cannot self-detect frames; therefore, its clock and Frame Synchronization (FS) signals must be **"stolen"** from the encoder.

---

## 🛠 Materials and Components Used
| Item | Description |
| :--- | :--- |
| **Trainer** | Emona Telecomms-Trainer 101 (plus power-pack) |
| **Oscilloscope** | Dual-channel 20MHz oscilloscope |
| **Modules** | PCM Encoder, PCM Decoder, Tuneable LPF, Buffer, VCO, Speech, Variable DCV |
| **Leads** | BNC-to-banana oscilloscope leads and assorted patch leads |

---

## 🔌 Procedures

### Part A - Setting up the PCM Encoder
1. Gather a set of the equipment listed.
2. Set up the scope per Experiment 1. Ensure **Trigger Source** is CH1 and **Mode** is CH1.
3. Locate the **PCM Encoder** module and set its **Mode** switch to the **PCM** position.
4. Connect the set-up shown in Figure 1. (Note: Insert black plugs into GND).
### Block Diagram
<img src="./docs/FIGURE 2.JPG" width="500" alt="PCM Encoder Block Diagram">

### Output
<img src="./images/FIGURE 1 - Page 13-14.jpg" width="600" alt="Part A Setup">
5. Set the scope's **Slope** control to the "-" position.
6. Adjust the scope's **Timebase** control to view one pulse of the PCM Encoder module's **FS** output (Tip: $10\mu\text{s/div}$).
7. Set the **Variable DCV** module's **Variable DC** control to about the middle of its travel.
8. Set the scope's **Mode** control to the **DUAL** position to view the PCM Encoder module's **PCM DATA** output as well as its **FS** output.
9. Vary the **Variable DCV** module's **Variable DC** control left and right.
10. Confirm the number on PCM DATA output goes down and up.
11. Disconnect the plug to the Variable DCV module's **VDC** output.
12. Locate the **VCO** module and turn its **Frequency Adjust** control fully anti-clockwise.
13. Set the VCO module's **Range** control to the **LO** position.

### Block Diagram
<img src="./docs/FIGURE 4.JPG" width="500" alt="Sine Input Block Diagram">

### Output
<img src="./images/FIGURE 3 - Page 13-6.jpg" width="600" alt="VCO Connection Setup">

### Part B - Decoding the PCM Data
14. Return the scope's **Slope** control to the "+" position.
15. Set the scope's **Mode** control to **CH1** position.
16. Modify the set-up as shown in Figure 5.
### Block Diagram
<img src="./docs/FIGURE 6.JPG" width="500" alt="Full System Block Diagram">

### Output
<img src="./images/FIGURE 5 PAGE 13-7.jpg" width="600" alt="Decoder Setup">

17. Adjust the scope's **Timebase** control to view two or so cycles of the message.
18. Set the scope's **Mode** control to the **DUAL** position to view the PCM Decoder module's output as well as the message signal.
19. Add the **Buffer** module to the set-up as shown in Figure 7 leaving scope connections as they are.
20. Turn the Buffer module's **Gain** control fully anti-clockwise.
21. Without wearing headphones, plug them into the Buffer module's headphone socket.
22. Put the headphones on.
23. Turn the Buffer module's **Gain** control clockwise until you can comfortably hear the PCM Decoder module's output.
24. Disconnect the Buffer module's lead where it plugs to the PCM Decoder module's output.
25. Modify the set-up as shown in Figure 8 below, again leaving the scope's connections as they are.
26. Compare the sound of the two signals. You should notice that they're similar but clearly different.

### Part C - Encoding and Decoding Speech
27. Completely remove the **Buffer** module from the set-up.
28. Disconnect the plugs to the **VCO** module's **SINE** output.
29. Modify the set-up as shown in Figure 9.
30. Talk, sing or hum while watching the scope's display.

### Part D - Recovering the Message
31. Locate the **Tuneable Low-pass Filter** module and set its **Gain** control to about the middle.
32. Turn the Tuneable Low-pass Filter module's **Cut-off Frequency Adjust** control fully anti-clockwise.
33. Disconnect the plugs to the **Speech** module's output.
34. Modify the set-up as shown in Figure 10.
### BLock Diagram
<img src="./docs/FIGURE 11.JPG" width="500" alt="Reconstruction Block Diagram">
35. Slowly turn the **Cut-off Frequency** control clockwise and stop the moment the message signal has been reconstructed (ignoring phase shift).
36. Add the **Buffer** module as shown in Figure 12.
37. Turn the Buffer module's **Gain** control fully anti-clockwise.
38. Put the headphones on.
39. Turn the Buffer module's **Gain** control clockwise until you can hear the filter output.
40. Disconnect the Buffer lead from the PCM Decoder and connect it to the **VCO** output.
41. Compare the sound of the two signals; they should be very similar.

---

## 📉 Results and Discussion

### Waveform Analysis
The experiment confirmed that the raw output of a PCM decoder is a "staircase" **PAM waveform**. The high-frequency "steps" represent the sampling intervals. By "stealing" the Clock and Frame Sync from the transmitter, the receiver stayed in perfect alignment. The final reconstruction stage using the **Tuneable LPF** proved essential for smoothing the signal back into a recognizable analog form.



---

## ❓ Questions and Answers

**Q: What does the PCM Decoder's "stepped" output tell you about the type of signal that it is?**
**A:** It indicates the signal is a **Pulse Amplitude Modulation (PAM)** signal. The "steps" show that the decoder is holding a specific voltage level for the duration of one frame before jumping to the next sampled value.

**Q: What must be done to the PCM Decoder module's output to reconstruct the message properly?**
**A:** It must be passed through a **Low-pass Filter**. This filter removes the high-frequency transitions (the steps) and recovers the original smooth analog waveform.

**Q: Even though the two signals look and sound the same, why isn't the reconstructed message a perfect copy of the original message?**
**A:** This is due to **Quantization Error**. Because an 8-bit system only has 256 discrete levels to represent an infinite range of analog voltages, there is a small rounding difference (quantization noise) between the original signal and its digital representation.

---

## 💡 Reflection and Learning Summary
This lab effectively demonstrated the transition from digital data back to analog reality. The most significant takeaway was the absolute necessity of bit and frame synchronization; without them, the data is just noise. It also highlighted how bit-depth (8-bit) limits the resolution of our reconstructed signal, reinforcing the importance of quantization theory in digital communications.
