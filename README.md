Predictive Relay Maloperation Early Warning System
Hybrid CNN–BiLSTM–Attention Model for Intelligent Relay Health Monitoring
Overview

Protective relay maloperations such as missed trips, delayed trips, and false trips can severely compromise power system stability and reliability.

This project presents a deep learning–based early warning framework capable of predicting relay maloperation using only the initial 50–60% of current and voltage waveform data — before the actual relay trip occurs.

The proposed system leverages a hybrid CNN–BiLSTM architecture enhanced with a temporal attention mechanism to capture both local waveform characteristics and long-term temporal dependencies.

Dataset Generation

The dataset was generated using MATLAB/Simulink simulations of a transmission system under five relay operating conditions:

Healthy

Correct Trip

Missed Trip

Delayed Trip

False Trip

Approximately 100 simulations per class (~500 total cases) were generated.

For early-warning modeling, the problem is reformulated as binary classification:

Normal = Healthy + Correct Trip

Maloperation = Missed + Delayed + False Trip

A small sample dataset is included in data/sample_dataset.csv

The complete automated dataset generation scripts are not publicly shared.

Model Architecture

The proposed early warning model employs a hybrid CNN–BiLSTM architecture augmented with a temporal attention mechanism:

1D Convolution layer for local waveform feature extraction

MaxPooling layer

Bidirectional LSTM (BiLSTM) for temporal dependency modeling

Attention mechanism to emphasize critical time instances

Dense layer with Softmax activation for binary classification

This architecture enables predictive supervision using partial waveform information.

Preprocessing Pipeline

Early waveform window extraction (first 50–60%)

Temporal downsampling

Zero-padding to ensure uniform sequence length

Stratified 80/20 train–validation split

Performance (Validation Set)

Accuracy: 0.920

Macro F1-score: 0.914

Recall (Maloperation): 0.983

AUC: ≈ 0.92

High recall for maloperation is critical in protection systems, ensuring minimal missed anomaly detection.

The model successfully predicts abnormal relay behavior before the actual tripping event.

Conference Publication

Accepted and presented at ICCECE 2026.
IEEE Xplore publication pending.

Tech Stack

MATLAB / Simulink (Dataset Generation)

Python

TensorFlow / Keras

NumPy, SciPy, scikit-learn

Matplotlib

Future Work

Multi-class maloperation classification

Transformer-based sequence modeling

Hardware-in-the-loop validation

Real-time embedded implementation