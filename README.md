# CPU-Scheduling-Algorithms-Simulator
A configurable simulator for classic CPU scheduling algorithms with clear metrics, Gantt charts, and reproducible experiments.
✨ Features

Implements multiple schedulers:

FCFS, SJF (Non‑Preemptive & Preemptive/SRTF)

Priority (Non‑Preemptive & Preemptive)

Round Robin (configurable quantum)

Computes standard metrics:

Waiting Time, Turnaround Time, Response Time, Throughput, CPU Utilization

Gantt chart (ASCII) and tabular outputs

Deterministic simulation with seeded random input (optional)

Import/Export JSON/CSV workloads

Clean, modular design for adding new algorithms

📦 Project Structure
cpu-scheduling-sim/
├─ src/
│  ├─ main.(cpp|py)
│  ├─ schedulers/
│  │  ├─ fcfs.(cpp|py)
│  │  ├─ sjf.(cpp|py)
│  │  ├─ srtf.(cpp|py)
│  │  ├─ priority_np.(cpp|py)
│  │  ├─ priority_p.(cpp|py)
│  │  └─ rr.(cpp|py)
│  ├─ core/
│  │  ├─ process.(hpp|py)
│  │  ├─ simulator.(hpp|py)
│  │  └─ metrics.(hpp|py)
├─ data/
│  ├─ examples.csv
│  └─ examples.json
├─ tests/
│  ├─ unit_*.*
│  └─ golden_outputs/
├─ docs/
│  └─ gantt_examples.md
└─ README.md

🧠 Algorithms (Quick Notes)

FCFS: Non‑preemptive, queue by arrival time.

SJF (NP): Pick shortest burst among arrived; ties → arrival/prio rule.

SRTF (Preemptive SJF): Preempt if a process arrives with smaller remaining time.

Priority (NP/P): Select highest priority; preemptive variant allows preemption on higher priority arrival.

Round Robin: Time‑sharing with quantum q; context switches on expiry/finish.

Assumptions (configurable): Context switch cost (default 0), priorities: lower number = higher priority, arrivals at t ≥ 0.

# CPU Scheduling Algorithms Simulator

This project is a C++ implementation of CPU scheduling algorithms.  
Currently implemented:  
- First Come First Serve (FCFS)

## Features
- Calculates Waiting Time, Turnaround Time, and Response Time
- Displays Gantt Chart
- Provides Average performance metrics

## Example Run
Input:
3
P1 0 4
P2 1 3
P3 2 1

Output:
Gantt Chart:
| P1 | P2 | P3 |

PID   Arr  Burst  Start  Finish  Wait  Turnaround  Response
P1    0    4      0      4       0     4          0
P2    1    3      4      7       3     6          3
P3    2    1      7      8       5     6          5

Average Waiting Time: 2.67  
Average Turnaround Time: 5.33  
Average Response Time: 2.67  

## How to Run
1. Compile the code:  
   `g++ main.cpp -o scheduler`
2. Run the program:  
   `./scheduler`

