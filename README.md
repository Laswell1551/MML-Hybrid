# MML-Hybrid: Protocol-Informed Machine Learning for WLANs

[![Paper](https://img.shields.io/badge/Paper-IEEE%20TMC%20(Under%20Review)-blue.svg)](#)
[![Python 3.8+](https://img.shields.io/badge/python-3.8+-green.svg)](https://www.python.org/downloads/release/python-380/)
[![ns-3](https://img.shields.io/badge/ns--3-3.40-orange.svg)](https://www.nsnam.org/)

> Official repository for the paper: **"Protocol-Informed Machine Learning for Interpretable Throughput Prediction in Dense 802.11ax/be WLANs"** (Under Review at *IEEE Transactions on Mobile Computing*).

MML-Hybrid is a novel **Protocol-Informed Machine Learning (PIML)** framework that synergistically couples an analytical MAC protocol baseline ($\Phi_{\mathrm{Protocol}}$) with a data-driven residual learner ($\Delta_{\mathrm{ML}}$). It achieves millisecond-scale, state-of-the-art throughput prediction accuracy under complex real-world dynamics (e.g., hidden nodes, OBSS_PD, and MLO cross-link coupling).

## 📊 Causality-Preserving Data Pipeline
To address temporal leakage concerns, this repository includes our rigorous **Purging and Embargo** data split pipeline (see `src/data/causal_split.py` and **Algorithm 1** in the paper), ensuring zero future-data leakage during the sliding-window feature extraction.

## 📂 Repository Structure

```text
MML-Hybrid/
├── ns3-simulation/          # C++ scripts for dense WLAN data generation
│   ├── scratch/mml_dense_wlan.cc  # Core 802.11ax/be simulation script
│   └── config.json                # Topology and OBSS_PD parameters
├── src/                     # Python source code for the ML framework
│   ├── data/
│   │   └── causal_split.py        # Embargo-based chronological data splitter
│   ├── models/
│   │   ├── analytical_prior.py    # Markov/SINR baseline solver (IFT implemented)
│   │   └── residual_learners.py   # GBRT, D-GCN, and Autoformer models
│   └── train_hybrid.py            # Main training script with Hybrid Loss
├── requirements.txt         # Python dependencies
└── README.md

![image](https://github.com/Laswell1551/MML-Hybrid/blob/main/feature%20definitions)

