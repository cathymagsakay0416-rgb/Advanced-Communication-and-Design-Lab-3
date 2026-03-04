# Experiment 19: Direct Sequence Spread Spectrum (DSSS) Modulation and Demodulation

---

## 🎯 Objectives

- To generate a Direct Sequence Spread Spectrum (DSSS) signal.
- To understand how a Pseudo-Noise (PN) sequence spreads a message signal.
- To observe the similarity between DSSS and DSBSC modulation.
- To recover a DSSS signal using a synchronized product detector.
- To investigate the effect of incorrect PN synchronization.
- To examine the interference rejection capability of DSSS.

---

## 🛠 Materials and Components Used

| Item | Description |
|------|------------|
| **Trainer** | Emona Telecoms-Trainer 101 (plus power-pack) |
| **Oscilloscope** | Dual-channel 20MHz oscilloscope |
| **Modules** | Master Signals, Sequence Generator, Multiplier (Product Modulator), Adder, Tuneable Low-pass Filter, Speech Module, VCO |
| **Leads** | Two oscilloscope leads and assorted patch leads |

---

## 📘 Preliminary Discussion

Direct Sequence Spread Spectrum (DSSS) is a digital modulation technique in which the transmitted signal occupies a much wider bandwidth than the original message signal.

Unlike conventional modulation, DSSS multiplies the message by a high-frequency **Pseudo-Noise (PN) sequence**. The PN sequence acts as a carrier, rapidly switching polarity and effectively “spreading” the signal energy across a wide frequency band.

Mathematically, DSSS resembles Double Sideband Suppressed Carrier (DSBSC) modulation. However, instead of a sinusoidal carrier, it uses a fast digital code. The spreading process reduces the signal’s power spectral density, often making it appear below the noise floor.

To recover the original message, the receiver must multiply the received signal by an **identical, perfectly synchronized PN sequence**. If the PN code does not match in frequency and phase, the signal cannot be recovered and appears as noise.

This principle provides both **security** and **interference resistance**, forming the basis of spread-spectrum communication systems.

---

## 🔌 Procedures

---

### Part A: Generating a DSSS Signal Using a Simple Message

1. Gather the required equipment.
2. Set up the oscilloscope:
   - Trigger Source → **CH1**
   - Mode → **CH1**
3. Set the scope’s **Trigger Source Coupling** to **HF REJ**.
4. Set the **Sequence Generator** dip-switches to **00**.
5. Connect the setup:
   - 2kHz Sine from **Master Signals** → Multiplier Input A
   - 100kHz Clock to Sequence Generator
   - PN output → Multiplier Input B

### Block Diagram
<img src="./docs/FIGURE 2 (5).JPG" width="600" alt="Expt 19 Figure 2">

### Output
<img src="./images/FIGURE 1 (1).jpg" width="600" alt="Expt 19 Figure 1">

6. Adjust the scope’s **Timebase** to view two cycles of the 2kHz sine wave.
7. Set the scope to **DUAL** mode to observe both the message and DSSS signal.
8. Adjust vertical sensitivity for clear display.
9. Observe and sketch both waveforms.
10. Compare the message waveform with the DSSS signal envelope.

---

### Part B: Generating a DSSS Signal Using Speech

11. Disconnect the 2kHz sine wave input.
12. Connect the **Speech Module** output to the Multiplier input.

### Output
<img src="./images/FIGURE 3 (3).jpg" width="600" alt="Expt 19 Figure 3">

13. Set the scope’s **Timebase** to **2ms/div**.
14. Speak or sing into the Speech module microphone.
15. Observe the spread-spectrum waveform.

---

### Part C: Recovering the Message Using a Product Detector

16. Connect the DSSS output to a second **Multiplier** (Product Detector).
17. “Steal” the same PN sequence from the transmitter and connect it to the second Multiplier.
18. Connect the Multiplier output to the **Tuneable Low-pass Filter**.

### Block Diagram
<img src="./docs/FIGURE 5 (4).JPG" width="600" alt="Expt 19 Figure 5">

<img src="./docs/FIGURE 6 (4).JPG" width="600" alt="Expt 19 Figure 6">

### Output
<img src="./images/FIGURE 4 (6).JPG" width="600" alt="Expt 19

19. Adjust the LPF cut-off frequency and gain.
20. Observe the recovered signal on the oscilloscope.

21. Replace the receiver PN sequence with a different sequence.
22. Observe the LPF output again.

### Output
<img src="./images/FIGURE 7 (5).JPG" width="600" alt="Expt 19 Figure 7">
---

### Part D: DSSS and Deliberate Interference (Jamming)

23. Add a **VCO** output to the DSSS signal using an **Adder** module.
24. Adjust the VCO frequency to act as a narrowband jammer.
25. Increase the jammer amplitude.
26. Observe the combined signal.
27. Pass the composite signal through the product detector and LPF.
28. Observe the recovered message.
29. Vary the jammer frequency and amplitude.
30. Examine the effect on the recovered signal.

### Block Diagram
<img src="./docs/FIGURE 9 (4).JPG" width="600" alt="Expt 19 Figure 9">

### Output
<img src="./images/FIGURE 10 (2).JPG" width="600" alt="Expt 19 Figure 10">
<img src="./images/FIGURE 11 (1).JPG" width="600" alt="Expt 19 Figure 11">
---

## ❓ Questions and Answers

### Question 1:
What feature of the Multiplier output suggests that it is basically a DSBSC signal?

**Answer:**  
The output shows phase reversals corresponding to the PN sequence transitions. The signal’s envelope follows the message waveform, which is characteristic of DSBSC modulation.

---

### Question 2:
Why is the DSSS signal large on the oscilloscope when it is supposed to be small and noise-like?

**Answer:**  
In the lab, the signal is observed directly in the time domain before transmission losses. In real communication systems, the signal power is spread across a wide bandwidth, reducing its power spectral density and making it appear noise-like.

---

### Question 3:
Why isn’t there any output from the DSSS modulator when you are not speaking?

**Answer:**  
The Multiplier performs mathematical multiplication:

```
0 × PN = 0
```

If the message amplitude is zero, no output signal is produced.

---

### Question 4:
What does the signal out of the Low-pass Filter look like when the correct PN sequence is used?

**Answer:**  
It resembles the original message (2kHz sine or speech), possibly with slight attenuation or filtering effects.

---

### Question 5:
Why does using the wrong PN sequence produce noise at the output?

**Answer:**  
DSSS relies on correlation. Using a mismatched PN sequence does not despread the signal; instead, it spreads it further. The Low-pass Filter then sees only random high-frequency components, resulting in noise.

---

### Question 6:
Why doesn’t the jamming signal prevent recovery of the message?

**Answer:**  
When multiplied by the correct PN sequence, the DSSS signal is despread back to its narrow bandwidth. The jammer, however, is spread across a wide bandwidth by this multiplication. The Low-pass Filter passes the narrowband message while rejecting the spread jammer, demonstrating processing gain.

---

## 💡 Summary and Reflection

In this experiment, a DSSS signal was generated by multiplying a message signal with a high-frequency Pseudo-Noise sequence. This spreading process distributed the signal energy across a wide bandwidth, making it appear noise-like and difficult to detect.

Message recovery required a synchronized product detector using an identical PN sequence. When synchronization was correct, the original message was successfully reconstructed. When incorrect, the output appeared as noise.

The experiment also demonstrated DSSS’s strong resistance to interference. Even with a high-amplitude jamming signal present, the despreading process effectively suppressed the jammer while recovering the message.

This lab clearly illustrated how spread-spectrum techniques provide security, interference rejection, and robustness in modern wireless communication systems.
