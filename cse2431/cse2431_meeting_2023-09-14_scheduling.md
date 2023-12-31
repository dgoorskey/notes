# Scheduling
- https://en.wikipedia.org/wiki/Scheduling_(computing)

## Ready queue
- where processes wait to get cpu time
- **arrival time:** when a process enters the ready queue
    - changes the waiting time!

## First come first serve (FCFS) algorithm
- non-preemptive
- run each progress completely before running other processes, in the order they arrived
- `px_wait_time = px_start_time - px_arrival_time`
- `avg_wait_time = (p1_wait_time + p2_wait_time + p3_wait_time + ...) / num_processes`
- only switch off processes when they do IO operations
    - they get moved into the IO queue
- used by batch systems - susceptible to convoy effects

## Convoy effects
- when many IO-bound processes and 1 CPU-bound process arrive
- IO-bound processes pass through ready queue and go to IO queue
- CPU-bound process runs on the cpu until completion
- IO-bound processes are forced to wait

## Shortest job first (SJF) algorithm
- https://en.wikipedia.org/wiki/Shortest_job_next
- non-preemptive
- processes are arranged in the ready queue according to their estimated processing time
- need to estimate processing time
- also used by batch systems
- susceptible to process starvation (one long process is continuously blocked by many short processes)
- optimal only if all jobs are available at the start

## Preemptive SJF
- SJF but preemptive
- remaining time of the process is used
    - if the current process and another process have the same remaining time, the current process will stay on the CPU to prevent the overhead of a context switch

## Scheduling on interactive systems
- **quantum:** an interval of time
    - scheduling decisions made at beginning of each quantum
- algorithms:
    - priority queue
    - round robin
    - multi-queue + multi-level feedback
    - shortest process time (not covered)
    - guaranteed scheduling (not covered)
    - lottery scheduling (not covered)
    - fair sharing scheduling (not covered)
  
## Priority queue algorithm
- processes have a priority
- FCFS within each priority
- suffers from priority inversion problems
- smaller number = higher priority
- preemptive

## Priority inversion problem
- high priority process needs to access a resource being locked by a low priority process
- high priority process needs to wait for low priority process, but high priority process is getting all the CPU time
- **priority inheritance:** a solution to the priority inversion problem. whenever a process accesses a resource, it temporarily gains the max priority of all processes that are waiting to access that resource

## Round robin algorithm
- processes get a fixed amount of cpu time
- high overhead, especially for a small time unit
- waiting times are longer

## Multi-queue scheduling
- using multiple queues
