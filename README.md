# Project: Grouping Possum Data Using Machine Learning

This project helps you find natural groups in a dataset of wild possums. It cleans the data, finds hidden patterns, and groups the animals by their physical measurements.

---

## 1. Project Goals
* **Clean the Data**: Fix missing values and scale numbers so the math works properly.
* **Group the Animals**: Use two different methods to put similar possums into groups.
* **Simplify the Views**: Turn complex data into a simple 2D map graph.
* **Plan for Real Use**: Design a simple way to use this system in the real world.

---

## 2. Summary of Results

| Evaluation Score | 2 Groups | 3 Groups (Best Choice) | 4 Groups |
| :--- | :--- | :--- | :--- |
| **Group Tightness (Inertia)** | 642.18 | **511.45** *(Clear drop)* | 445.80 |
| **K-Means Separation Score** | 0.2841 | **0.3105** *(Highest peak)* | 0.2450 |
| **Hierarchical Separation Score** | 0.2412 | **0.2984** | 0.2210 |

### What the Groups Mean
* **Group 0 (Small Possums)**: Young, small body lengths, small heads.
* **Group 1 (Long-Tailed Possums)**: Medium body weights but very long tails.
* **Group 2 (Large Possums)**: Heavy, largest total body frames, wide heads.

---

## 3. Real-World Use Plan

### Setup Plan
The model will live on a fast web cloud server. When a user types physical measurements into an app, the server processes the data instantly and responds with the group number (Group 0, 1, or 2).

### Challenges and Solutions
* **Speed**: Searching group categories can get slow. **Fix**: Store the center points of the groups in a quick memory cache system (Redis) to get answers instantly.
* **System Load**: Too many users at the same time can crash the server. **Fix**: Use an auto-scaling cloud system that automatically adds server power when it gets busy.
* **Data Changes**: Animals change size across different seasons, making old models wrong. **Fix**: Run a monthly automated check on new data. If the animal shapes look different from our original data, a script will automatically re-run the training code and refresh the live system.
