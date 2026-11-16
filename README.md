# Intel and the $25 Billion Analytics Program: A Case Presentation

Class presentation and report for **IE 590: Supply Chain Engineering and Analytics**, Purdue University, reviewing **Heiney et al. (2021), "Intel Realizes $25 Billion by Applying Advanced Analytics from Product Architecture Design Through Supply Chain Planning"**, INFORMS Journal on Applied Analytics, Vol. 51, No. 1, pp. 9 to 25. The presentation was given by a team of three. The written report and the critique below are my own. Presentation team: Ajith Anandh, Gautham Vepa and Adharsh Rajasekar.

This is a paper review. The methods and the financial results belong to Intel and the paper's authors. The contribution here is the summary, the critique and the lessons for analytics practitioners.

## The problem

Intel designs and manufactures its own chips. Products grew from a single core to multi-die designs with 50 or more cores, while manufacturing variability produces a spread of speeds, core counts and power levels from the same wafers. The supply chain spans roughly 400 wafer types, 4,600 SKUs, 600 million units a year and more than 200 internal and outsourced factories in 13 countries. The legacy planning tools could no longer produce feasible plans in time.

## The approach

**Product architecture design (about two years ahead)**
- **Composition:** a device physics simulation of manufacturing variability feeds a mixed-integer program that picks the set of architecture configurations with the lowest total cost. One SKU-set redesign saved about $750 million in manufacturing cost.
- **Performance:** a genetic algorithm searches SKU-sets, with a linear program per candidate estimating manufacturing cost. On one product it found a SKU-set worth about $235 million in extra revenue.

**Supply chain planning (monthly, about a year ahead)**

| Step | What it decides | Scale |
|---|---|---|
| 1. Wafer starts optimization | Fab and sort capacity allocation for all products | 13M variables, solved in about 6 minutes |
| 2. Network capacity alignment | Capacity by product family across die-prep, assembly and test | 7.9M variables, about 4 minutes |
| 3. Optimized routing plans | The enterprise plan of record, solved per product family | Under 2 minutes per family |

Techniques include problem decomposition, sequential goal programming, path-based formulations, constraint caching, and explainability modules (rules and machine learning) that help planners understand the optimizer's output.

## Reported results (2009 to 2019)

All figures are as reported in the paper, with the financial benefits computed by Intel Finance.

- **$25.4 billion** in total financial benefit, based on $568 billion of Intel revenue: about $1.9 billion per year in added revenue and $1.5 billion per year in cost reduction.
- **Product architecture design:** $1.38 billion over four years ($1.04 billion in cost savings and $340 million in revenue).
- **Supply chain planning:** the legacy greedy heuristics needed 6% to 15% more wafer starts for the same demand. Intel's conservative valuation uses 6%, counted as a 6% cost saving in years without capacity constraints, a 6% revenue upside in capacity-constrained years, and a 3% and 3% split in mixed years.
- **Water:** about 2 billion gallons of water saved and over 500 million gallons of wastewater prevented over the ten years, as a by-product of fewer wafer starts.
- **Planning speed:** problems solved in minutes or hours instead of days or weeks, with 5 to 10 times more scenarios evaluated per cycle.

## Critique and suggestions

- **Counterfactual:** the $25.4 billion rests on a comparison with legacy heuristics, and the paper says little about how that baseline held up over ten years of growing product complexity. If it deteriorated, the measured gap may overstate the benefit.
- **Demand forecasts:** composition and performance are sensitive to forecast accuracy, which the paper treats as an input. Two-stage or scenario-based stochastic programming could make the plans robust to forecast error.
- **Failure modes:** the paper is almost uniformly positive, with no account of overridden recommendations or product generations where the system underperformed.
- **Disruptions:** it does not show how the framework behaves under shocks such as the pandemic or export restrictions.
- **Further ideas:** a published benchmark against a commercial solver, a generalizability analysis for chiplet designs and new process nodes, and online or reinforcement-learning methods for continuous re-planning.

## Lessons for practitioners

1. Integration beats silos: linking product design with supply chain planning unlocked value neither could deliver alone.
2. Decompose to conquer: breaking the large MIPs into structured sub-problems made solves of a few minutes possible.
3. Simulation plus optimization: when the physics cannot be written in closed form, simulation-informed optimization is the way in.
4. Adopt from the bottom up: build a proof of concept with real data and share it with users before their managers.
5. Explain the black box: explainability modules helped planners trust the output.
6. Custom can beat off-the-shelf: no commercial software met Intel's scale and update cadence.
