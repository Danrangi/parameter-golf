# Parameter Golf Submission

This repository contains our submission for the OpenAI Parameter Golf Challenge.

## Objective
Design a compact language model under strict constraints:
- ≤16MB total size (model + code)
- ≤10 minutes training time
- Optimized for compression efficiency (bits per byte)

## Structure
- weights/ — model weights
- config/ — configuration files
- train.py — training script
- run.sh — execution script
- training_log.txt — training logs

## Approach (Draft)
Work in progress — focused on:
- parameter sharing
- quantization
- compression-aware training

