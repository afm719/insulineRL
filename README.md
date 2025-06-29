# Insulin Simulator

This project uses Reinforcement Learning (RL) to develop an automated insulin delivery system. The goal is to maintain blood glucose levels within a healthy range for individuals with type 1 diabetes by simulating food intake and administering appropriate insulin doses.

## System Methodology

We use the `simglucose` library, a validated FDA-accepted simulator, to create a safe and realistic digital environment for training our RL agents. This environment, wrapped to be compatible with the `gymnasium` interface, allows the agent to learn through trial and error without any risk to real patients.

The learning process involves discrete 1-minute cycles where the agent:
1.  **Observes** the current glucose level.
2.  **Decides** on an insulin dose (action).
3.  Receives a **reward** based on whether the resulting glucose level is within the target range (70-180 mg/dL). Hypoglycemia (<70 mg/dL) is heavily penalized.

## Core Components

* **State Space**: The agent's perception is based on a discretized state of the current glucose level (4 levels) and the velocity of glucose change (3 levels).
* **Action Space**: The agent can choose from a discrete set of insulin doses: `{0, 0.5, 1.0, 1.5}` units.
* **Reward Function**: A Gaussian function centered at 115 mg/dL, with a significant penalty for hypoglycemia.

## Models Implemented

Several RL algorithms were trained and evaluated:
* Q-learning (TD(0) and TD(1))
* SARSA
* Expected SARSA
* REINFORCE
* Actor-Critic

These agents were compared against a traditional **PID (Proportional-Integral-Derivative) Controller** as a baseline.

## Setup

To run the project, install the necessary libraries:
```bash
pip install matplotlib numpy simglucose
```
## References

* OpenAI. (2025). *ChatGPT* (Jun 29 version) [Large language model]. https://chat.openai.com
* jxx123. (2019). *simglucose* [Software]. GitHub. https://github.com/jxx123/simglucose
