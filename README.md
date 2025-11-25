# DSB--SC-MODULATION-AND-DEMODULATION-USING-PYTHON

__AIM__:

To generate a Double Sideband Suppressed Carrier (DSB-SC) signal in Python (Google Colab), transmit it (optionally add noise), and recover the message using coherent (synchronous) demodulation with a low-pass filter. Observe time and frequency domain waveforms and measure demodulation performance

__APPARATUS REQUIRED__:

Google Colab (or any Python environment)

Python libraries: numpy, matplotlib, scipy (scipy.signal)

__Theory__:

DSB-SC signal: s(t) = m(t) · cos(2πf_c t)
Coherent demodulation: multiply received s(t) by a synchronized carrier cos(2πf_c t) then low-pass filter (LPF) to remove double-frequency components:

r(t) = s(t)·cos(2πf_c t) = m(t)·cos²(2πf_c t) = 0.5 m(t) + 0.5 m(t)·cos(4πf_c t)
LPF extracts 0.5·m(t) → scale by 2 to recover m(t).

__Procedure__:

1) Import libraries and set parameters
2) Define message and carrier signals
3) Generate DSB-SC signal (modulation)
4) View spectra (FFT) of message and DSB-SC
5) (Optional) Add noise
6) Coherent demodulation (multiply by synchronized carrier)
7) Low-pass filter to recover message
```
import matplotlib.pyplot as plt
Ac = 20.6
fc = 4761.90
Am =10.3
fm = 600
fs = 70000
t = np.arange(0, 2/fm, 1/fs)
Wm = 2 * np.pi * fm
Wc = 2 * np.pi * fc
Em = Am * np.sin(Wm * t)
Ec = Ac * np.sin(Wc * t)
Edsbsc = ((Am / 2) * np.cos((Wc - Wm) * t)) - ((Am / 2) * np.cos((Wc + Wm) * t))
plt.figure(figsize=(10, 6))
plt.subplot(3, 1, 1)
plt.plot(t, Em)
plt.grid()
plt.subplot(3, 1, 2)
plt.plot(t, Ec)

plt.grid()
plt.subplot(3, 1, 3)
plt.plot(t, Edsbsc)
plt.grid()
plt.tight_layout()
plt.show()
```
   __Tabulation__:
   
   ![WhatsApp Image 2025-11-25 at 22 09 07_1a1638cb](https://github.com/user-attachments/assets/46e7e982-cb08-4bb1-ae4d-bdffe4a5d10a)
   ![WhatsApp Image 2025-11-25 at 22 08 35_7f5fa710](https://github.com/user-attachments/assets/17dbabc3-62f4-4466-873a-f6a1bd586c7b)
  




   __Output__:
   
   ![IMG-20251126-WA0003 1](https://github.com/user-attachments/assets/dacd459f-727f-4c93-9966-4fb768e7945b)


   __Result__:
   
   ![IMG-20251126-WA0002 1](https://github.com/user-attachments/assets/c0f81d7b-974d-489f-87ee-0e3a2fb5c772)

