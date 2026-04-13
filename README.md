# Reinforcement Learning for Fabric Cutting Optimization

This project applies Q-learning to solve a 2D packing problem inspired by fabric cutting in the fashion industry.

The goal is to place irregular shapes (patterns) onto a fixed grid (fabric) in order to maximize space utilization and minimize waste.

## Problem Description

In textile manufacturing, efficient fabric usage is critical. Poor layout leads to material waste and increased costs.

This project models the problem as a Reinforcement Learning task where an agent learns how to optimally place pieces on a grid.

## Approach

- Environment: Custom grid-based simulation
- Algorithm: Q-learning
- State: Flattened grid representation
- Actions: Select piece, rotation, and position
- Reward:
  - Positive reward for placing pieces
  - Penalty for holes and unused space
  - Final penalty for wasted fabric

## Training Behavior

- The agent shows clear learning progress over episodes
- Converges to stable policies
- Demonstrates improved packing efficiency

