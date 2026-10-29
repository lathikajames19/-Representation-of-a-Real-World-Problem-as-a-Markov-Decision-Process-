# -Representation-of-a-Real-World-Problem-as-a-Markov-Decision-Process

## Aim

To represent a Smart Traffic Signal Control System as a Markov Decision Process (MDP) by defining its states, action space, transition probabilities, and reward function, and implementing the model using Python.

## Problem Statement

### Problem Description

A smart traffic signal system monitors the traffic level at a road junction. Based on the traffic condition, the system decides whether to keep the green signal, switch the signal, or extend the green signal time. The goal is to reduce traffic congestion and waiting time by selecting the best action.

## MDP Components

A Markov Decision Process is represented as:


MDP = (S, A, P, R, gamma)


Where:

| Symbol | Meaning |
|---|---|
| S | Set of states |
| A | Set of actions |
| P | Transition probability function |
| R | Reward function |
| gamma | Discount factor |

---

## State Space

The state space represents the possible traffic conditions.

Statespace format:

```text
S = {
    0: "Low Traffic",
    1: "Medium Traffic",
    2: "High Traffic"
}
```



---

## Sample State

A sample state is one specific example from the state space.

Medium Traffic (State 1)

When the traffic signal system detects medium traffic, it can keep the green signal, switch the signal, or extend the green time. It selects an action based on the expected reward and traffic condition.

---

## Action Space

The action space represents the actions available to the traffic signal system.

Example format:

```text
A = {
    0: "Keep Green Signal",
    1: "Switch Signal",
    2: "Extend Green Time"
}
```


---

## Sample Action

Keep Green Signal

When the traffic is low, the system keeps the green signal. When the traffic is high, it extends the green signal time to reduce congestion. The system can also switch the signal to allow vehicles on another road to move.



---

## Transition Probability

If the traffic is Low and the system chooses Keep Green Signal, the traffic remains Low with probability 0.8.

P(Low Traffic | Low Traffic, Keep Green Signal) = 0.8

If the traffic is High and the system chooses Extend Green Time, the traffic reduces to Medium with probability 0.7.

P(Medium Traffic | High Traffic, Extend Green Time) = 0.7

The transition probability explains how traffic conditions change from one state to another after an action is taken.

General form:

P(Next State | Current State,Action)


This means:
Probability of reaching the next traffic state after taking an action in the current traffic state.

---

## Reward Function

```text
Traffic congestion reduced       = +10
Traffic condition maintained     = +2
Traffic congestion increased     = -5
```
General form:


R(s,a,s')

```
+10 – When traffic congestion is reduced.
+5 – When vehicle waiting time is reduced.
-10 – When traffic congestion increases.

```

---

## Graphical Representation

<img width="1163" height="1353" alt="86251551-35e7-4903-8a4b-578a4a730ffc" src="https://github.com/user-attachments/assets/37dcd78c-a69a-41b0-8e04-84246c833138" />

---

## Python Representation


```python
# MDP Representation using Python
# Smart Traffic Signal Control

# States
# 0 = Low Traffic
# 1 = Medium Traffic
# 2 = High Traffic

# Actions
# 0 = Keep Green Signal
# 1 = Switch Signal
# 2 = Extend Green Time

P = {
    0: {
        0: [(0.8, 0, 2, False),
            (0.2, 1, -5, False)],

        1: [(0.7, 0, 2, False),
            (0.3, 1, -5, False)],

        2: [(0.9, 0, 2, False),
            (0.1, 1, -5, False)]
    },

    1: {
        0: [(0.6, 1, 2, False),
            (0.4, 2, -5, False)],

        1: [(0.7, 0, 10, False),
            (0.3, 1, 2, False)],

        2: [(0.8, 0, 10, False),
            (0.2, 1, 2, False)]
    },

    2: {
        0: [(0.7, 2, -5, False),
            (0.3, 1, 2, False)],

        1: [(0.6, 2, -5, False),
            (0.4, 1, 2, False)],

        2: [(0.7, 1, 10, False),
            (0.3, 2, -5, False)]
    }
}

print("Smart Traffic Signal Control MDP\n")

for state in P:
    print("State:", state)
    for action in P[state]:
        print(" Action:", action)
        print(" Outcomes:", P[state][action])
    print()

print("Name: Lathika K")
print("Register Number: 212224230140")

```
---
## Output

<img width="498" height="461" alt="1b0072af-972a-4ed9-b46b-3c69908a9146" src="https://github.com/user-attachments/assets/a0ca8855-6f63-473d-a3a7-b6d48ff04a61" />

---

## Result

Thus, the Smart Traffic Signal Control System was successfully represented as a Markov Decision Process with three states: Low Traffic, Medium Traffic, and High Traffic, and three actions: Keep Green Signal, Switch Signal, and Extend Green Time. The transition probabilities, reward function, and Python implementation were defined successfully to model traffic congestion reduction.


---
