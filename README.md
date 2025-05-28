# Assigning Regions to Sales Representatives at Pfizer Turkey

This case study presents a real-world application of multi-objective optimization to redesign the assignment of geographical regions (termed "bricks") to sales representatives at Pfizer Turkey. The goal is to reduce operational inefficiencies while preserving continuity and equity in workload distribution.

## Case Summary

Pfizer Turkey had not updated its sales territories in years, leading to inefficiencies in how regions ("bricks") were distributed among sales representatives. The company aimed to improve operational efficiency while limiting disruption to existing assignments.

Using mathematical programming, we modeled the problem as a binary integer program with multiple objectives:

- **Total travel distance:** Reduce the cumulative travel burden across all representatives.
- **Workload balance:** Ensure a fair distribution of bricks based on their demand index.
- **Disruption minimization:** Limit how much the new assignments differ from the current structure.

The optimization considered both fixed and flexible assignment models, including partial sharing of bricks and scenarios with increased demand or office relocations.

## Implementation

The optimization models were implemented in Python using the **Gurobi solver**. The code is available is [case_study_pfizer_solver.ipynb](case_study_pfizer_solver.ipynb).

The study used two standard techniques for multi-objective optimization:

- Weighted Sum Method
- $\varepsilon$-Constraint Method

We also integrated preference learning to reflect decision-maker priorities when choosing among Pareto-optimal solutions.

## Key Findings

| Strategy                      | Travel Distance | Disruption |
| ----------------------------- | --------------- | ---------- |
| Current Assignments           | 187.41          | 0.000      |
| Minimize Distance             | 154.60          | 1.200      |
| Minimize Disruption           | 188.95          | 0.169      |
| Relocate Offices (Distance)   | 103.56          | 3.537      |
| Relocate Offices (Disruption) | 291.87          | 0.169      |

Additional experiments showed that:

- Allowing **partial assignments** reduced both travel and disruption.
- Hiring an extra sales rep becomes necessary if **demand increases by over 20%**.
- The **office relocation** of new or existing reps can significantly affect performance.

## Takeaways

- Relocating offices can yield significant efficiency gains but may increase disruption.
- Demand forecasting should guide workforce expansion decisions.
- Human preferences should be considered when selecting optimal solutions among trade-offs.
