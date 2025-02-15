# Series-Parallel Workflow Decomposition Experimental Results

This repository contains results of various experiments conducted
for [Series-Parallel Workflow Decomposition](https://github.com/mkroczek/WorkflowDecomposition) (SPWD).
The main goal of SPWD was to divide big workflow instances, so that they could be successfully scheduled on the [CQM
hybrid quantum-classical sampler](https://docs.ocean.dwavesys.com/en/stable/docs_system/reference/generated/dwave.system.samplers.LeapHybridCQMSampler.sample_cqm.html),
which is unable to solve big Workflow Scheduling Problems due to capacity limitations.

### Experiments

Experiments described in this repository cover:

* [CQM capacity limitations](./experiments/cqm_scheduling/cqm_limits) - Experiment shows CQM capacity limits, which were
  observed in July 2024.
* [SPWD applicability for CQM](./experiments/cqm_scheduling) - The most important experiment, which proved that SPWD
  application allows to schedule big workflow instances on the CQM.
* [Max subgraph size influence on the cost increase](./experiments/mss_influence_results) - Shows how max subgraph size
  parameter (mss), which controls algorithm behaviour, affect the final schedule cost.
* [Correlation between max subgraph size and problem size](./experiments/problem_size_increase) - WSP in CQM notation
  consists of variables and constraints, which we call problem size. This experiment checks how mss is correlated with
  problem size of divided workflows.
* [Critical path value influence on the cost increase](./experiments/cpv_impact) - SPWD may cause an increase of the
  critical path value (CPV) in workflow. This experiment checks if such increase can increase final schedule cost.

### Solvers

WSPs from experiments were solved on the [CQM
hybrid quantum-classical sampler](https://docs.ocean.dwavesys.com/en/stable/docs_system/reference/generated/dwave.system.samplers.LeapHybridCQMSampler.sample_cqm.html)
provided by the [D-Wave](https://www.dwavesys.com/) and classical [Gurobi](https://www.gurobi.com/). Access to the CQM
and support was provided by Polish highperformance computing infrastructure PLGrid (HPC Center: ACK
Cyfronet AGH) within computational grant no. PLG/2024/017229. Gurobi was accessed
under [Academic License](https://www.gurobi.com/features/academic-named-user-license/).