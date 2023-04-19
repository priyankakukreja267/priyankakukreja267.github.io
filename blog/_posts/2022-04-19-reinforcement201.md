---
layout: post
type: post
title: "Reinforcement Learning 201"
date: 2022-04-19
category: blog
comments: true
author: "Priyanka Kukreja"
tags: [ai]
---

Reinforcement learning is a mathematical framework for training an agent to take actions in an environment to maximize a reward signal. The goal of reinforcement learning is to learn an optimal policy, which is a function that maps states to actions that maximize the cumulative reward over time.

Formally, we can define a reinforcement learning problem as a Markov Decision Process (MDP) represented by a tuple (S, A, P, R, γ), where:
* S is the set of possible states of the environment.
* A is the set of possible actions that the agent can take.
* P is the transition probability function, which defines the probability of transitioning from one state to another given an action. Formally, P(s',r `|` s,a) = Pr(s_{t+1}=s',r_{t+1}=r`|`s_t=s,a_t=a), where s' is the next state, r is the reward, s is the current state, a is the current action, and t is the current time step.
* R is the reward function, which defines the immediate reward received by the agent for taking a particular action in a particular state. Formally, R(s,a) = E[r_{t+1}`|`s_t=s,a_t=a].
* γ is the discount factor, which determines the importance of future rewards. Formally, the discounted cumulative reward, or return, is defined as G_t = ∑_{k=0}^∞ γ^k r_{t+k+1}.

The agent's goal is to learn a policy π: S → A that maximizes the expected cumulative reward:
J(π) = E_π[G_t] = E_π[∑_{k=0}^∞ γ^k r_{t+k+1}]

There are two main types of reinforcement learning algorithms: model-based and model-free.

**Model-based algorithms** try to learn the transition probabilities P and the reward function R to compute an optimal policy π*. One example is the value iteration algorithm, which iteratively computes the optimal value function V* for each state and then derives the optimal policy from V*.

**Model-free algorithms** do not require a model of the environment and learn policies directly from experience. There are two main types of model-free algorithms: value-based and policy-based.

_Value-based algorithms_ try to learn the value function Vπ, which estimates the expected cumulative reward starting from a given state and following a certain policy π. One example is the Q-learning algorithm, which iteratively updates the Q-values, defined as the expected cumulative reward starting from a state-action pair, by minimizing the temporal difference error:

δ_t = r_{t+1} + γ max_a' Q(s_{t+1},a') - Q(s_t,a_t)

Q(s_t,a_t) ← Q(s_t,a_t) + α δ_t

_Policy-based algorithms_ try to learn the policy π directly. One example is the policy gradient algorithm, which updates the policy parameters θ to increase the expected cumulative reward:

∇_θ J(π_θ) = E_π_θ[∇_θ log π_θ(s,a) Qπ(s,a)]

θ ← θ + α ∇_θ J(π_θ)

Deep reinforcement learning is a variant of reinforcement learning that uses deep neural networks to represent the policy or value function. Deep reinforcement learning has achieved remarkable success in recent years, with applications in games, robotics, and healthcare. However, deep reinforcement learning algorithms face several challenges, including the instability of the learning process, the high computational cost of training deep networks, and the difficulty of generalizing to new environments.



