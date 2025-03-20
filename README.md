# MountainCar-v0

The [MountainCar-v0](https://www.gymlibrary.dev/environments/classic_control/mountain_car/) environment is a classic reinforcement learning challenge. The goal is to drive a car up a steep hill by building momentum.

<p align="center">
  <img width="480" height="323" src="/assets/demo.png" alt="MountainCar-v0 Demo">
</p>

This project applies several reinforcement learning (RL) algorithms to solve the MountainCar-v0 problem. Detailed analyses and findings are available in the [report](https://github.com/pavlosdais/MountainCar-v0/blob/main/report.pdf). In short, the algorithms explored are:

### [Deep Q-Network (DQN)](https://github.com/pavlosdais/MountainCar-v0/blob/main/src/mountaincarv0-DQN.ipynb)
- **Overview:**  
  DQN uses a deep neural network to estimate Q-values and leverages experience replay and target networks for stability. We also explored a variant called noisy DQN, which introduces randomness in the network parameters to encourage better exploration.
- **Results:**  
  The standard DQN agent improves gradually, but its performance is sensitive to hyperparameters like the learning rate and batch size. The noisy DQN variant showed notable improvement under certain conditions.

---

### [Deep Recurrent Q-Network (DRQN)](https://github.com/pavlosdais/MountainCar-v0/blob/main/src/mountaincarv0-DRQN.ipynb)
- **Overview:**  
  DRQN adds LSTM layers to capture memory over time. This is useful when the full state (like velocity) isn’t visible.
- **Tests Conducted:**  
  - **Partial Observability:** Only the car’s position is given.
  - **Noisy Observations:** Gaussian noise is added to the position.
- **Results:**  
  DRQN performs better than DQN when some information is missing or noisy, thanks to its ability to remember past observations.

---

### [Proximal Policy Optimization (PPO)](https://github.com/pavlosdais/MountainCar-v0/blob/main/src/mountaincarv0-PPO.ipynb)
- **Overview:**  
  PPO is a policy gradient method that uses a clipping mechanism to prevent large, unstable updates.
- **Results:**  
  The agent learns steadily and reliably, with the clipping strategy helping to keep the training process stable.

---

### [Advantage Actor Critic (A2C)](https://github.com/pavlosdais/MountainCar-v0/blob/main/src/mountaincarv0-A2C.ipynb)
- **Overview:**  
  A2C combines an actor (which chooses actions) and a critic (which evaluates them) to improve learning efficiency.
- **Results:**  
  A2C offers a stable, straightforward alternative with performance comparable to PPO in many scenarios.

