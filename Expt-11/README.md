# Experiment 11: Sampling and Reconstruction

## 🎯 Objectives
* To observe the process of sampling a continuous signal using different techniques, specifically Natural and Sample-and-Hold.
* To investigate the reconstruction of a sampled signal using a tuneable low-pass filter.
* To demonstrate the phenomenon of **aliasing** and verify the **Nyquist-Shannon Sampling Theorem**.

---

## 🛠 Materials and Components Used
| Item | Description |
| :--- | :--- |
| **Trainer** | Emona Telecomms-Trainer 101 (plus power-pack) |
| **Oscilloscope** | Dual-channel 20MHz oscilloscope |
| **Modules** | Master Signals, Dual Analog Switch, Speech, Tuneable LPF, VCO |
| **Leads** | BNC-to-banana oscilloscope leads and assorted patch leads |

---

## 🔌 Procedures

### Part A: Sampling a Simple Message
1. Gather the required equipment and ensure the trainer is powered.
2. Connect the $2kHz$ SINE output from the **Master Signals** module to the **IN** socket of the **Dual Analog Switch**.
3. Connect the $8kHz$ DIGITAL output to the **CONTROL** input of the switch.
4. Set the oscilloscope's **Trigger Source** to **CH1** and the **Mode** to **CH1**.
5. View the $2kHz$ SINE output on **CH1** and adjust the **Timebase** to view approximately two cycles.
6. Connect the output of the switch to **CH2** of the scope and switch the scope to **DUAL** mode.
7. Set the **Vertical Attenuation** controls to **1V/div**.
8. **Natural Sampling:** Observe the waveform where the pulses follow the shape of the message signal.
9. **Sample-and-Hold:** Modify the set-up to use the S/H circuit (Figure 4) and observe the resulting waveform.

![Part A Block Diagram](./docs/Part%20A%20Block%20Diagram.png)

### Part B: Sampling Speech
10. Disconnect the plugs from the **Master Signals** $2kHz$ SINE output.
11. Connect the lead to the **Speech** module’s output as shown in Figure 6.
12. Set the oscilloscope **Timebase** to **2ms/div**.
13. Talk, sing, or hum while watching the display to see the sampled representation of a complex signal.

### Part C: Reconstructing a Sampled Message
14. Return the **Timebase** to **0.1ms/div** and reconnect the $2kHz$ SINE message.
15. Set the **Tuneable LPF** module's **Gain** to the middle and turn the **Cut-off Frequency Adjust** fully anti-clockwise.
16. Connect the output of the **Sample-and-Hold** circuit to the **IN** of the **Tuneable LPF**.
17. Slowly turn the **Cut-off Frequency** control clockwise until the $2kHz$ sine wave is reconstructed on the oscilloscope.



### Part D: Investigating Aliasing
18. Locate the **VCO** module, set **Frequency Adjust** fully clockwise, and set **Range** to **LO**.
19. Replace the fixed $8kHz$ control signal with the **VCO** variable frequency output.
20. Monitor the reconstructed signal on **CH2** while slowly decreasing the VCO frequency.
21. Observe the distortion (aliasing) that occurs as the sampling rate drops below the Nyquist rate.

---

## 📉 Results and Discussion
In Part A, the experiment demonstrated that sampling converts a continuous signal into a series of pulses. Natural sampling maintains the original signal's shape during the "on" time, whereas Sample-and-Hold maintains a constant voltage level for the duration of the sample. 

The reconstruction phase in Part C showed that a low-pass filter can successfully recover the original message by rejecting high-frequency sampling components. However, Part D confirmed that if the sampling rate is too low—specifically below the Nyquist rate of $4kHz$ for a $2kHz$ signal—aliasing occurs. This creates frequency components that overlap with the original message, causing irreversible distortion.



---

## ❓ Questions and Answers
**Q: What two features of the sampled signal confirm that the set-up models the sample-and-hold scheme?**
**A:** The sample-and-hold scheme is confirmed by the pulses having a "flat-top" appearance and the signal level being fixed at the instant of measurement rather than following the message shape during the sample period.

**Q: Why is the practical minimum sampling rate slightly higher than the theoretical Nyquist rate?**
**A:** Because real-world filters are not perfect; their rejection of frequencies beyond the cut-off is gradual rather than instantaneous, requiring the sampling frequency to be slightly higher than the Nyquist rate in practice.

---

## 💡 Reflection and Learning Summary
This experiment provided a practical verification of the Nyquist-Shannon sampling theorem. I learned that while theoretical models suggest a minimum sampling rate of $2f_m$, real-world limitations—such as the gradual roll-off of physical filters like the Tuneable LPF—require a "guard band" or a sampling rate slightly higher than the theoretical minimum to ensure clean reconstruction. Observing the visual "shimmer" of aliasing firsthand reinforced why anti-aliasing measures are critical in digital communication systems.
