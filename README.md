IGABH: Improved Hybrid Genetic BlackHole
Algorithm

Publication-Grade README

1. Scope of Repository
This repository contains the MATLAB implementation of the Improved Hybrid Genetic BlackHole (IGABH) algorithm together with competing metaheuristics and ablation-study scripts used in the manuscript. The repository is intended to enable complete reproduction of benchmark functions,
engineering problems, and ablation-study results.

2.Repository Structure
The main folder IGABH contains all the necessary MATLAB scripts required to reproduce the
results presented in the manuscript. The main folder IGABH contains a sub-folder known as “Ablation Study” and the IGABH and competing algorithms MATLAB scripts. Detailed information about the MATLAB scripts found in the main folder IGABH are given below :

(a)Optimization Algorithms
• IGABH_Algorithm.m – Proposed Improved Hybrid Genetic BlackHole Algorithm (IGABH)
• GABH_Algorithm.m – Hybrid Genetic BlackHole Algorithm (GABH)
• Genetic_Algorithm.m – Standard Genetic Algorithm (GA)
• PSO_Algorithm.m – Particle Swarm Optimization (PSO)
• Mayfly_Algorithm.m – Mayfly Algorithm (MA)
• Blackhole_Algorithm.m – Black Hole Algorithm (BH)

(b)Dependencies & Set Up
MATLAB Scripts of Optimization Algorithms	Required Files
Genetic_Algorithm.m	          UniformCrossover.m, Mutate.m, SortPopulation.m, 
RouletteWheelSelection.m
PSO_Algorithm.m	-
Mayfly_Algorithm.m	           Crossover3.m, Mutate3.m
Blackhole_Algorithm.m	        EnforceBounds.m
GABH_Algorithm.m	             UniformCrossover.m, Mutation.m, EnforceBounds.m
IGABH_Algorithm.m	            UniformCrossover.m, Mutation.m, EnforceBounds.m, Crossover.m, 
Adaptivealpha


(c)Detailed Folder Structure
IGABH/
│
├── IGABH_Algorithm.m
├── GABH_Algorithm.m
├── Genetic_Algorithm.m
├── PSO_Algorithm.m
├── Mayfly_Algorithm.m
├── Blackhole_Algorithm.m
├── UniformCrossover.m
├── Adaptivealpha.fis
├── Mutation.m
├── fun_info.m
├── fun_eng.m
├── EnforceBounds.m
├── Crossover.m
├── Mutate.m
├── Crossover3.m
├── Mutate3.m
├── SortPopulation.m
├── RouletteWheelSelection.m
│
├── Ablation Test/
│ ├── Full_IGABH
│ ├── IGABH_Without_FIS.m
│ ├── IGABH_Without_SawTooth_scheme.m
│ ├── IGABH_Without_Enhanced_Mayfly.m
│ ├── IGABH_Without_Probability_Star_Generation.m
│ ├── IGABH_With_Fixed_Alpha_value.m
│ └── IGABH_With_Single_Star_Movement.m
│  
│
└── README.md

3.System Requirements
The IGABH algorithm, competing algorithms (GA,PSO,MA,BH, and GABH), and variants of the IGABH algorithm used for the ablation test were developed and tested using the following environment:
Item	                  Specification
MATLAB Version	          MATLAB R2021b
Required Toolbox	  Fuzzy Logic Toolbox
Operating System	  Windows 10/11
Processor	          Intel Core i5, 2.30 GHz
RAM	                  8 GB

■ The Fuzzy Logic Toolbox is required to load and execute Adaptivealpha.fis. 

(a)Known MATLAB Version Compatibility
The following MATLAB versions given below are known to be compatible with the optimization algorithm MATLAB scripts and can run them smoothly without any errors:
MATLAB Version	               Status
R2015a	                     Fully Tested
R2021b                       Fully Tested
R2016a - R2019b  	     Expected Compatible
R2020a - R2026a	             Expected Compatible but not formally tested


