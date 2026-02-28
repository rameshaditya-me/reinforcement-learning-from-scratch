# Reinforcement Learning From Scratch

This repository is a continuation of [norhum’s reinforcement-learning-from-scratch](https://github.com/norhum/reinforcement-learning-from-scratch), but with a different goal: **to build a real decision-making system step-by-step, not just to explain algorithms**.

Instead of introducing reinforcement learning as a collection of methods, the series follows a single motivating problem — **constructing a recommendation system**.
Each algorithm appears only when the current system fails. The reader sees *why* a method is needed before learning *how* it works.

A recommender is not merely predicting user behavior. The system *chooses what users see*, which in turn changes future data. This makes recommendation a sequential control problem rather than a standard supervised learning task, and naturally leads to reinforcement learning.

---

## Learning Trajectory

We start with a naive recommender and progressively upgrade it.

### 1. Recommendation as Interaction

We first formalize recommendation as an agent–environment loop:

| RL Concept | Recommender Interpretation       |
| ---------- | -------------------------------- |
| State      | user/session history             |
| Action     | item shown to the user           |
| Reward     | click, dwell time, or engagement |
| Policy     | ranking strategy                 |

---

### 2. Multi-Armed Bandits — Cold-Start Recommendation

When no user information is available, the system must learn which items are generally good while minimizing user dissatisfaction.

Topics:

* Exploration vs. exploitation
* ε-Greedy and scheduled exploration
* Upper Confidence Bound (UCB)
* Thompson Sampling and stochastic bandits
* Neural bandits
* Non-stationary environments (changing user taste)
* Contextual Bandits
* Real-world bandit applications

Here, bandits replace fixed A/B tests by learning during experimentation.

---

### 3. Value-Based Methods — Personalization

Global recommendations fail because different users want different items.
We introduce state and learn:

[
Q(s,a) = \text{expected engagement for user state } s \text{ and item } a
]

Topics:

* Q-values vs rewards
* Q-Learning (off-policy TD learning)
* SARSA (on-policy learning)

The recommender becomes personalized rather than global.

---

### 4. Deep Reinforcement Learning — Representation Learning

User behavior is high-dimensional and tabular methods break down.
Neural networks are introduced to learn embeddings and decision policies jointly.

Topics:

* Deep Q-Networks (DQN)
* Experience replay (logged interaction data)
* Target networks (stability under distribution shift)
* GridWorld experiments as controlled testbeds

---

### 5. Policy Gradient Methods — Ranking Optimization

Real recommenders present multiple items simultaneously.
Instead of estimating action values, we directly optimize the recommendation policy.

Topics:

* REINFORCE (Monte Carlo policy gradients)
* CartPole as an initial policy optimization environment

---

### 6. Actor–Critic — Long-Term Engagement

Maximizing immediate clicks can harm retention.
We now optimize long-term user value rather than short-term reward.

Topics:

* Advantage Actor-Critic (A2C)
* Continuous control (Pendulum)
* Learning stable policies using value baselines

---

## Why Reinforcement Learning?

A supervised model estimates:

[
P(\text{click} \mid \text{user}, \text{item})
]

However, once deployed, the model decides which items users see.
This introduces selection bias and changes the data distribution.
Reinforcement learning explicitly models this feedback loop and optimizes behavior over time rather than static prediction.

---

## What You Will Gain

This series focuses on:

* implementing algorithms from first principles
* understanding failure modes (instability, bias, non-stationarity)
* connecting theory to real online decision systems
* building a complete learning-based recommender

The goal is not only to learn reinforcement learning, but to understand **when and why it is the correct tool for real interactive systems**.
