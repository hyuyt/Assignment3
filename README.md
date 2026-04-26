# Sorting Algorithm Performance Analysis
# Nurkhayat Talgatkyzy IT-2503


## Overview

This project compares the performance of two sorting algorithms — **Insertion Sort** (basic) and **Merge Sort** (advanced) — across varying array sizes, alongside a binary/linear search time measurement. The goal is to empirically validate theoretical time complexity differences between O(n²) and O(n log n) sorting approaches.

---

## Algorithms

### Basic Sort — Insertion Sort
- **Time Complexity:** O(n²) average and worst case
- **Space Complexity:** O(1) auxiliary
- **Strategy:** Iterates through the array, inserting each element into its correct position among the already-sorted elements to its left.
- **Best for:** Small arrays or nearly sorted data.

### Advanced Sort — Merge Sort
- **Time Complexity:** O(n log n) average and worst case
- **Space Complexity:** O(n) auxiliary
- **Strategy:** Recursively divides the array in half, sorts each half, and merges the results.
- **Best for:** Large datasets where consistent performance is required.

---

## Experiment Results

The following table summarizes the measured operation counts (time complexity units) for each algorithm across four input sizes:

| Array Size | Basic Sort (Insertion) | Advanced Sort (Merge) | Search Time |
|------------|------------------------|------------------------|-------------|
| 10         | 2,916                  | 10,208                 | 1,667       |
| 100        | 33,667                 | 50,167                 | 917         |
| 1,000      | 1,481,417              | 529,750                | 750         |
| 10,000     | 14,988,875             | 475,917                | 2,375       |

---

## Analysis

### Small Arrays (n = 10, 100)
At small input sizes, **Insertion Sort outperforms Merge Sort**. This is consistent with theory: Merge Sort carries fixed overhead from recursion and merging steps, which dominates when n is small. Insertion Sort's simplicity gives it an edge here.

### Large Arrays (n = 1,000, 10,000)
As the array size grows, **Merge Sort significantly outperforms Insertion Sort**. The gap widens dramatically:
- At n = 1,000: Merge Sort is ~**2.8× faster** than Insertion Sort.
- At n = 10,000: Merge Sort is ~**31.5× faster** than Insertion Sort.

This confirms the O(n²) vs O(n log n) theoretical complexity gap in practice.

### Search Time
Search time does not follow a strict monotonic trend across sizes, likely due to factors such as cache behavior or the specific search target position within the array. Overall, search times remain consistently low relative to sort times.

---

## Key Takeaways

- **Insertion Sort is preferable for small datasets** due to low overhead and cache-friendly access patterns.
- **Merge Sort is superior for large datasets**, with its O(n log n) complexity yielding dramatic performance gains as n increases.
- The crossover point in this experiment occurs somewhere between n = 100 and n = 1,000, where Merge Sort begins to outperform Insertion Sort.
