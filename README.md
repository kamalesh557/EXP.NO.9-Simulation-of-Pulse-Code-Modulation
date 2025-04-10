# EXP.NO.9-Simulation-of-Pulse-Code-Modulation
9.Simulation of PCM

# AIM
To implement Pulse Code Modulation (PCM) for encoding and decoding a sinusoidal signal using quantization and to observe the output waveforms.

# SOFTWARE REQUIRED
Python Software -> Numpy Library
-> Matplotlib Library

-> Scipy Library (for signal processing

# ALGORITHMS
Generate a sinusoidal signal.
Sample the signal at a fixed rate.
Quantize the sampled values to the nearest discrete level.
Convert the quantized values into binary (encoding).
Decode the binary data back into quantized values.
Reconstruct the signal from the quantized values.
Plot the original, sampled, quantized, and reconstructed signals.

# PROGRAM
import numpy as np

sampling_rate = 5000

frequency = 50

duration = 0.1

quantization_levels = 16

t = np.linspace(0, duration, int(sampling_rate * duration), endpoint=False)

message_signal = np.sin(2 * np.pi * frequency * t)

clock_signal = np.sign(np.sin(2 * np.pi * 200 * t))

quantization_step = (max(message_signal) - min(message_signal)) / quantization_levels

quantized_signal = np.round(message_signal / quantization_step) * quantization_step

pcm_signal = (quantized_signal - min(quantized_signal)) / quantization_step

pcm_signal = pcm_signal.astype(int)

plt.figure(figsize=(12, 10))

plt.subplot(4, 1, 1)

plt.plot(t, message_signal, label="Message Signal (Analog)", color='blue')

plt.title("Message Signal (Analog)")

plt.xlabel("Time [s]")

plt.ylabel("Amplitude")

plt.grid(True)

plt.subplot(4, 1, 2)

plt.plot(t, clock_signal, label="Clock Signal (Increased Frequency)", color='green')

plt.title("Clock Signal (Increased Frequency)")

plt.xlabel("Time [s]")

plt.ylabel("Amplitude")

plt.grid(True)

plt.subplot(4, 1, 3)

plt.step(t, quantized_signal, label="PCM Modulated Signal", color='red')

plt.title("PCM Modulated Signal (Quantized)")

plt.xlabel("Time [s]")

plt.ylabel("Amplitude")

plt.grid(True)

plt.subplot(4, 1, 4)

plt.plot(t, quantized_signal, label="Signal Demodulation", color='purple', linestyle='--')

plt.title("Signal Without Demodulation")

plt.xlabel("Time [s]")

plt.ylabel("Amplitude")

plt.grid(True)

plt.tight_layout()

plt.show()

# OUTPUT
![image](https://github.com/user-attachments/assets/e22740a2-0d10-4680-8a4b-def2e22fd288)

![image](https://github.com/user-attachments/assets/61332446-fafc-43cb-9a03-f86feac288a4)

# RESULT / CONCLUSIONS
The PCM encoding process successfully quantized the original sine wave into 16 levels.

The demodulated signal closely resembled the original signal with minor quantization noise.

The output waveforms validated the functioning of PCM in digital communication systems.
