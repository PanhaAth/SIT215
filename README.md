Student ID: `s224529554`
Assessment: `SIT215 Assignment 1 - Problem Solving`
Project Title: `Truck Delivery Navigation System`

## Submission Overview

This submission implements a search-based truck delivery navigation system modelled on the Deakin Burwood campus. The solution is organised around the Assignment 1 task structure and is designed to support the rubric criteria for environment modelling, algorithmic implementation, heuristic reasoning, and clear communication.

## Main Submission Files

- `s224529554.ipynb`
  Main notebook containing the full implementation for Task 1 to Task 4.
- `README.md`
  This file. It explains how to run the notebook and where rubric evidence is located.
- `campus_map.png`
  Visual representation of the Deakin Burwood campus delivery graph.
- `algorithm_results.csv`
  Structured results comparing `A*` and `UCS` on the required evaluation cases.
- `algorithm_comparison.png`
  Visual comparison of nodes expanded and execution time for `A*` and `UCS`.
- `heuristic_results.csv`
  Structured results comparing the baseline heuristic and the enhanced heuristic.
- `heuristic_comparison.png`
  Visual comparison of heuristic performance.

## How This Submission Aligns With The Rubric

### 1. Problem Formulation, Environment Modelling, And Completion

Evidence for this criterion appears mainly in the `Task 1` section of the notebook.

The notebook models the problem as a truck delivery task over a simplified Deakin Burwood campus graph with:

- `22 landmarks`
- `31 weighted path segments`
- static constraints using narrow-road restrictions and truck-height restrictions
- dynamic constraints using delivery-hour and peak-hour rules

The environment model is implemented in the `TruckDeliveryEnvironment` class. The graph structure, path costs, and feasibility checks are all defined there, which supports the rubric requirement that the problem is clearly formulated and represented in a structured way.

### 2. Algorithmic Implementation Competency And Comparison

Evidence for this criterion appears mainly in the `Task 2` and `Task 3` sections of the notebook.

The notebook implements:

- `A*` as the benchmark informed search algorithm
- `UCS` as the uninformed comparison algorithm

The planning problem is represented by the `DeliveryPlanningProblem` class, where each state is modelled as:

- `(location, time, delivered_status)`

This gives the search process enough information to represent movement, time progression, and delivery completion. The notebook then evaluates the algorithms on three required start-goal cases:

- `Gate2 -> DeliveryHub`
- `BuildingJ -> BuildingHD`
- `Library -> Gate1`

The comparison outputs are saved to:

- `algorithm_results.csv`
- `algorithm_comparison.png`

These files provide direct evidence for completeness, optimality comparison through cost matching, and efficiency comparison through nodes expanded and execution time.

### 3. Application Of Theoretical Concepts

Evidence for this criterion appears in the `Task 2` and `Task 4` sections of the notebook.

The notebook applies two heuristics:

- `baseline_heuristic`: Manhattan distance
- `enhanced_heuristic`: Manhattan distance plus additional penalties related to constraint-heavy locations and delivery-hour considerations

This supports the rubric requirement to justify and compare heuristic design. The implementation also includes constraint-aware successor generation through `is_path_feasible()`, which links the search behaviour to the problem environment rather than treating the graph as an unconstrained map.

The heuristic comparison results are saved to:

- `heuristic_results.csv`
- `heuristic_comparison.png`

### 4. Reasoning, Presentation, And Communication

Evidence for this criterion appears across the full notebook and the saved outputs.

The notebook is divided into task-labelled sections that mirror the assignment structure:

- `Task 1: Environment Modelling and Problem Formulation`
- `Task 2: Search Algorithm Implementation`
- `Task 3 and Task 4: Evaluation, Logical Validation, and Output Generation`

The submission also includes figures and CSV files to support analysis rather than relying only on printed console output. This helps present the work clearly and makes it easier for the assessor to trace how the implementation supports the discussion in the report.

## Software Requirements

To run the notebook successfully, the following Python libraries are required:

- `heapq`
- `time`
- `pandas`
- `matplotlib`
- `numpy`
- `collections`
- `typing`

Standard library modules are included with Python. External libraries that need to be available are:

- `pandas`
- `matplotlib`
- `numpy`

## How To Run The Notebook

1. Open `s224529554.ipynb` in Jupyter Notebook, JupyterLab, or VS Code.
2. Ensure that `pandas`, `matplotlib`, and `numpy` are installed in the Python environment.
3. Run all cells from top to bottom.
4. The notebook will:
   - build the campus graph
   - visualise the map
   - run `A*` and `UCS` on the three evaluation cases
   - compare the baseline and enhanced heuristics
   - save result tables and figures into the current folder

## Expected Outputs After Running

When the notebook is executed successfully, it will generate or overwrite the following files:

- `campus_map.png`
- `algorithm_results.csv`
- `algorithm_comparison.png`
- `heuristic_results.csv`
- `heuristic_comparison.png`

## Summary Of Current Results

Based on the saved CSV outputs:

- `A*` and `UCS` return the same path cost for all three evaluated test cases.
- `A*` expands fewer nodes than `UCS` in all three cases:
  - `Gate2 -> DeliveryHub`: `8` vs `39`
  - `BuildingJ -> BuildingHD`: `12` vs `23`
  - `Library -> Gate1`: `17` vs `58`
- The enhanced heuristic is mixed in performance:
  - worse on `Gate2 -> DeliveryHub`
  - slightly better on `BuildingJ -> BuildingHD`
  - equal on `Library -> Gate1`

This means the enhanced heuristic is evaluated transparently rather than assumed to be better in every case. That makes the results section more evidence-based and supports a stronger rubric-aligned discussion in the report.

## Notes For The Assessor

- The notebook is the main executable submission file.
- The CSV and PNG outputs are included to support the analysis and comparison sections of the report.
- This README is intended to make the structure of the submission and its alignment to the rubric easier to follow.
