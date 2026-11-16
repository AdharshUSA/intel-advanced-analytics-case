# Intel and the $25 Billion Analytics Program: A Case Presentation

Class presentation reviewing **Heiney et al. (2021), "Intel Realizes $25 Billion by Applying Advanced Analytics from Product Architecture Design Through Supply Chain Planning"**, INFORMS Journal on Applied Analytics, Vol. 51, No. 1, pp. 9 to 25. Team of three.

This is a paper review. The methods and the financial results belong to Intel and the paper's authors. The contribution here is the summary and the lessons for analytics practitioners.

## The problem

Intel designs and manufactures its own chips. Products grew from a single core to multi-die designs with 50 or more cores, while manufacturing variability produces a spread of speeds, core counts and power levels from the same wafers. The supply chain spans roughly 400 wafer types, 4,600 SKUs and 200+ factories in 13 countries, and the legacy planning tools could no longer produce feasible plans in time.

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

- $25.4 billion in total financial benefit
- About $1.9 billion per year in added revenue and $1.5 billion per year in cost reduction
- 6% fewer wafer starts
- Roughly 2 billion gallons of water saved, as a by-product of fewer wafer starts
- 5 to 10 times more planning scenarios evaluated per cycle

## Lessons for practitioners

1. Integration beats silos: linking product design with supply chain planning unlocked value neither could deliver alone.
2. Decompose large optimization models so they run fast enough to be useful.
3. When the physics has no closed form, combine simulation with optimization.
4. Win users over bottom-up. Adoption mattered as much as the math.
5. Explain the black box, because planners trust what they can understand.
6. Off-the-shelf software could not meet this scale, so custom builds were sometimes the only path.

## Team

Adharsh Rajasekar, Ajith Anandh, Gautham Vepa
