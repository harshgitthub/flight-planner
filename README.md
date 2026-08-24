# Flight Planner COL106

A Python implementation of a flight-planning system that searches for valid routes between cities based on different optimization criteria.

## Overview

This project models flights as directed connections between cities and provides a `Planner` that can answer three types of route queries:

- Least number of flights with earliest arrival among equally short routes
- Cheapest total fare route
- Least flights, breaking ties by cheapest total fare

It is built around a graph-like structure with custom heap and queue utilities for route planning.

## Project Structure

- `flight.py` – defines the `Flight` data model
- `planner.py` – contains the route-planning logic, graph representation, and helper data structures
- `main.py` – sample usage and demonstration of the planner on a small flight network

## Flight Model

Each flight is represented by a `Flight` object with:

- `flight_no`
- `start_city`
- `departure_time`
- `end_city`
- `arrival_time`
- `fare`

The planner assumes:

- Cities are labeled with integers
- Time is represented as a non-negative integer
- Flights are directed from one city to another
- A route must respect minimum layover time and time-window constraints

## Planner Functions

The `Planner` class exposes the following methods:

### 1. `least_flights_earliest_route(start_city, end_city, t1, t2)`

Returns the route from `start_city` to `end_city` that:

- departs at or after `t1`
- arrives at or before `t2`
- uses the fewest flights
- if multiple routes have the same number of flights, chooses the earliest arrival

### 2. `cheapest_route(start_city, end_city, t1, t2)`

Returns the cheapest valid route satisfying the time constraints.

### 3. `least_flights_cheapest_route(start_city, end_city, t1, t2)`

Returns the route with:

- the minimum number of flights
- and, among equal-length routes, the lowest total fare

## Example Run

The project includes a ready-to-run example in `main.py`:

```python
from flight import Flight
from planner import Planner
```

The script builds a sample network of cities and flights, then checks the three planner tasks:

```python
route1 = flight_planner.least_flights_earliest_route(0, 4, 0, 300)
route2 = flight_planner.cheapest_route(0, 4, 0, 300)
route3 = flight_planner.least_flights_cheapest_route(0, 4, 0, 300)
```

The expected validation prints:

```text
Task 1 PASSED
Task 2 PASSED
Task 3 PASSED
```

## Running the Project

From the project directory, run:

```bash
python main.py
```

On Windows, the common equivalent is:

```bash
py main.py
```

## Notes

- This is a graph-based flight routing assignment.
- The code demonstrates route optimization using custom priority structures.
- You can modify the sample flights in `main.py` to test different scenarios.
