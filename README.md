# Reinforcement Learning for Fabric Cutting Optimization

## Overview
This project models fabric layout optimization as a Markov Decision Process (MDP) and solves it using tabular Q-learning.

The agent learns a placement policy that optimizes long-term reward by:

maximizing space utilization
minimizing structural inefficiencies (holes)
reducing final material waste

The system is implemented from scratch (no RL frameworks), with a focus on environment design, reward engineering, and algorithmic efficiency.

## Key Contributions
Designed a custom RL environment for 2D packing with constraints
Implemented efficient action space generation with caching
Developed a reward shaping strategy for stable learning
Implemented a tabular Q-learning agent with ε-greedy exploration
Benchmarked performance against a random baseline
Visualized training dynamics and final layouts

## Methodology

### Environment
Grid-based fabric: 8x8
State: flattened grid + remaining pieces
Action: (piece_index, rotation, x, y)
Deterministic transitions
Episode ends when all pieces are placed or no valid moves remain

### Reward Function

To address sparse rewards and guide learning, a shaped reward is used:

+2 x filled cells (encourages compact placement)
-3 x holes (penalizes poor structure)
-2 x unused cells at episode end (penalizes waste)

This design significantly improves convergence stability and policy quality.

## Learning Algorithm

Tabular Q-Learning (off-policy): 
Q(s, a) ← Q(s, a) + α [r + γ max_a' Q(s', a') − Q(s, a)]

Exploration: ε-greedy
ε decay for convergence
No model of environment required

## Results

The learned policy consistently outperforms a random baseline:

higher average grid utilization
fewer structural holes
reduced final waste

### Training Dynamics
Early phase: random exploration
Mid phase: emergence of structured layouts
Late phase: stable, near-optimal packing behavior

## Visualization
Reward curve (raw + moving average)
Best grid layout found during training
Direct comparison with random baseline

## Technical Highlights
Action caching reduces redundant computation
Efficient validity checking for piece placement
Lightweight state representation (tuple encoding)
Modular design:
- FabricEnv
- QLearningAgent
- train()

## Complexity & Limitations
State-action space grows exponentially
Tabular Q-learning does not scale to large instances
Performance depends on reward design quality

## Future Work
Replace Q-table with Deep Q-Network (DQN)
Introduce stochastic environments
Expand to real-world cutting constraints
Multi-agent or hierarchical RL approaches

<img width="571" height="455" alt="rl-project-001" src="https://github.com/user-attachments/assets/f147a3a7-319d-43ff-beb1-5ec7760ffd14" />

<img width="389" height="411" alt="rl-project-002" src="https://github.com/user-attachments/assets/ef354a03-35ed-4d55-b237-d2586b8288af" />


