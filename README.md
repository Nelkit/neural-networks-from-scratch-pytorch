# Neural Networks from Scratch — PyTorch & NumPy

> Deep Learning · MSc Data Science & Innovation · University of Technology Sydney (UTS) · 2026

## Overview

Two-part project exploring neural network fundamentals: a Perceptron built from scratch using only NumPy, and a fully connected neural network trained on the Japanese MNIST dataset using PyTorch.

The goal was to understand what happens under the hood before relying on high-level abstractions.

## Part A — Perceptron from Scratch (NumPy)

Implemented forward and backpropagation manually using only NumPy and Pandas. No scikit-learn, no PyTorch. The exercise forces a clear understanding of how gradients flow and weights update at the most fundamental level.

## Part B — Neural Network on Kuzushiji-MNIST (PyTorch)

**Dataset:** 70,000 images of handwritten Hiragana characters · 10 classes · 28x28px flattened to 784-dimensional vectors

Four experiments were run progressively:

| Experiment | Architecture | Test Accuracy | Overfitting Gap |
|---|---|---|---|
| 0 — Baseline | 128 neurons, no regularisation | 89.49% | 10.49% |
| 1 — Dropout | 128 neurons, dropout 0.5 | 84.37% | 12.63% |
| 2 — Hyperparameter Tuning | 512 neurons, dropout 0.3, LR 0.001 | 92.13% | 7.46% |
| 3 — Weight Decay (final) | 512 neurons, dropout 0.3, LR 0.001, L2 1e-4 | 91.60% | 7.14% |

**Final model selected:** Experiment 3, prioritising generalisation over raw accuracy. The addition of L2 regularisation compressed the overfitting gap to 7.14% while maintaining 91.60% test accuracy.

## Key Findings

- Aggressive dropout (0.5) on a small architecture hurts more than it helps — it reduced active capacity to ~64 neurons per epoch
- Scaling hidden neurons from 128 to 512 was the single biggest performance driver
- L2 regularisation (Weight Decay) proved more effective than dropout alone for controlling overfitting
- Class 2 was the hardest to classify (F1: 0.87, Recall: 0.89) — a structural limitation of flattening 2D images for fully connected layers, which destroys spatial relationships between pixels
- CNNs would be the natural next step to address this limitation

## Stack

Python · PyTorch · NumPy · Pa
