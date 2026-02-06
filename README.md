# PAM-4 Image Transmission (Python)

This project implements an end-to-end PAM-4 image transmission system to study how communication impairments affect real image data. The goal is to bridge concepts from digital communication and signal integrity with practical image-level validation.

---

## Project Overview

In this project, an RGB image is:
1. Converted into a binary bitstream
2. Mapped to PAM-4 symbols
3. Transmitted through a noisy and ISI-impaired channel
4. Quantized using a finite-resolution ADC
5. Equalized and demodulated at the receiver
6. Reconstructed back into an image

Performance is evaluated using **BER (Bit Error Rate)** and **PSNR (Peak Signal-to-Noise Ratio)**.

---

## System Features

- PAM-4 modulation and demodulation
- Root Raised Cosine (RRC) pulse shaping
- Inter-symbol interference (ISI) channel modeling
- Additive white Gaussian noise (AWGN)
- ADC quantization (configurable bit resolution)
- Timing phase selection
- Linear equalization
- BER and image-quality evaluation

---
## System Flow

1. Load input RGB image  
2. Convert image pixels into a binary bitstream  
3. Group bits and map them to PAM-4 symbols (2 bits per symbol)  
4. Apply Root Raised Cosine (RRC) pulse shaping  
5. Transmit the signal through a channel with:
   - Additive White Gaussian Noise (AWGN)
   - Inter-Symbol Interference (ISI)
6. Receiver processing includes:
   - Matched filtering
   - Optimal sampling phase selection
   - PAM-4 symbol detection
   - Bit reconstruction
7. Reconstruct the image from recovered bits  
8. Evaluate performance using BER and PSNR  
9. Generate plots and image comparison results  
 ---

## Example Run Configuration

- Image size: **512 × 512 RGB**
- Modulation: **PAM-4**
- SNR: **15 dB**
- ADC resolution: **8 bits**
- Oversampling factor: **8 samples/symbol**
- RRC roll-off factor: **0.25**
- ISI channel taps: [0.85, 0.35, -0.18, 0.08]

---

## Key Results

- **Bit Error Rate (BER):**  
  `4.69 × 10⁻⁴`

- **Image Quality (PSNR):**  
  `39.9 dB`

Despite channel noise and quantization, the reconstructed image maintains high visual fidelity, with errors appearing sparsely and without structural distortion.

---

## Result Visualizations

### BER vs ADC Resolution
![BER vs ADC](input_ber_vs_adc.png)

### BER vs SNR
![BER vs SNR](input_ber_vs_snr.png)

### PAM-4 Symbol Distribution (Post-Equalization)
![Constellation](input_constellation.png)

### Channel Equalizer Taps
![EQ Taps](input_eq_taps.png)

---

## Image-Level Validation

### Original vs Reconstructed Image

| Original Image | Reconstructed Image |
|---------------|---------------------|
| ![Original](input.png) | ![Reconstructed](input_rec_snr15.0_adc8.png) |


### Error Localization
![Error Overlay](error_overlay.png)

The error map highlights pixel locations affected by bit errors, demonstrating how physical-layer impairments translate into localized image artifacts.

---

## Why This Project Matters

This project demonstrates how:
- Physical-layer impairments impact real data
- ADC resolution and SNR trade-offs affect system performance
- Communication metrics (BER) relate to perceptual quality (PSNR)

The workflow reflects challenges encountered in **high-speed serial links, wireline communication, and image data transmission systems**.

---

## How to Run

```bash
python3 pam4_image_link_industry.py --image input.png --snr_db 15 --adc_bits 8
python3 pam4_image_link_industry.py --image input.png --do_sweeps
