# 🧬 Genetic Algorithm: Cargo Optimization

> An evolutionary approach to solving logistics optimization (a multi-constrained 0/1 Knapsack problem). Developed as a laboratory project for the "Intelligent Systems" university course.

---

## 🎯 Problem Statement
The algorithm selects the optimal combination of cargo items from 50 available options. Each item has a specific **value**, **weight**, and **volume**. The objective is to maximize the total value of the loaded cargo while strictly adhering to the physical constraints of the transport vehicle:
- Total Weight $\le$ `MAX_WEIGHT` (40% of the total weight of all available items)
- Total Volume $\le$ `MAX_VOLUME` (35% of the total volume of all available items)

---

## 🧠 Genetic Algorithm Mechanics
- **Chromosome Representation:** An individual is encoded as a binary array (where `1` means the item is selected, and `0` means it is left behind).
- **Fitness Function:** Calculates the total value of the selected items, applying severe mathematical penalties for exceeding the weight (x10 penalty multiplier) or volume (x12 penalty multiplier) limits.
- **Selection:** Tournament selection ($k=3$) to choose the most fit parents for breeding.
- **Crossover:** One-point crossover with a high probability rate (`CROSSOVER_RATE = 0.9`).
- **Mutation:** Random bit inversion with a low probability (`MUTATION_RATE = 0.02`) to maintain genetic diversity and escape local optima.
- **Elitism:** The top 2 individuals (`ELITISM = 2`) are guaranteed to pass directly to the next generation without mutation.

---

## 📊 Performance & Results
Leveraging vectorized operations via `numpy`, the algorithm demonstrates rapid convergence and high packing density. In typical test runs, the algorithm successfully maximizes the transport vehicle's capacity:
- Volume utilization reaches **100.0%**.
- Weight capacity utilization reaches **97.5%**.
- The best fitness score stabilizes efficiently by the 150th generation.