# Experiment 17: Binary Phase Shift Keying (BPSK)

## 🎯 Objectives
* To generate a Binary Phase Shift Keying (BPSK) signal.
* To observe the 180° phase reversal corresponding to digital logic transitions.
* To demodulate a BPSK signal using a product detector.
* To restore the recovered digital signal using a comparator.
* To understand the relationship between BPSK and DSBSC modulation.

---

## 🛠 Materials and Components Used
| Item | Description |
| :--- | :--- |
| **Trainer** | Emona Telecoms-Trainer 101 (plus power-pack) |
| **Oscilloscope** | Dual-channel 20MHz oscilloscope |
| **Modules** | Master Signals, Sequence Generator, Multiplier (Product Modulator), Tuneable Low-pass Filter, Comparator (Utilities), Variable DCV |
| **Leads** | Three oscilloscope leads and assorted patch leads |

---

## 📘 Preliminary Discussion

Binary Phase Shift Keying (BPSK) is a digital modulation technique in which digital data is transmitted by changing the phase of a carrier signal. Unlike ASK and FSK, which vary amplitude and frequency respectively, BPSK varies the carrier’s phase to represent binary information.

In BPSK, a logic transition causes the carrier to shift phase by 180°. When the digital data changes state, the sine wave effectively inverts, starting at the opposite polarity. A logic-1 may correspond to a sine wave beginning at a positive peak, while a logic-0 begins at a negative peak.

Mathematically, BPSK is equivalent to Double-Sideband Suppressed Carrier (DSBSC) modulation where the message signal is a bipolar digital waveform. Because the carrier amplitude remains constant and only phase changes, BPSK is highly resistant to noise and offers better error performance than ASK and FSK.

---

## 🔌 Procedures

---

### Part A: Generating a BPSK Signal

1. Gather a set of the equipment listed above.
2. Set up the scope per the instructions in Experiment 1.
3. Set the scope's **Trigger Source** control to the **EXT** position.
4. Set the scope's **Trigger Source Coupling** control to the **HF REJ** position.
5. Set the scope's **Channel 1** and **Channel 2 Input Coupling** controls to the **DC** position.
6. Set the scope's **Timebase** control to the **0.1ms/div** position.
7. Locate the **Sequence Generator** module and set its dip-switches to **00**.
8. Connect the set-up so that:
   - Sequence Generator **CLK** connects to Master Signals **8kHz** clock.
   - Sequence Generator **SYNC** connects to Scope **EXT** trigger.
   - Sequence Generator **OUT** connects to Multiplier **X input**.
   - Master Signals **100kHz sine** connects to Multiplier **Y input**.

### Block Diagram
<img src="./docs/FIGURE 3 (2).JPG" width="600" alt="Expt 17 Figure 3">

### Output
<img src="./images/FIGURE 2 (2).jpg" width="600" alt="Expt 17 Figure 2">

9. Set the scope’s **Mode** control to the **DUAL** position to view the digital signal and the BPSK signal.
10. Activate the scope’s **Sweep Magnification** control.
11. Compare the signals and observe phase reversals.
12. Use the scope’s **Horizontal Position** control if needed to observe a logic transition clearly.
13. Deactivate the scope’s **Sweep Magnification** control.
14. Use the scope’s **Channel 1 Vertical Position** control to overlay the digital signal with the BPSK signal’s envelopes and compare them.

---

### Part B: Demodulating BPSK Using a Product Detector

15. Locate the **Tuneable Low-pass Filter** module and turn its **Cut-off Frequency Adjust** control fully clockwise.
16. Set the **Tuneable Low-pass Filter Gain** control to about the middle of its travel.
17. Modify the set-up by adding a second **Multiplier** and the **Low-pass Filter** to form a product detector.

### Block Diagram
<img src="./docs/FIGURE 5 (2).JPG" width="600" alt="Expt 17 Figure 5">

### Output
<img src="./images/FIGURE 4 (4).jpg" width="600" alt="Expt 17 Figure 4">

18. Compare the original digital signal with the recovered digital signal.

---

### Part C: Restoring the Recovered Digital Signal Using a Comparator

19. Modify the set-up by connecting the Low-pass Filter output to the **Comparator IN** and adding the **Variable DCV** module to the **Comparator REF** input.

### Block Diagram
<img src="./docs/FIGURE 7 (3).JPG" width="600" alt="Expt 17 Figure 7">

### Output
<img src="./images/FIGURE 6 (2).jpg" width="600" alt="Expt 17 Figure 6">

20. Set the **Variable DCV** module’s **Variable DC** control to about the middle of its travel.
21. Compare the signals. If they are not identical, vary the **Variable DC** control until the recovered digital signal matches the original (ignoring phase shift).

---

## ❓ Questions and Answers

**Question 1: What happens to the BPSK signal on the data stream's logic transitions?**  
**Answer:** At each logic transition, the BPSK signal undergoes a 180° phase shift. The sine wave instantly inverts in polarity.

**Question 2: What feature of the BPSK signal suggests that it's a DSBSC signal?**  
**Answer:** The envelope of the BPSK signal follows the digital data pattern and crosses zero during polarity changes, which is characteristic of a suppressed carrier signal.

**Question 3: Why is the recovered digital signal not a perfect copy of the original?**  
**Answer:** The Low-pass Filter removes high-frequency components of the square wave, rounding the edges and slightly distorting the waveform.

**Question 4: What can be used to “clean-up” the recovered digital signal?**  
**Answer:** A comparator circuit (or Schmitt trigger).

**Question 5: Why does varying the DC voltage on the comparator’s input change the shape of the digital signal?**  
**Answer:** The DC voltage sets the comparator’s threshold level. Because the recovered signal has sloped edges, changing the threshold alters the exact switching point, which affects the pulse width of the output waveform.

---

## 💡 Summary and Reflection

In this experiment, a BPSK signal was generated by multiplying a digital data stream with a high-frequency carrier, producing characteristic 180° phase reversals. The relationship between digital transitions and carrier phase inversion was clearly observed.

Demodulation was performed using a product detector followed by a Low-pass Filter to recover the baseband signal. Although filtering introduced rounding of the waveform edges, a comparator successfully restored the signal to a clean digital format. This experiment demonstrated the practical implementation of BPSK modulation and demodulation and highlighted its robustness in digital communication systems.
