# RL & Transformer-Driven Transistor Placer

A research project on learning-based transistor placement for standard cell layout generation, targeting diffusion-break minimization and physical design optimization.

## Overview

This project explores reinforcement learning for transistor placement in standard cell layout generation.  
The current framework takes **ASAP7 SPICE netlists converted into JSON format** as input and generates transistor placements for standard cells.

The model combines:

- **PPO** for policy optimization
- **GNN-based encoding** for transistor-level structural features
- **Transformer / cross-attention** for sequential placement decision modeling
- **Coupled lookahead checks** to avoid dead-end placements across N/P rows
- **Clock-aware heuristics** for handling sensitive sequential-cell alignment cases

The goal is to improve placement validity, reduce diffusion breaks, and provide a more scalable alternative to exhaustive search-based approaches.

## Motivation

Standard cell layout generation is a core problem in physical design automation.  
At advanced nodes, transistor placement quality strongly affects diffusion sharing, layout compactness, and downstream routing quality.

This project studies whether reinforcement learning can improve:

- placement robustness
- runtime efficiency
- generalization to unseen cells
- future integration with routing-aware optimization

## Input Representation

The input netlists are extracted from the **ASAP7** standard cell library.  
SPICE transistor netlists are preprocessed into **JSON-based transistor/net connectivity representations**, which are then converted into graph and sequence features for training and inference.

## Method

The current version is based on a **coupled row-based transistor placement framework** for NMOS/PMOS transistor pairing.

Key design ideas include:

- **Graph-based feature construction** from transistor connectivity and device attributes
- **Cross-attention / Transformer-based sequence modeling** for placement context
- **Coupled dead-end checks** to prevent infeasible future placements across N/P rows
- **Clock-aware alignment heuristics** for sequential cells with sensitive clock-related nets
- **Dual-model ensemble inference** with automatic layout selection based on break count and HPWL

## Current Status

This project is under active development.

Current focus areas include:

- improving robustness on challenging standard cells
- studying zero-shot generalization on unseen test cells
- extending the framework toward placement-routing co-optimization
- refining routing-aware and timing-aware placement signals

Representative results reported in the project include:

- **100% solvability** on evaluated ASAP7 standard cells
- **strong win/tie rate** against the AutoCellGen baseline
- **significant runtime speedup** over exhaustive-style search approaches

## Example Output

Example layout outputs include placed standard cells such as `DFFLQx4_ASAP7_75t_R`, with generated N/P row pairings, inserted isolation columns, and break counts for evaluation.

## Repository Note

This public repository serves as a project showcase.  
The full training/inference codebase is currently kept private due to ongoing collaborative research and project development.

## Keywords

EDA, APR, transistor placement, reinforcement learning, PPO, GNN, Transformer, standard cell layout, physical design automation
