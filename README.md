# CSE-316
A C-program written to simulate the performance of the Round Robin scheduling algorithm, and compares the results to that of an ideal scenario of a perfect scheduler.
## Approach:

### Program Design and Implementation
We designed and implemented a simulation program using the C/C++ programming language. The program is organized into modular components to ensure maintainability and readability. It includes data structures to represent processes, the scheduler, and other essential components.
### Process Generation
We utilized a random number generator to generate random arrival times and CPU burst times for a set of processes (for simplicity, the process count has been limited to 5 processes). These generated values are used to simulate the behavior of processes in a real-world scenario.
### Round Robin Scheduling Algorithm
The core of the simulation program is the Round Robin scheduling algorithm. We implemented this algorithm, which maintains a queue of processes and a time quantum. The algorithm selects the next process from the queue and executes it for the specified time quantum.
### Simulation Loop
The program runs within a simulation loop until a predefined time limit is reached. During each iteration of the loop, the state of processes, the scheduler, and the simulation time are updated.

## Pseudocode:

Step 1: Set parameters and seed random number generator
    - num_processes = 10
    - time_quantum = 2
    - total_time_units = 100
    - Seed random number generator with current time

Step 2: Create an array to store process structures
    - Create an array of Process structures with size num_processes

Step 3: Initialize processes with random arrival times and burst times
    For i = 0 to num_processes - 1:
        - Assign a unique process_id (i + 1)
        - Generate a random arrival_time between 0 and 20
        - Generate a random burst_time between 1 and 10
        - Set remaining_time to burst_time
        - Set waiting_time to 0
        - Set turnaround_time to 0

Step 4: Initialize variables for simulation
    - Set current_time to 0
    - Set completed_processes to 0

Step 5: Execute the Round Robin scheduling algorithm
    While (current_time < total_time_units) and (completed_processes < num_processes):
        For i = 0 to num_processes - 1:
            If processes[i].remaining_time > 0:
                If processes[i].remaining_time > time_quantum:
                    - Run the process for a time quantum (time_quantum)
                    - Update current_time and remaining_time
                Else:
                    - Complete the process
                    - Update current_time
                    - Calculate waiting_time for the process
                    - Set remaining_time to 0
                    - Increment completed_processes

Step 6: Calculate turnaround time for each process
    For i = 0 to num_processes - 1:
        - Calculate turnaround_time for each process as waiting_time + burst_time


Step 7: Calculate and display the average waiting time and turnaround time
    - Initialize total_waiting_time and total_turnaround_time to 0
    For i = 0 to num_processes - 1:
        - Add processes[i].waiting_time to total_waiting_time
        - Add processes[i].turnaround_time to total_turnaround_time
    - Calculate avg_waiting_time = total_waiting_time / num_processes
    - Calculate avg_turnaround_time = total_turnaround_time / num_processes
    - Display "Average Waiting Time: " + avg_waiting_time
    - Display "Average Turnaround Time: " + avg_turnaround_time

Step 8: Calculate the ideal scenario results
    - In an ideal scenario, all processes are scheduled with no waiting time
    - Calculate ideal_avg_waiting_time = 0
    - Calculate ideal_avg_turnaround_time as the average burst_time of all processes

Step 9: Display the ideal average waiting time and ideal average turnaround time
    - Display "Ideal Average Waiting Time: " + ideal_avg_waiting_time
    - Display "Ideal Average Turnaround Time: " + ideal_avg_turnaround_time

Step 10: Compare the results with the ideal scenario
    - Calculate the differences between actual and ideal waiting times and turnaround times
    - Display comparisons and improvements or increases in waiting and turnaround times
