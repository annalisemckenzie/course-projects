# Project Proposal for ME 599 - Annalise Miller - April 8, 2018

## Motivation
As a graduating master's student, I have already developed the functionality of codes related to the specific case studies that I will include in my thesis. While most individual codes perform wind farm layout optimization or hard-coded analysis, they each do so using different commands, data structures, optimization algorithms, and input cost and wake models. While the various codes contain useful functions for future research, such as the optimization algorithms and input models, a future researcher would have to devote weeks to understanding the organization and operation of a code before they could restructure it for new analyses. The goal of this project is to develop a program combining and modularizing my existing code for accessibilty and use in future research by other researchers.

## Required Work
This project would involve reorganizing the codes I have developed individually, standardizing input requirements and output parameters, and allowing users to specify input data and select relevant input models. While several of my codes use similar input models, the requirements of the optimization algorithms involved lent themselves to different data structures and thus different representations of, and interactions between, the same input models. To provide a streamlined, modularized code, I will need to create a single function for each input model that is capable of interacting with all other input models and optimization algorithms. This step requires revision of the bulk of my research over the past two years. I will then need to create a wrapper that allows users to select input models and optimization algorithms (or hard-code analysis), gathers the necessary functions, performs the required analysis, and creates an output file with pertient model output and metadata.

## Program User Inputs
The proposed program would allow researchers to choose between analyzing an input layout or optimizing a layout given input wind conditions. Each analysis would require the user to input the farm dimensions (assumed to be rectangular), surface roughness, power coefficient, wind conditions and associated probabilities, turbine power curve, atmospheric stability conditions, air density, turbine geometry, the number of turbines, axial induction factor, and wind speed reference height. Each of these inputs would also have an appropriate default value. Users would then be given the option of onshore or offshore farm optimization, which would be used to select the appropriate farm cost model. The user would then select the desired objective evaluation, wake model, and cost model. With each of these selections the necessary additional user inputs would be requested as given in the "user input" column of the table at the end of this document. 

## Program Outputs
The program would return simulation data and metadata in CSV format. This file would include the objective evaluation, simulation time, number of function evaluations performed, energy produced, farm cost, wind speeds at each turbine for each wind case, turbine coordinates, and a summary of the input parameters selected before evaluation. 

| **User Selected** | **User Input** |
| ----------------- | -------------- |
| **Optimization Algorithm** |  |
|    Genetic Algorithm | Mesh size, mutation rate, percent elite, percent mateable, population size, no-change iterations to convergence |
|    Paritcle Swarm Optimization | swarm size, self weight, global weight, no-change iterations to convergence |
|    Extended Pattern Search | initial step size, min step size, popping attepts, num turbines popped, max popping attempts per turbine |
| **Cost Model** |   |
|    Onshore Cost Model [1] | None |
|    Offshore Cost Model [2] | water depth |
| **Wake Model** |   |
|    3D PARK wake model with or without nested wake provision | None |
|    2D PARK wake model with or without nested wake provision | None |
|    2D RANS-based CFD wake model | None |
| **Objective Function** |   |
|    Annual Energy Production | optimization algorithm, wake model |
|    Cost-per-kilowatt | optimization algorithm, farm life, cost model, wake model |
|    Profit | optimization algorithm, farm life, cost model, wake model |
|    LCOE  | optimization algorithm, farm life, cost model, wake model |
|    Cost  | optimization algorithm, cost model |

## References
[1]  B.  L.  DuPont,  J.  Cagan,  and  P.  Moriarty,  “Optimization  of  Wind  Farm  Layout  and  Wind  TurbineGeometry Using a Multi-Level Extended Pattern Search Algorithm That Accounts for Variation in WindShear Profile Shape,”38th Design Automation Conference, vol. 3, Parts A and B, p. 243, 2012. [Online].Available:  http://www.scopus.com/inward/record.url?eid=2-s2.0-84884605472&partnerID=tZOtx3y1

[2]  B. D. Annalise Miller, Caitlin Forinash, “An extended pattern search approach for optimizing floatingoffshore wind farms,”In Review, 2018.
