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

📥 Input Format
CSV
pid,arrival,burst,priority
P1,0,8,2
P2,1,4,1
P3,2,9,3
P4,3,5,2

JSON
{
  "processes": [
    {"pid": "P1", "arrival": 0, "burst": 8, "priority": 2},
    {"pid": "P2", "arrival": 1, "burst": 4, "priority": 1},
    {"pid": "P3", "arrival": 2, "burst": 9, "priority": 3},
    {"pid": "P4", "arrival": 3, "burst": 5, "priority": 2}
  ]
}

🚀 Build & Run
C++ (example)
# Build
g++ -std=c++17 -O2 -o scheduler \
  src/main.cpp src/core/*.cpp src/schedulers/*.cpp

# Run
./scheduler --algo srtf --input data/examples.csv --format csv --ctx 0 --quantum 3

Python (example)
# (Optional) create venv and install deps if any
python src/main.py --algo rr --input data/examples.json --format json --quantum 2


Common CLI Options

--algo        fcfs|sjf|srtf|priority-np|priority-p|rr
--input       path to CSV/JSON
--format      csv|json
--quantum     integer (RR only)
--ctx         context switch cost (time units)
--seed        integer for synthetic generation
--export      path to write results (csv|json)
--gantt       print gantt chart (true/false)

📊 Sample Output

Gantt (SRTF)

0   1   3     7     12    17
| P1 | P2 | P1 |  P4  |  P3  |


Metrics Table

PID  Arrival  Burst  Start  Finish  Waiting  Turnaround  Response
P1        0      8      0       7        0          7         0
P2        1      4      1       3        0          2         0
P3        2      9     12      21        1          19        10
P4        3      5      7      12        2          9         4
---------------------------------------------------------------
AVG Waiting: 0.75   AVG Turnaround: 9.25   AVG Response: 3.5
Throughput: 4/21 = 0.1905   CPU Utilization: 100.00%



This project is licensed under the MIT License.

🙌 Acknowledgements

Classic OS texts and lecture notes inspired the structure and test cases.
