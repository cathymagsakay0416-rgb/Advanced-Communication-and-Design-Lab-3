# Experiment 20: Undersampling in SDR (Software Defined Radio)

---

## 🎯 Objectives

- To generate a bandwidth-limited DSBSC signal.
- To understand the concept of undersampling (band-pass sampling).
- To observe how aliasing can be used for direct down-conversion.
- To recover a baseband message using a Sample-and-Hold and Low-pass Filter.
- To investigate the importance of synchronization in SDR systems.
- To understand how harmonics of the sampling clock can act as a local oscillator.

---

## 🛠 Materials and Components Used

| Item | Description |
|------|------------|
| **Trainer** | Emona Telecoms-Trainer 101 (plus power-pack) |
| **Oscilloscope** | Dual-channel 20MHz oscilloscope |
| **Modules** | Master Signals, Multiplier, Sample-and-Hold, Tuneable Low-pass Filter, VCO |
| **Leads** | Two oscilloscope leads and assorted patch leads |

---

## 📘 Preliminary Discussion

Modern communication systems have evolved from hardware-specific radios to flexible **Software Defined Radio (SDR)** architectures.

Traditional radios require dedicated hardware for each modulation scheme. In contrast, SDR converts radio frequency (RF) signals into digital form as early as possible, allowing software to perform demodulation and processing.

A major challenge in SDR is the requirement of high-speed Analog-to-Digital Converters (ADCs). According to the Nyquist theorem, sampling must occur at least twice the highest frequency present in the signal. For high RF carriers, this would require extremely fast and expensive ADCs.

Undersampling (also known as band-pass sampling) provides a solution. If a signal is narrow-band, it can be sampled at a rate related to its **bandwidth**, not its carrier frequency. The sampling process produces aliases of the signal spectrum. By carefully choosing the sampling frequency, one of these aliases appears at baseband (near DC), effectively performing frequency down-conversion without a traditional hardware mixer.

This experiment demonstrates how aliasing can intentionally be used as a tool for direct conversion in SDR systems.

---

## 🔌 Procedures

---

### Part A: Setting Up a Bandwidth-Limited Signal

1. Gather the required equipment.
2. Set up the oscilloscope:
   - Trigger Source → **CH1 (or INT)**
   - Mode → **CH1**
3. Connect the setup:
   - 2kHz Sine (Message) → Multiplier Y input
   - 100kHz Cosine (Carrier) → Multiplier X input

### Block Diagram
<img src="./docs/FIGURE 2 (7).JPG" width="600" alt="Expt 20 Figure 2">

### Output
<img src="./images/FIGURE 2 (6).JPG" width="600" alt="Expt 20 Figure 2">

4. Adjust the scope’s **Timebase** to view two cycles of the 2kHz sine wave.
5. Set scope Mode to **DUAL**.
6. Set:
   - Channel 1 Attenuation → **1V/div**
   - Channel 2 Attenuation → **2V/div**
7. Observe the DSBSC signal output from the Multiplier.

---

### Part B: Direct Down-Conversion Using Undersampling

8. Return Scope Channel B scale to **0.5V/div**.
9. Modify the setup by adding the **Sample-and-Hold (S/H)** module.

### Block Diagram
<img src="./docs/FIGURE 4 (7).JPG" width="600" alt="Expt 20 Figure 4">

### Output
<img src="./images/FIGURE 3 (4).JPG" width="600" alt="Expt 20 Figure 3">

10. Trigger the S/H using an **8kHz clock** from Master Signals.


### Output
<img src="./images/FIGURE 5 (5).JPG" width="600" alt="Expt 20 Figure 5">

11. Compare the undersampled DSBSC signal with the original message.
12. Modify the setup by connecting the S/H output to the **Tuneable Low-pass Filter (LPF)**.
13. Observe the LPF output and compare it with the original 2kHz sine wave.

---

### Part C: Synchronization

14. Locate the **VCO** module and set its Range to **LO**.
15. Set the **Frequency Adjust** control to mid-position.
16. Connect Scope CH1 to the VCO **Digital Output**.
17. Adjust the VCO frequency to **8.333kHz** (Period ≈ 120µs).
18. Return Scope CH1 to the 2kHz sine output.
19. Adjust the timebase to view 2–3 cycles of both original and recovered signals.

### Output
<img src="./images/FIGURE 6 (5).JPG" width="600" alt="Expt 20 Figure 6">

20. Disconnect the 8kHz clock from Master Signals.
21. Use the VCO Digital Output as the new S/H clock source.
22. Observe the effect on the recovered message.
23. Attempt to correct frequency error by adjusting the VCO Frequency control.

---

## ❓ Questions and Answers

### Question 1:
For the given inputs to the Multiplier module, what are the frequencies of the two sinewaves that make up the DSBSC signal?

**Answer:**

The DSBSC output contains the sum and difference frequencies:

```
f1 = fc - fm = 100 kHz - 2 kHz = 98 kHz
f2 = fc + fm = 100 kHz + 2 kHz = 102 kHz
```

---

### Question 2:
What is the bandwidth of the DSBSC signal?

**Answer:**

```
BW = 102 kHz - 98 kHz = 4 kHz
```

Alternatively:

```
BW = 2 × fm = 2 × 2 kHz = 4 kHz
```

---

### Question 3:
What is the significance of the signal at the Baseband LPF output?

**Answer:**

It is the recovered message signal. The LPF removes high-frequency aliases generated during sampling, leaving only the baseband component, which matches the original 2kHz sine wave.

---

### Question 4:
Given the sampling frequency is 8.333kHz, which harmonic in the sampling signal demodulates the DSBSC signal?

**Answer:**

The 12th harmonic:

```
12 × 8.333 kHz ≈ 100 kHz
```

Since this harmonic equals the carrier frequency, it acts as a virtual local oscillator for demodulation.

---

### Question 5:
Why doesn’t adjusting the VCO solve the instability problem and allow stable recovery?

**Answer:**

Because the VCO is not phase-locked to the transmitter carrier. Even a small frequency mismatch causes a beat frequency between the carrier and the sampling harmonic, producing amplitude variations (“rolling”) in the recovered signal. Without synchronization (e.g., a Phase-Locked Loop), the two oscillators cannot remain in phase.

---

## 💡 Summary and Reflection

In this experiment, a DSBSC signal centered at 100kHz was undersampled using an 8kHz sampling clock. By selecting a sampling frequency whose harmonic matched the carrier frequency, the signal was effectively down-converted to baseband without a conventional mixer.

The Low-pass Filter successfully recovered the original 2kHz message signal. This demonstrated that aliasing—normally considered undesirable—can be intentionally exploited in SDR systems for direct conversion.

However, the experiment also highlighted the critical importance of synchronization. Without a shared clock or phase-locked system, even slight frequency differences cause instability in the recovered signal.

This lab clearly illustrates that modern SDR systems rely more on mathematical signal processing and clever sampling strategies than on complex analog hardware.
