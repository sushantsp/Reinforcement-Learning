# Reinforcement Learning: 

**L1: Basic Concepts (P1-State, action, policy, ...)**

Certainly! Let's create a more detailed and nuanced summary, reflecting on the lecture with more depth and personal insights:


This is the first lecture of my reinforcement learning course, where we begin by laying down the essential concepts that will form the backbone of everything we study moving forward. The lecture is structured in two parts: first, using intuitive examples to make the concepts relatable, and then formalizing these ideas within the framework of Markov Decision Processes.

### Introduction to Grid-World

#### What is a Grid-World?

Today, I was introduced to the concept of a **Grid-World**, a simplified environment that serves as a perfect illustration for understanding reinforcement learning. Imagine a grid where a robot moves around with the aim of reaching specific target areas. Each cell in this grid has a distinct role:
- **Accessible Cells**: These are the areas the robot can freely traverse, marked in white.
- **Forbidden Cells**: Represented in yellow, these are zones the robot should avoid to prevent penalties.
- **Boundaries**: The edges of the grid that the robot cannot cross, creating a closed environment.
- **Movement**: The robot's movement is restricted to left, right, up, and down directions—no diagonal moves allowed.

**Illustration Needed**: It might be helpful to create or find an image depicting a grid-world with these features clearly labeled, as visualizing these constraints can aid in understanding.

#### Task Objective

The core task within this grid-world setup is to determine an optimal path from the starting point to the target location. This is not as straightforward as it might seem. The robot must navigate efficiently, avoiding forbidden areas and unnecessary detours, such as circling back or hitting the boundaries. The challenge here lies in defining what makes a path "good" or "bad," which I will explore further when studying optimal policies.

## Diving into Key Concepts

### State

- **Definition**: The state describes the agent's current situation in the environment. In the grid-world context, it refers to the robot's location at any given time.
- **Example**: Each position on the grid is labeled as a state, such as \(s_1, s_2, \ldots, s_9\). For instance, \(s_1\) might correspond to specific x and y coordinates on the grid.
- **State Space**: The collection of all possible states forms the state space, denoted as \(S\). Although the term "space" might initially sound daunting, it simply refers to a set of all these locations.

### Action

- **Definition**: Actions are the possible moves the robot can make from its current state.
- **Example**: Possible actions (\(a_1\) to \(a_5\)) include moving up (\(a_1\)), right (\(a_2\)), down (\(a_3\)), left (\(a_4\)), and staying still (\(a_5\)), which is depicted by a circle.
- **Action Space**: The set of all possible actions is represented by \(A\), and it changes depending on the robot's current state. This dependency is denoted as \(A(s_i)\), indicating that the available actions may vary from one state to another.

### State Transition

- **Definition**: This refers to the process of moving from one state to another upon taking an action. 
- **Example**: If the robot is in \(s_1\) and executes action \(a_2\) (moving right), it transitions to \(s_2\). However, if action \(a_1\) (moving up) is taken in \(s_1\), the robot encounters a boundary and remains in \(s_1\). This concept illustrates the interaction between the agent and the environment.
- **Deterministic vs. Stochastic**: State transitions can be deterministic (certain outcomes) or stochastic (probabilistic outcomes), depending on the presence of uncertainties like wind.

**Note**: Creating a table of state transitions could be useful for visualizing deterministic scenarios, although it may not capture the full complexity of probabilistic cases.

### State Transition Probability

Probability is introduced to describe transitions in scenarios where outcomes are uncertain. In deterministic cases, the probability of moving from one state to another given a particular action is either 0 or 1. However, in stochastic environments, this becomes more nuanced:
- **Example**: If there's a chance of wind affecting movement, the probability of moving from \(s_1\) to \(s_2\) might be 0.5, with another 0.5 chance of being blown to \(s_5\).

**Expression**:
```plaintext
P(s'|s, a) = 
- 1, if deterministic and s' = s2
- 0.5, if stochastic and s' = s2 or s' = s5
```

### Policy

- **Definition**: A policy is a strategy that dictates which action the agent should take in each state.
- **Representation**: This can be visually represented by arrows indicating directions, or mathematically by \(\pi\), which denotes the probability of taking a certain action in a given state.
- **Deterministic vs. Stochastic**: Policies can be fixed, where an action is always the same, or probabilistic, where different actions might be taken depending on certain probabilities.

**Illustration Needed**: I should sketch a diagram showing policy arrows for each state to better grasp how policies guide movement across the grid.

### Policy Execution

When implementing these concepts, particularly in programming, I need to consider how to execute policies that involve probabilistic decisions:
- **Implementation**: This can be done through random sampling. For instance, if a policy assigns a 0.5 probability to actions \(a_2\) and \(a_3\), a random number can be used to choose between them.
- **Example**: In state \(s_1\), the policy might dictate:
  ```plaintext
  π(a|s) = 
  - 0.5, if a = a2 or a = a3
  - 0, otherwise
  ```