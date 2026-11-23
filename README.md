# Mini-Courier Planner

<p align="center">
  A Python-based courier delivery optimization system implementing sorting, dynamic programming, graph algorithms, and approximation algorithms.
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Python-3.9%2B-blue?logo=python" alt="Python">
  <img src="https://img.shields.io/badge/Algorithms-DAA-orange" alt="Algorithms">
  <img src="https://img.shields.io/badge/Testing-Unittest-green" alt="Testing">
  <img src="https://img.shields.io/badge/Dependencies-Standard%20Library-lightgrey" alt="Dependencies">
</p>

---

## Overview

Mini-Courier Planner is a Python application developed to demonstrate the practical implementation of Design and Analysis of Algorithms (DAA) through a courier delivery optimization problem.

The application processes parcel information, vehicle capacity, and a weighted road network to generate an optimized parcel selection and delivery route.

It combines multiple algorithmic techniques to prioritize parcels, maximize delivery value, calculate shortest paths, and construct an approximate delivery tour.

## Key Features

- **Parcel Prioritization:** Sorts parcels based on priority, delivery deadline, and parcel ID.
- **0/1 Knapsack Optimization:** Selects the most valuable combination of parcels within the vehicle's weight capacity.
- **Graph Representation:** Models the road network using a weighted, undirected graph.
- **Shortest Path Calculation:** Implements Dijkstra's algorithm to determine shortest paths from the depot.
- **Delivery Route Optimization:** Uses the nearest-neighbor TSP heuristic to construct a delivery tour.
- **Performance Benchmarking:** Evaluates sorting, knapsack dynamic programming, and Dijkstra's algorithm across increasing input sizes.
- **CSV Data Processing:** Reads parcel and road network information from structured CSV files.
- **Automated Testing:** Includes unit tests to verify the correctness of core algorithms.

## Technology Stack

| Technology | Purpose |
|---|---|
| Python 3.9+ | Application development |
| Python Standard Library | Core functionality and utilities |
| CSV | Input data management |
| Heap Queue (`heapq`) | Priority queue for Dijkstra's algorithm |
| `unittest` | Automated testing |
| Dynamic Programming | Parcel selection optimization |
| Graph Algorithms | Shortest path calculation |
| Approximation Algorithms | Delivery route construction |

## Application Structure

```text
mini_courier_planner/
│
├── courier_planner/
│   ├── __init__.py
│   ├── algorithms.py
│   ├── benchmark.py
│   ├── io_utils.py
│   ├── main.py
│   ├── models.py
│   └── planner.py
│
├── data/
│   ├── parcels.csv
│   └── roads.csv
│
├── outputs/
│
├── tests/
│   └── test_algorithms.py
│
├── README.md
├── requirements.txt
└── PROJECT_REPORT.md
```

## Getting Started

### Prerequisites

- Python 3.9 or newer
- Git
- Visual Studio Code (recommended)

No third-party Python packages are required.

### Clone the Repository

```bash
git clone https://github.com/aradhana-bit/Mini-Courier-Planner.git
cd Mini-Courier-Planner
```

### Verify Python Installation

```bash
python --version
```

### Run the Application

```bash
python -m courier_planner.main
```

### Run with Performance Benchmarking

```bash
python -m courier_planner.main --benchmark
```

### Run with Custom Vehicle Capacity

```bash
python -m courier_planner.main --capacity 30 --benchmark
```

### Run Unit Tests

```bash
python -m unittest discover -s tests -v
```

## Algorithms Implemented

| Algorithm | Application | Time Complexity |
|---|---|---|
| Comparison Sorting | Parcel prioritization | O(n log n) |
| 0/1 Knapsack DP | Parcel selection | O(nW) |
| Dijkstra's Algorithm | Shortest path calculation | O((V+E) log V) |
| Nearest-Neighbor TSP | Approximate delivery tour | O(k(V+E) log V) |

### Algorithmic Concepts

**1. Sorting Algorithms**

Parcels are prioritized using comparison-based sorting according to priority, deadline, and parcel ID.

**2. Dynamic Programming**

The 0/1 Knapsack algorithm determines the combination of parcels that maximizes total value without exceeding vehicle capacity.

**3. Graph Algorithms**

The road network is represented as a weighted, undirected graph. Dijkstra's algorithm calculates shortest paths from the depot.

**4. Approximation Algorithms**

The nearest-neighbor heuristic constructs an approximate Traveling Salesperson Problem (TSP) tour, including the return journey to the depot. It does not guarantee a globally optimal route.

**5. Performance Analysis**

Benchmarking evaluates the execution time of selected algorithms across increasing input sizes to demonstrate their computational behavior.

## Output Files

The application generates its output inside the `outputs/` directory.

| File | Description |
|---|---|
| `delivery_plan.txt` | Generated parcel selection and delivery plan |
| `benchmark_results.csv` | Performance benchmarking results |

These files are generated when the corresponding application modes are executed.

## Project Objectives

- Apply theoretical DAA concepts to a practical optimization problem.
- Understand sorting and dynamic programming through implementation.
- Explore weighted graphs and shortest path algorithms.
- Demonstrate approximation techniques for route planning.
- Analyze algorithmic performance through benchmarking.
- Develop modular and maintainable Python code.

## Purpose

This project was developed as an academic capstone project for the Design and Analysis of Algorithms (DAA) course.

It demonstrates how fundamental algorithmic techniques can be combined to address a simplified courier delivery optimization problem.

**Note:** The road distances are illustrative sample values and do not represent live geographical or GPS-based distances.

---

<p align="center">
  Developed as a Design and Analysis of Algorithms Capstone Project.
</p>

<p align="center">
  <strong>Mini-Courier Planner</strong>
  <br>
  Algorithmic Thinking. Optimized Deliveries.
</p>
