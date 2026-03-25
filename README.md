# audio-denoising-in-production

Practical, use-case-driven collection of audio denoising methods focused on real-world performance. Includes curated implementations, standardized comparisons, real audio evaluations, and clear guidance on what works best in production.

---

## Goal

This repository is not a paper list or benchmark leaderboard.

It answers one question:

What audio denoising method should I actually use in production?

Focus areas:
- real-world audio (calls, meetings, noisy environments)
- practical tradeoffs (latency, compute, robustness)
- actual behavior, not just benchmark scores

---

## Quick Decision Guide

| Use Case | Recommended Approach | Notes |
|----------|--------------------|------|
| Phone / call audio | RNNoise | low latency, robust |
| Real-time processing | Lightweight DSP / RNNoise | CPU-friendly |
| Offline high quality | Demucs / deep models | higher compute |
| Simple baseline | Spectral gating | fast, but artifacts |

See detailed results below.

---

## Evaluation Approach

All methods are tested on consistent real-world scenarios:

- Phone call audio (compressed, low bitrate)
- Meeting recordings (background noise)
- Music with noise
- Multilingual speech
- Silence / baseline noise profiling

Evaluation includes:
- subjective listening tests
- optional metrics (e.g. SNR, WER impact)
- notes on artifacts and failure modes

---

## Results by Scenario

### Phone Call Audio

| Method | Result | Notes |
|--------|--------|------|
| RNNoise | Good | strong baseline |
| Spectral gating | Mixed | metallic artifacts |
| Demucs | Poor | over-processing |

---

### Meeting Audio

| Method | Result | Notes |
|--------|--------|------|
| TBD | | |

---

### Music with Noise

| Method | Result | Notes |
|--------|--------|------|
| TBD | | |

---

## Methods Overview

### RNNoise
- Type: RNN-based noise suppression
- Real-time: Yes
- GPU: No
- Best for: speech, calls
- Weakness: music, complex environments

### Spectral Gating (noisereduce)
- Type: classical DSP
- Real-time: depends
- GPU: No
- Best for: simple noise
- Weakness: artifacts

### Demucs
- Type: deep learning (source separation)
- Real-time: No
- GPU: Recommended
- Best for: high-quality offline processing
- Weakness: latency, over-processing speech

---

## How to Use This Repository

1. Start with the Quick Decision Guide
2. Check results for your specific scenario
3. Review method tradeoffs
4. Test with your own audio

---

## Repository Structure

.
├── methods/          
├── evaluations/      
├── audio_samples/    
├── scripts/          
└── README.md

---

## Roadmap

- Add more real-world audio samples
- Standardized evaluation pipeline
- WER-based evaluation (ASR impact)
- Streaming vs batch comparison
- Lightweight / edge models
- Diffusion-based denoising methods

---

## Disclaimer

Results are based on limited real-world tests and may vary depending on data and setup. Always validate with your own audio pipeline.

---

## Motivation

Most resources optimize for research or completeness.

This repository focuses on making the right engineering decision in real-world systems.
