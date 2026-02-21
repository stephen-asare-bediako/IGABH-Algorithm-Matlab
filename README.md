IGABH: Improved Genetic Algorithm–Black Hole
--------------------------------------------------------------------------------------------------
Hybrid

This repository contains the MATLAB implementation of the Improved Genetic Algorithm–Black
Hole (IGABH) algorithm, together with competing metaheuristics and ablation study scripts used for
performance benchmarking.
-------------------------------------------------------------------------------------------------- 
■ Repository Structure
The main folder IGABH contains all the necessary MATLAB scripts required to reproduce the
results presented in the manuscript.
Optimization Algorithms
• IGABH_Algorithm.m – Proposed hybrid IGABH algorithm
• GABH_Algorithm.m – Genetic Algorithm–Black Hole hybrid
• Genetic_Algorithm.m – Standard Genetic Algorithm (GA)
• PSO_Algorithm.m – Particle Swarm Optimization (PSO)
• Mayfly_Algorithm.m – Mayfly Algorithm (MA)
• Blackhole_Algorithm.m – Black Hole Algorithm (BH)
■■ Dependencies & Setup
Algorithm Required Files
IGABH UniformCrossover.m, Mutation.m, EnforceBounds.m, Crossover.m, Adaptivealpha.fis
GA UniformCrossover.m, Mutate.m, SortPopulation.m, RouletteWheelSelection.m
MA Crossover3.m, Mutate3.m
BH EnforceBounds.m
GABH UniformCrossover.m, Mutation.m, EnforceBounds.m
■■ Important Configuration Notes
A. Update the FIS file path in:
fis = readfis('C:\Users\user\Desktop\IGABH\Adaptivealpha.fis');
B. Always set CBPE_min to the theoretical true global optimum of the selected benchmark function.
■ Running the Benchmarks
CEC Benchmark Functions → Requires fun_info.m
Engineering Optimization Problems → Requires fun_eng.m
--------------------------------------------------------------------------------------------------
MATLAB Version: Tested on MATLAB R2015a
Author: Stephen Asare Bediako
Institution: Kwame Nkrumah University of Science and Technology (KNUST), Ghana 
--------------------------------------------------------------------------------------------------
