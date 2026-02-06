# PAM-4 Image Transmission

This project demonstrates an end-to-end PAM-4 image transmission system to study how real communication impairments affect actual data instead of only random bit streams.

An image is used as the payload so that the impact of noise, inter-symbol interference (ISI), ADC quantization, and equalization can be observed both numerically and visually.

---

## What was implemented

The following processing chain was implemented:

Image → Bitstream generation → PAM-4 symbol mapping  
→ Pulse shaping → ISI channel → AWGN noise  
→ ADC quantization → Matched filtering  
→ Timing phase selection → Feed-forward equalization (FFE)  
→ Symbol detection → Bit recovery → Image reconstruction

---

## Motivation

Most communication simulations use PRBS or random data.  
Using an image allows visual validation of BER, PSNR, and equalization performance, which better reflects real systems such as display links and high-speed serial interfaces.

---

## Concepts covered

- PAM-4 modulation and Gray coding  
- Channel ISI effects  
- Additive white Gaussian noise (SNR sweep)  
- ADC resolution trade-offs  
- Matched filtering and sampling phase selection  
- Feed-forward equalization (FFE)  
- BER and PSNR evaluation  
- Eye diagram and post-equalization scatter analysis  
- Pixel-level error visualization

---

## Results

The `results/` folder contains:

- BER vs SNR plots  
- BER vs ADC resolution plots  
- Eye diagram (matched filter output)  
- Post-equalization PAM-4 scatter plot  
- Equalizer tap coefficients  
- Original vs reconstructed image comparison  
- Difference heatmap and error overlay

---

## Notes

- Source code is intentionally not included.
- This repository focuses on system-level validation and results.

---

## Relevance

This project is relevant to:
- High-speed serial links (SerDes)
- Mixed-signal receiver design
- Hardware validation and PHY-layer analysis
