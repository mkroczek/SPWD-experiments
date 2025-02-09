# SPWD algorithm usability for the CQM hybrid solver

This experiment is meant to verify whether SPWD application improves the results of workflow scheduling on the hybrid solver. Workflows are solved on a hybrid CQM
sampler, provided by the D-Wave company. CQM struggles with big workflow instances, which is further described [here](./cqm_limits/cqm_limits.png).

### Methodology

For this experiment we used 4 Montage workflows, that couldn't be solved on the CQM:

|   workflow   | task count | path count | max subgraph size |
|:------------:|:----------:|:----------:|:-----------------:|
| Montage_310  |    310     |   25536    |        100        |
| Montage_472  |    472     |   46272    |        150        |
| Montage_619  |    619     |   101880   |        200        |
| Montage_1066 |    1066    |   180300   |        350        |

For each instance we selected arbitrary max subgraph size value and performed scheduling three times:

* Scheduling on the raw Gurobi (without SPWD application)
* Scheduling with SPWD on the Gurobi
* Scheduling SPWD in the CQM

### Results

Scheduling results have been collected in [this folder](./montage_schedules).

|   workflow   | $\frac{\text{CQM + SPWD}}{\text{Gurobi + SPWD}} [\%]$ | $\frac{\text{CQM + SPWD}}{\text{Gurobi (raw)}} [\%]$ |
|:------------:|:-----------------------------------------------------:|:----------------------------------------------------:|
| Montage_310  |                          0.0                          |                         8.0                          |
| Montage_472  |                          0.0                          |                         1.4                          |
| Montage_619  |                          0.7                          |                         15.8                         |
| Montage_1066 |                          0.1                          |                         1.2                          |

SPWD allowed to successfully schedule all workflow instances, that were
problematic to the CQM solver. Scheduling cost of divided parts was very similar to the
benchmark Gurobi solver (difference did not exceed 1%). Cost overhead caused by SPWD was also acceptable and the highest
noted increase was 15.8% for the
Montage_619.