# CPU Scheduling Simulator

A C++ simulator that compares process scheduling algorithms on randomly generated workloads.

## Algorithms

- **FCFS** — First Come, First Served
- **RR1 / RR4** — Round Robin with quantum 1 and quantum 4
- **SPN** — Shortest Process Next
- **FB** — Multilevel Feedback (dynamic priorities)

## Metrics

For every algorithm and round, the program reports the averages of:

- **T** — turnaround time (from arrival to completion)
- **E** — waiting time (time spent in the ready queue)
- **P** — penalty ratio (turnaround time / burst time)

It also prints an **execution timeline**, one letter per time unit (`-` means the CPU was idle).

## How it works

1. Generate random processes (arrival time and burst time).
2. Sort them by arrival time.
3. Simulate the CPU one time unit at a time for each algorithm.
4. Record which process runs at every step.
5. Compute and print the metrics.

## Run it

```bash
g++ compara_planif.cpp -o compara_planif
./compara_planif
```

```text
- Ronda 1:
C: 2, t=1; D: 2, t=5; B: 3, t=2; E: 3, t=2; A: 7, t=3;
  FCFS: T=6.2, E=3.6, P=2.57333
  --CDDDDDBBEEAAA
  RR1: T=6.4, E=3.8, P=2.28667
  --CDBEDBEADADAD
  SPN: T=4.6, E=2, P=1.52
  --CBBEEAAADDDDD
```

## Challenges

- Handling arrival times and idle CPU periods correctly.
- Managing the ready queue in Round Robin.
- Implementing the multiple queues of the feedback scheduler.

*Authors: Hugo Chacón, Sebastián Valdez.*
