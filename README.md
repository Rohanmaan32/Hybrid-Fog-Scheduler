# Task Scheduling Optimization in Fog-Cloud Environments

## Overview
This project implements and compares multiple task scheduling algorithms for fog-cloud computing environments. The goal is to optimize key performance metrics including makespan, energy consumption, processing cost, and overall fitness value in a heterogeneous computing infrastructure.

## Project Description
Task scheduling in fog-cloud environments is a critical optimization problem. With the proliferation of edge computing and cloud services, efficiently distributing computational tasks across fog nodes (edge) and cloud nodes (remote data centers) is essential for:
* Minimizing latency and response times (makespan)
* Reducing energy consumption
* Decreasing processing costs
* Meeting deadline constraints

This project provides implementations of 11 different scheduling algorithms, ranging from simple heuristics to advanced metaheuristic approaches.

## Implemented Algorithms

### 1. Random Scheduling
* Baseline algorithm that randomly assigns tasks to available nodes
* Used as a benchmark for comparison

### 2. Performance to Cost (P2C)
* Compares two randomly selected nodes
* Selects the node with better performance characteristics
* Simple but effective heuristic approach

### 3. Genetic Algorithm (GA)
* Population-based evolutionary algorithm
* Uses crossover and mutation operators
* **Parameters:**
  * Population size: 150
  * Iterations: 1000
  * Mutation rate: 0.05
  * Elite individuals: 2

### 4. Energy-efficient and Cost-aware Method (EMA) / PSGS1
* Considers both energy efficiency and cost efficiency metrics
* Normalizes node attributes for fair comparison
* Selects nodes based on makespan prediction and efficiency metrics

### 5. Simulated Annealing (SA)
* Temperature-based metaheuristic algorithm
* Gradually reduces search space using cooling rate
* **Parameters:**
  * Initial temperature: 1000.0
  * Final temperature: 1.0
  * Cooling rate: 0.9
  * Iterations per temperature: 1000

### 6. GA + EMA (Hybrid)
* Combines genetic algorithm with EMA refinement
* Applies EMA-based local search to elite solutions
* Enhanced exploration and exploitation balance

### 7. Particle Swarm Optimization (PSO)
* Swarm intelligence-based algorithm
* Particles move through solution space toward best positions
* **Parameters:**
  * Number of particles: 50
  * Max iterations: 100
  * Inertia weight: 0.5
  * Cognitive coefficient: 1.5
  * Social coefficient: 1.5

### 8. Enhanced Hybrid Genetic Algorithm (E-HGA)
* Advanced genetic algorithm with local search refinement
* Combines genetic operators with hill climbing
* **Parameters:**
  * Population size: 100
  * Iterations: 500
  * Mutation rate: 0.05
  * Elite individuals: 5

### 9. Base PSGS (Performance and Service-level aware Green Scheduling)
* Deadline-aware scheduling algorithm
* Maintains a Deadline Satisfaction List (DSL)
* Offloads non-deadline-meeting tasks to cloud
* Focuses on deadline compliance

### 10. Hybrid PSGS + PSO
* Combines PSGS deadline awareness with PSO optimization
* Hybrid approach leveraging strengths of both methods
* **Parameters:**
  * Swarm size: 20
  * Iterations: 30
  * Inertia weight: 0.5

## Performance Metrics

### Evaluated Metrics

* **Makespan (ms)**
  * Total time to complete all tasks
  * Calculated from maximum node available time
  * *Lower is better*
* **Energy Consumption (units)**
  * Total energy used across all nodes
  * Considers both active and idle power consumption
  * **Formula:** `E = (available_time × max_power) + ((makespan - available_time) × min_power)`
  * *Lower is better*
* **Processing Cost (units)**
  * Cumulative cost of task execution
  * Based on task size and node processing cost coefficient
  * *Lower is better*
* **Fitness Value**
  * Weighted combination of normalized metrics
  * **Formula:** `Fitness = 0.34 × (min_energy / energy) + 0.33 × (min_cost / cost) + 0.33 × (min_makespan / makespan) × 1000`
  * *Higher is better*

## System Architecture

### Computing Nodes

**Fog Nodes (Edge Computing)**
* **Processing capacity:** 500-1500 units
* **Memory:** 150-250 GB
* **Bandwidth:** 10-1000 Mbps
* **Delay:** 1-10 ms
* **Max power consumption:** 40-100 W
* **Processing cost coefficient:** 0.1-0.4

**Cloud Nodes (Remote Data Centers)**
* **Processing capacity:** 3000-5000 units
* **Memory:** 8192-65536 GB
* **Bandwidth:** 100-10000 Mbps
* **Delay:** 200-500 ms
* **Max power consumption:** 200-400 W
* **Processing cost coefficient:** 0.7-1.0

### Task Characteristics
Tasks are randomly generated in three categories:

| Category | Size (units) | Deadline (ms) |
|----------|--------------|---------------|
| Small    | 100-10000    | 100-500       |
| Medium   | 1028-4280    | 500-2500      |
| Large    | 5123-9784    | 2500-10000    |

## Experimental Results
The project compares algorithm performance across multiple metrics. Key findings from generated graphs:
* **Makespan Performance:** E-HGA and GA-based approaches show competitive results
* **Energy Efficiency:** EMA and PSGS algorithms excel at energy optimization
* **Cost Efficiency:** Different algorithms show varying cost characteristics
* **Overall Fitness:** E-HGA and Hybrid PSGS+PSO provide best overall performance

*See latest `graphs/` directory for detailed performance comparisons:*
* `Figure_1.png`: Makespan comparison
* `2.png`, `3.png`, `4.png`: Additional performance metrics

## File Structure
*(Add your project structure here)*

## Usage

### Running the Main Program
The program presents an interactive menu:
```bash
python SchedulerMain.py
