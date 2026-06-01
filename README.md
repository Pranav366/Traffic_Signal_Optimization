# 🚦 Rule-Based Traffic Signal Optimization System

## 📌 Project Overview

The **Rule-Based Traffic Signal Optimization System** is an Artificial Intelligence-based traffic management solution that improves vehicle movement at road intersections using predefined rules and heuristics instead of machine learning algorithms.

The system continuously monitors traffic conditions such as vehicle queue length and waiting time across multiple lanes. Based on the observed traffic state, it dynamically selects the most suitable lane to receive the green signal, helping reduce congestion, minimize delays, and improve overall traffic flow.

This project demonstrates the application of AI concepts including:

* Intelligent Agents
* State Space Representation
* Search Algorithms
* Constraint Satisfaction Problems (CSP)
* Rational Decision Making

---

# 🎯 Objectives

* Reduce traffic congestion at intersections.
* Minimize vehicle waiting time.
* Improve traffic flow efficiency.
* Demonstrate AI-based decision making without machine learning.
* Implement search and CSP techniques for traffic optimization.

---

# 🧠 AI Concepts Used

## 1. Intelligent Agent

The traffic controller acts as an intelligent agent that:

* Perceives the environment through traffic data.
* Evaluates lane congestion.
* Chooses the best action (green signal assignment).
* Updates the environment after each decision.

### Agent Type

* Goal-Based Agent
* Rule-Based Agent
* Rational Agent

---

## 2. Environment Characteristics

| Property        | Type                 |
| --------------- | -------------------- |
| Observability   | Partially Observable |
| Environment     | Dynamic              |
| Agents          | Single Agent         |
| Decision Making | Rational             |
| State Changes   | Continuous           |

---

## 3. State Representation

Each traffic state contains:

```python
{
    "North": queue_length,
    "South": queue_length,
    "East": queue_length,
    "West": queue_length
}
```

Additional information:

* Vehicle queue length
* Waiting time per lane

---

## 4. Actions

Possible actions available to the agent:

```python
["North", "South", "East", "West"]
```

Selecting a lane means assigning a green signal to that lane.

---

## 5. Transition Model

When a lane receives a green signal:

1. Vehicles pass through the intersection.
2. Queue length decreases.
3. Waiting time for that lane resets.
4. Waiting times for other lanes increase.

---

## 6. Goal State

The objective is to:

* Minimize traffic congestion.
* Reduce average waiting time.
* Maintain smooth traffic movement.

---

# 🏗️ Project Structure

```text
Traffic_Signal_Optimization/
│
├── config.py
│
├── core/
│   ├── actions.py
│   ├── environment.py
│   └── rules.py
│
├── csp/
│   └── scheduler.py
│
├── search/
│   ├── bfs.py
│   ├── dfs.py
│   └── greedy.py
│
├── utils/
│   └── logger.py
│
├── main.py
│
└── README.md
```

---

# ⚙️ Modules Description

## config.py

Stores system-wide configurations:

```python
LANES = ["North", "South", "East", "West"]

VEHICLE_PASS_RATE = 5

MAX_GREEN_TIME = 30
```

---

## actions.py

Defines all valid traffic actions.

```python
def get_possible_actions():
    return LANES
```

---

## environment.py

Represents the traffic environment.

Responsibilities:

* Generate random traffic queues.
* Track waiting times.
* Update traffic conditions.
* Apply green signals.

Key Functions:

```python
update_waiting()
apply_green(lane)
is_congested()
get_state()
```

---

## rules.py

Contains heuristic decision-making rules.

```python
choose_best_lane(state)
```

Selects the lane with the maximum queue length.

---

## scheduler.py (CSP)

Implements Constraint Satisfaction Problem concepts.

### Constraints

* Only lanes with vehicles can receive green signals.
* Most congested lane gets higher priority.

Functions:

```python
is_valid()
select_mrv()
schedule()
```

MRV (Minimum Remaining Values) principle is adapted to prioritize highly congested lanes.

---

## bfs.py

Implements Breadth First Search.

Purpose:

* Explore possible signal sequences.
* Analyze future traffic control actions.

```python
bfs_simulate()
```

---

## dfs.py

Implements Depth First Search.

Purpose:

* Explore traffic signal paths recursively.

```python
dfs()
```

---

## greedy.py

Implements Greedy Search.

```python
greedy_step()
```

Chooses the lane with maximum congestion at every step.

---

## main.py

Main simulation driver.

Responsibilities:

* Initialize traffic state.
* Execute traffic optimization.
* Log system activity.
* Display results.

---

# 🔍 Search Algorithms Used

## Greedy Search

### Strategy

Choose the lane with the highest vehicle count.

### Advantages

* Fast
* Simple
* Effective for real-time systems

### Complexity

```text
Time Complexity: O(n)
Space Complexity: O(1)
```

---

## Breadth First Search (BFS)

### Strategy

Explore all possible signal sequences level by level.

### Complexity

```text
Time Complexity: O(b^d)
Space Complexity: O(b^d)
```

Where:

* b = branching factor
* d = depth

---

## Depth First Search (DFS)

### Strategy

Explore one signal sequence completely before backtracking.

### Complexity

```text
Time Complexity: O(b^d)
Space Complexity: O(d)
```

---

# 🔐 Constraint Satisfaction Problem (CSP)

The CSP scheduler determines valid signal assignments.

## Variables

```text
Green Signal Lane
```

## Domain

```text
North
South
East
West
```

## Constraints

* Queue length must be greater than zero.
* Priority given to congested lanes.
* One green signal at a time.

---

# 🔄 Simulation Workflow

```text
Initialize Traffic State
           │
           ▼
Observe Queue Lengths
           │
           ▼
Greedy Search Selects Lane
           │
           ▼
Assign Green Signal
           │
           ▼
Update Traffic State
           │
           ▼
Run CSP Scheduler
           │
           ▼
Repeat Until Completion
```

---

# 📊 Sample Output

```text
INITIAL STATE:
{'North': 20, 'South': 10, 'East': 15, 'West': 8}

--- STEP 1 ---

Green Signal → North

State:
{'North': 15, 'South': 10, 'East': 15, 'West': 8}

CSP Suggestion: North

--- STEP 2 ---

Green Signal → North

State:
{'North': 10, 'South': 10, 'East': 15, 'West': 8}

CSP Suggestion: East

FINAL STATE:
{'North': 5, 'South': 10, 'East': 10, 'West': 8}

# 💡 Features

✅ Rule-Based Traffic Optimization

✅ Intelligent Agent Design

✅ Greedy Search Algorithm

✅ BFS Simulation

✅ DFS Simulation

✅ CSP-Based Scheduling

✅ Dynamic Traffic Environment

✅ Real-Time Decision Making

✅ Waiting Time Tracking

✅ Congestion Detection

---

# 📈 Future Enhancements

* Emergency vehicle prioritization.
* Adaptive green signal timing.
* Multi-intersection coordination.
* Real sensor integration.
* Traffic prediction module.
* Reinforcement Learning comparison.
* Graphical User Interface (GUI).
* Real-time dashboard visualization.

---

# 🎓 Course Outcomes Achieved

## CO1

Formulate real-world traffic management as an AI problem using:

* States
* Actions
* Goals
* Constraints
* Environment representation

## CO2

Implement and analyze search algorithms:

* BFS
* DFS
* Greedy Search

## CO3

Apply CSP techniques for intelligent scheduling and optimization.
