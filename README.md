# Domain Randomization for Sim-to-Sim Transfer

*(Reinforcement Learning project — Intelligent Control course project, by Panagiotis Kiousis and
Emmanouil Tsiknakis)*

![Preview](pic.png)

A PPO-trained Actor–Critic agent learns to navigate a continuous 2D environment to a randomly placed
goal, using a simulated LiDAR-type sensor. The environment's physical parameters (mass, friction) are
randomized at every episode reset — domain randomization — so the policy is evaluated on its zero-shot
generalization to dynamics it never saw during training.

## Report

The full write-up is **[`report_en/report_en.pdf`](report_en/report_en.pdf)**. It covers the
environment and reward design, the Actor–Critic architecture, the PPO/GAE math, and the training and
zero-shot evaluation results, with all the original figures.

## Requirements

Install the required Python libraries with:

```bash
pip install -r requirements.txt
```

## Files

| File | Description |
|---|---|
| `main.py` | Runs the PPO training loop and the zero-shot evaluation. |
| `env.py` | Defines the environment, sensors (simulated LiDAR), physics, and 3D visualization. |
| `model.py` | Defines the Actor–Critic neural network architecture. |
| `report_en/report_en.pdf` | Full project report. |
| `requirements.txt` | Project dependencies. |

## How to Run

To start training:

```bash
python main.py
```

During training, the console prints the average reward per epoch. During the last 10% of training, the
3D visualization is enabled automatically.

## Output

During training:
- The best policy (its `state_dict`) is saved automatically whenever a new best average reward is found.
- Reward-per-epoch plots are generated.

After training completes, the agent is evaluated on new, randomized environments (zero-shot evaluation).
