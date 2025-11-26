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
   ## PROGRAM:
```
import numpy as np
import matplotlib.pyplot as plt
Am =5    
Ac =10   
fm = 777   
fc = 7770    
fs = 77700   
t = np.arange(0, 2/fm, 1/fs)
m = Am * np.cos(2 * np.pi * fm * t)
plt.subplot(3, 1, 1)
plt.plot(t, m)
c = Ac * np.cos(2 * np.pi * fc * t)
plt.subplot(3, 1, 2)
plt.plot(t, c)
s1 = (Ac + m) * np.cos(2 * np.pi * fc * t)
s2 = (Ac - m) * np.cos(2 * np.pi * fc * t)
s = s1 - s2
plt.subplot(3, 1, 3)
plt.plot(t, s)
plt.tight_layout()
plt.show()
```


   __Tabulation__:

   ![WhatsApp Image 2025-11-26 at 19 56 30_a2d427b7](https://github.com/user-attachments/assets/8a104544-b460-465b-86d8-34f48e91008c)

   ![WhatsApp Image 2025-11-26 at 19 57 56_862088ba](https://github.com/user-attachments/assets/f3318f92-47a0-4232-85af-8d312c3186ad)

   __Output__:
    
 <img width="777" height="582" alt="image" src="https://github.com/user-attachments/assets/8c20d2d0-7a02-4168-87b0-73236e2b8e1b" />
 
   __Result__:

   Thus the DSB-SC-AM Modulation and Demodulation using python is generated.