■ NOTE (Very Important!!!): 
(i). Users may need to update “readfis(...)” syntax in IGABH_Algorithm.m and other variants of  IGABH that uses FIS in the ablation test if MathWorks changes FIS (fuzzy inference system) handling in future releases.
(ii). The file path fis = readfis('C:\Users\user\Desktop\IGABH\Adaptivealpha.fis')  in IGABH_Algorithm.m and other variants of  IGABH that uses FIS in the ablation test also needs to be updated. For example, if the IGABH repository is stored in the Downloads folder :

fis = readfis('C:\Users\user\Downloads\IGABH\Adaptivealpha.fis')or if  the IGABH repository is stored on Desktop on a different computer under another user account (e.g., Lydia), fis = readfis('C:\Users\Lydia\Desktop\IGABH\Adaptivealpha.fis').


4.Experimental Protocol
All experiments were conducted under the identical conditions given below to ensure fair comparison among all algorithms:
Parameter	                           Value
Population Size	                            50
Maximum Iterations	                   2,000
Independent Runs	                    30
Stopping Criterion	                   Max iterations reached
Number of CEC benchmark functions tested   23 unconstrained functions
Number of engineering problems tested	   2 Constrained problems

Benchmark definitions are provided in:
■ fun_info.m (CEC benchmark functions)
■ fun_eng.m (engineering problems)

NOTE: It is important to note that the MATLAB script fun_eng.m contain the function definitions of 10 engineering problems but only 2 were selected to test the IGABH and the competing algorithms for experiments reported in the manuscript. The selected engineering problems were F1 (Tension/Compression Spring) and F9 (Welded Beam).

■ All algorithms (IGABH, GA, PSO, MA, BH, GABH) use the identical settings provided in the table above for all experiments conducted.

■ However, the algorithm-specific parameter settings for GA, PSO, MA, BH,GABH  and IGABH correspond exactly to those reported in the manuscript.


(a)Random Number Generation & Independent Runs
■ All results are obtained from 30 independent runs.

■ For each independent run, a new population of candidate solutions is generated using MATLAB's pseudo-random number generator through the rand() function. Since each run is initialized independently, different initial populations are produced across runs, thereby enabling statistical evaluation of algorithm performance over multiple trials.

■ The original experiments were conducted using MATLAB's default pseudo-random number generation mechanism without enforcing fixed random seed values. Consequently, exact run-by-run numerical replication may vary slightly due to the stochastic nature of the algorithms. However, all reported performance metrics (Best, Mean, and Standard Deviation) were computed from 30 independent runs, which is standard practice for evaluating stochastic metaheuristic optimization algorithms.

(b)How to test an Optimization Algorithm on the CEC Benchmark functions
To reproduce the CEC Benchmark function results reported in the manuscript, the user has to follow the following steps:


Step 1:

■ Set MATLAB current folder to IGABH/.

Step 2:

■ Open the MATLAB script of the optimization algorithm you want to test on the CEC benchmark functions. 

■ The MATLAB scripts of the optimization algorithms available in the IGABH directory are IGABH_Algorithm.m,Genetic_Algorithm.m,PSO_Algorithm.m,Mayfly_Algorithm.m, Blackhole_Algorithm.m, and GABH_Algorithm.m 

Step 3:

■ Activate these lines of code in the selected optimization algorithm MATLAB script to call the fun_info.m  file :


[lb,ub,D,out] = fun_info(Fun_name);

lowerbound = lb;
upperbound = ub;
dimension = D;
fitness = out;

Step 4:

Comment out or deactivate the lines of code below in the selected optimization algorithm MATLAB script:

[lb,ub,D,out] = fun_eng(Fun_name);

lowerbound = lb;
upperbound = ub;
dimension = D;
fitness = out;

Step 5:

■ Select the benchmark function (F1, F2,…,F23) you want to run using the for loop code below in the selected optimization algorithm MATLAB script:

for uu = 1:23

■ The table below explains how to select the benchmark function you want to run using the for loop setting:
Benchmark Function	      Setting
F1	                    for uu = 1:1
F6	                    for uu = 6:6
F23	                    for uu = 23:23
F1 - F12	            for uu = 1:12
All	                    for uu = 1:23


