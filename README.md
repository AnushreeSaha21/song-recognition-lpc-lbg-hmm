# 🎵 Song Recognition using LPC + LBG + HMM (C++ from Scratch)

A classical audio recognition system built completely from scratch in **C++** that recognizes short sung song segments using:

- LPC Cepstral Feature Extraction  
- Vector Quantization (LBG Algorithm)  
- Discrete Hidden Markov Models (HMM)  
- Live Audio Recording + Recognition  

This project demonstrates how speech/audio recognition worked **before deep learning** by implementing the entire pipeline manually without external ML libraries.

---

## 🚀 Motivation

This project started as an academic **digit recognition assignment** using LPC, LBG, and HMM.

Out of curiosity, I extended the same pipeline to recognize short sung song segments.  
The goal was to explore how classical speech recognition techniques behave beyond isolated digits and understand the limitations of discrete HMM-based audio modeling.

Modern speech recognition is dominated by deep learning, but classical techniques like LPC, VQ, and HMM remain:

- foundational  
- interpretable  
- lightweight  
- academically important  

This project was built to deeply understand the **signal processing → modeling → recognition pipeline**.

---

## 🧠 Pipeline Overview
Audio Recording → Pre-processing (DC shift + normalization) → Framing + Hamming Window → LPC → Cepstral Coefficients (C1–C12) → Universe Creation → LBG Vector Quantization → Codebook → Observation Sequence Generation → HMM Training (Baum-Welch) → Live Recognition (Forward Algorithm)

---

## 🔊 Dataset

Each song contains multiple utterances (~3 seconds each):


song_1/
song_2/
song_3/
song_4/


Each utterance:
- mono audio  
- ~3 seconds duration  
- converted to `.txt` amplitude samples  

---

## ⚙️ Feature Extraction

- Frame size: **320 samples**  
- LPC order: **12**  
- Cepstral coefficients: **C1–C12**  
- Raised sine window applied  
- Silence removal via energy threshold  

---

## 📦 Vector Quantization (LBG)

- Universe built from all Ci vectors  
- Tokhura distance used  
- Codebook size: **32**  
- K-means refinement until distortion convergence  

---

## 🤖 Hidden Markov Model

- Left-to-right HMM topology  
- States (N): **7**  
- Observation symbols (M): **32**  
- Training: **Baum-Welch re-estimation**  
- Recognition: **Scaled Forward Algorithm**  

---

## 🎤 Live Recognition

The system:
1. Records ~3 seconds of singing  
2. Extracts Cepstral features  
3. Maps them to observation sequence  
4. Computes likelihood for each song model  
5. Outputs the most probable song  

---

## 📊 Results

- Correct recognition for trained songs  
- Confusion between acoustically similar songs (expected in classical HMM)  
- Works reliably for distinct melodic patterns  

---

## 💡 Key Learnings

- End-to-end audio recognition pipeline  
- Signal processing fundamentals  
- Vector quantization intuition  
- Numerical stability in HMM (scaling)  
- Importance of data quality and variability  

---

## ⚠️ Limitations

- Small dataset  
- Sensitive to recording conditions  
- Confusion between similar songs  
- Classical model capacity limits  

---

## 🛠️ How to Run

### 1. Generate Universe

universe.cpp


### 2. Build Codebook

lbg.cpp


### 3. Generate Observation Sequences

vq_observations.cpp


### 4. Train HMM Models

hmm_train.cpp


### 5. Evaluate

hmm_test.cpp


### 6. Live Recognition

live_song_recognition.cpp


---




