# Mini-Courier Planner

<p align="center">
  <img src="https://img.shields.io/badge/Python-3.9%2B-3776AB?style=for-the-badge&logo=python&logoColor=white" alt="Python">
  <img src="https://img.shields.io/badge/DAA-Capstone-orange?style=for-the-badge" alt="DAA Capstone">
  <img src="https://img.shields.io/badge/Algorithms-4-blueviolet?style=for-the-badge" alt="Algorithms">
  <img src="https://img.shields.io/badge/Dependencies-None-success?style=for-the-badge" alt="Dependencies">
</p>

<p align="center">
  <strong>An Algorithm-Driven Courier Delivery Planning and Optimization System</strong>
  <br>
  Integrating Sorting, Dynamic Programming, Graph Algorithms and Approximation Techniques.
</p>

<p align="center">
  <a href="#overview">Overview</a> •
  <a href="#features">Features</a> •
  <a href="#algorithms">Algorithms</a> •
  <a href="#installation">Installation</a> •
  <a href="#execution">Execution</a> •
  <a href="#testing">Testing</a> •
  <a href="#documentation">Documentation</a>
</p>

---

## Overview

**Mini-Courier Planner** is a Python-based application developed to demonstrate the practical application of Design and Analysis of Algorithms (DAA) through a simplified courier delivery optimization problem.

The system processes parcel information, vehicle weight capacity and a weighted road network to generate a delivery plan. It combines multiple algorithmic approaches to prioritize parcels, select a valuable combination of packages, calculate shortest paths and construct an approximate delivery tour.

The project demonstrates how different algorithmic techniques can work together to solve a real-world-inspired optimization problem.

## Features

- **Intelligent Parcel Prioritization:** Organizes parcels by descending priority, earliest deadline and parcel ID.
- **Optimal Package Selection:** Uses 0/1 Knapsack Dynamic Programming to maximize parcel value within vehicle capacity.
- **Weighted Graph Modeling:** Represents the road network using an undirected adjacency-list graph.
- **Shortest Path Computation:** Implements Dijkstra's algorithm with a priority queue.
- **Approximate Route Planning:** Uses the Nearest-Neighbor TSP heuristic to visit selected destinations and return to the depot.
- **Performance Benchmarking:** Measures sorting, knapsack and Dijkstra execution times across different input sizes.
- **CSV-Based Input:** Processes parcel and road network datasets through CSV files.
- **Automated Unit Testing:** Validates the core algorithms and delivery route behavior.
- **Report Generation:** Saves the generated delivery plan and benchmark results in the output directory.

## Algorithms

| Algorithm | Application | Time Complexity |
|---|---|---|
| Comparison Sorting | Parcel prioritization | O(n log n) |
| 0/1 Knapsack DP | Capacity-constrained parcel selection | O(nW) |
| Dijkstra's Algorithm | Shortest path calculation | O((V + E) log V) |
| Nearest-Neighbor TSP | Approximate delivery tour | O((k + 1)(V + E) log V) |

### Algorithmic Implementation

**1. Comparison Sorting**

Parcels are sorted using three criteria:
- Higher priority first.
- Earlier delivery deadline first.
- Parcel ID in ascending order for deterministic tie-breaking.

**2. 0/1 Knapsack Dynamic Programming**

The algorithm selects a combination of parcels that maximizes their total value without exceeding the vehicle's weight capacity. Each parcel is either selected completely or excluded.

**3. Dijkstra's Shortest Path Algorithm**

The road network is represented as a weighted, undirected graph. Dijkstra's algorithm calculates the shortest distances from the depot using a min-priority queue.

**4. Nearest-Neighbor TSP Heuristic**

The system repeatedly selects the nearest unvisited delivery destination using shortest-path distances. After visiting all selected destinations, it returns to the depot.

This is a heuristic approach and does not guarantee the globally optimal Traveling Salesperson Problem solution.

**5. Performance Benchmarking**

The benchmark module measures execution times for sorting, knapsack dynamic programming and Dijkstra's algorithm. Results are stored in CSV format for further analysis.

## Technology Stack

| Technology | Purpose |
|---|---|
| Python 3.9+ | Core application development |
| `heapq` | Priority queue implementation |
| `csv` | Dataset processing |
| `dataclasses` | Structured parcel representation |
| `argparse` | Command-line configuration |
| `pathlib` | File and directory handling |
| `unittest` | Automated testing |

**External Dependencies:** None. The application uses Python's standard library.

## Project Architecture

The application follows a modular structure that separates algorithm implementation, data processing, planning logic, benchmarking and testing.

```text
Mini-Courier-Planner/
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
│   ├── delivery_plan.txt
│   └── benchmark_results.csv
│
├── tests/
│   └── test_algorithms.py
│
├── Mini-Courier-Planner-Report.pdf
├── PROJECT_REPORT.md
├── README.md
└── requirements.txt
```