Step 6:

■ If CBPE_min is available in the selected optimization algorithm MATLAB script, set it to the theoretical global optimum value of the selected benchmark function(s).

Step 7:

■ Run the selected optimization algorithm MATLAB script.


(c)How to test an Optimization Algorithm on the Engineering Benchmark Problems
To reproduce the engineering benchmark problems results reported in the manuscript, the user has to follow the same steps outlined in reproducing the CEC Benchmark function results stated in “(b) How to test an Optimization Algorithm on the CEC Benchmark functions”.

 However, the steps 3, 4 & 5 in this case will change. The new steps 3, 4 & 5 for reproducing the engineering benchmark problems results are:


Step 3:

■ Activate these lines of code in the selected optimization algorithm MATLAB script to call the fun_eng.m  file :


[lb,ub,D,out] = fun_eng(Fun_name);

lowerbound = lb;
upperbound = ub;
dimension = D;
fitness = out;

Step 4:

■ Comment out or deactivate the lines of code below in the selected optimization algorithm MATLAB script:

[lb,ub,D,out] = fun_info(Fun_name);

lowerbound = lb;
upperbound = ub;
dimension = D;
fitness = out;

Step 5:

■ Select the engineering benchmark problem (F1, F2,…,F10) you want to run using the for loop code below in the selected optimization algorithm MATLAB script:

for uu = 1:10

■ NOTE: It is important to note that the MATLAB script fun_eng.m contain the function definitions of 10 engineering problems but only 2 were selected to test the IGABH and the competing algorithms for the experiments reported in the manuscript. The selected engineering problems were F1 (Tension/Compression Spring) and F9 (Welded Beam).


(d)Reproducing the Ablation Study
The folder IGABH/Ablation Test/contains all IGABH variants evaluated in the manuscript.
The variants include: Full IGABH, IGABH without FIS, IGABH without Saw-Tooth mechanism, IGABH without enhanced Mayfly crossover, IGABH without probability-based star generation, and other variants used in the study.

To reproduce the ablation test results reported in the manuscript, the user has to follow the following steps:

Step 1:

■ Set MATLAB current folder to IGABH/Ablation Test

Step 2:

■ Open the MATLAB script of the IGABH variant you want to test on the CEC benchmark function(s). 
Step 3:

■ Select the benchmark function (F1, F2,…,F23) you want to run using the for loop code below in the selected IGABH variant MATLAB script:

for uu = 1:23

■ The table below explains how to select the benchmark function you want to run using the for loop setting:
Benchmark Function             Setting
F1	                    for uu = 1:1
F9	                    for uu = 9:9
F23	                    for uu = 23:23
F1 - F12	            for uu = 1:12
All	                    for uu = 1:23


Step 4:

■ If CBPE_min is available in the selected IGABH variant MATLAB script, set it to the theoretical global optimum value of the selected benchmark function(s).

Step 5:

■ Run the selected IGABH variant MATLAB script.

NOTE: 

i.All IGABH variants must be run under identical benchmark settings.
ii.To ensure fair comparison among all IGABH variants, all ablation experiments were conducted with the following parameters:

Parameter	                               Value
Population Size	                                 50
Maximum Iterations	                        2,000
Independent Runs	                         30
Stopping Criterion	                      Max iterations reached
Number of CEC benchmark functions tested      6 unconstrained functions (F1, F2, F10, F11, F19, F20)
Crossover Probability (Pc)	                 1.0
Mutation Rate (μ)	                         0.02


5.Software Lincense
This repository is released under the MIT License.

6.Citation
If you use this repository, please cite:

Stephen Asare Bediako, Elvis Twumasi, and Emmanuel Assuming Frimpong.
Solving Optimization Problems using Hybrid Metaheuristics: Hybrid Genetic Algorithm with Modified Black Hole Algorithm as Local Search.
Wiley Journal of Electrical and Computer Engineering, 2026.




