*Note: The files inside `outputs/` are generated when the application runs.*

## Installation

### Prerequisites

- Python 3.9 or newer
- Git
- Visual Studio Code (recommended)

### 1. Clone the Repository

```bash
git clone https://github.com/aradhana-bit/Mini-Courier-Planner.git
```

### 2. Navigate to the Project Directory

```bash
cd Mini-Courier-Planner
```

### 3. Verify Python Installation

```bash
python --version
```

No additional package installation is necessary.

## Execution

### Run the Delivery Planner

```bash
python -m courier_planner.main
```

### Run with Performance Benchmarking

```bash
python -m courier_planner.main --benchmark
```

### Specify Vehicle Capacity

```bash
python -m courier_planner.main --capacity 30
```

### Specify Custom Input Files

```bash
python -m courier_planner.main --parcels data/parcels.csv --roads data/roads.csv
```

### Specify a Different Depot

```bash
python -m courier_planner.main --depot DEPOT
```

### Combine Configuration Options

```bash
python -m courier_planner.main --capacity 30 --depot DEPOT --benchmark
```

### Command-Line Arguments

| Argument | Description | Default |
|---|---|---|
| `--parcels` | Path to parcel CSV file | `data/parcels.csv` |
| `--roads` | Path to road network CSV file | `data/roads.csv` |
| `--depot` | Starting and ending depot node | `DEPOT` |
| `--capacity` | Maximum vehicle weight capacity | `25` |
| `--benchmark` | Enables performance benchmarking | Disabled |

## Input Data

The application uses two CSV files stored inside the `data/` directory.

### Parcel Dataset — `parcels.csv`

| Field | Description |
|---|---|
| `parcel_id` | Unique parcel identifier |
| `destination` | Delivery destination node |
| `weight` | Parcel weight in kilograms |
| `priority` | Parcel urgency score |
| `deadline` | Delivery deadline in `YYYY-MM-DD HH:MM` format |
| `value` | Parcel value used by the Knapsack algorithm |

### Road Network — `roads.csv`

| Field | Description |
|---|---|
| `from` | Starting graph node |
| `to` | Connected graph node |
| `distance` | Distance or travel cost between nodes |

Road connections are treated as bidirectional and must have non-negative distances.

## Output

The application generates its results inside the `outputs/` directory.

| Output File | Description |
|---|---|
| `delivery_plan.txt` | Prioritized parcels, selected packages, shortest-path distances and delivery tour |
| `benchmark_results.csv` | Execution-time measurements for the selected algorithms |

The delivery plan includes:
- Prioritized parcel queue.
- Selected parcels and total selected weight.
- Maximum selected parcel value.
- Shortest-path distances from the depot.
- Approximate delivery visit order.
- Expanded road path and total tour distance.

## Testing

The project includes automated unit tests for the core algorithmic components.

### Execute the Test Suite

```bash
python -m unittest discover -s tests -v
```

### Testing Coverage

- Parcel prioritization and sorting order.
- Knapsack capacity constraints and maximum value.
- Dijkstra shortest distances and path reconstruction.
- Delivery tour construction and depot return.

## Performance Analysis

The benchmarking module evaluates algorithm execution time across increasing parcel counts.

| Algorithm | Benchmark Objective |
|---|---|
| Sorting | Evaluate parcel prioritization performance |
| Knapsack DP | Measure dynamic programming execution time |
| Dijkstra | Measure shortest-path computation time |

Benchmark measurements depend on the computer, operating system and Python environment. Use the generated CSV file for performance charts and academic analysis.

## Limitations

- Road distances are illustrative sample values, not live GPS or map data.
- The application plans deliveries for a single vehicle.
- Traffic conditions and delivery time windows are not considered.
- Knapsack optimization uses integer weight capacity.
- The Nearest-Neighbor heuristic does not guarantee an optimal TSP route.

## Future Scope

- Integration with real-world mapping and navigation APIs.
- Live traffic and distance estimation.
- Multiple vehicle and route optimization.
- Delivery time-window constraints.
- Comparison of route heuristics such as 2-opt.
- Graphical user interface and interactive route visualization.

## Documentation

The repository includes additional project documentation:

- [Project Report (PDF)](Mini-Courier-Planner-Report.pdf)
- [Detailed Project Report (Markdown)](PROJECT_REPORT.md)

## Academic Context

This project was developed as a **Design and Analysis of Algorithms (DAA) Capstone Project** to demonstrate the integration of fundamental algorithmic techniques into a practical optimization workflow.

It provides an implementation-focused study of sorting, dynamic programming, graph traversal, shortest-path computation, approximation algorithms and performance analysis.

---

<p align="center">
  <strong>Mini-Courier Planner</strong>
  <br>
  Algorithmic Thinking. Optimized Deliveries.
  <br><br>
  Developed as a DAA Capstone Project.
</p>
