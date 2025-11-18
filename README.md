# Tussebreen Bed Topography Simulation
Gator glaciology lab 2025: Antarctic bed topography MCMC simulation for the Tussebreen glacier located in the Sor Rondane region.

Overview:
The bed topography under the Antarctic ice sheet is largely unknown. By creating geologically realistic rough simulations of the bed topography, ice sheet modelers can give more accurate predictions about sea level rise. To generate this realistic  topography we want it to be as physically real as possible, so we focus not only on roughness but also on minimizing the mass flux residual. This is done by taking the sequential gaussian simulation and running it through a bi-step monte carlo markov chain. Using a large block chain to regenerate large chunks of the topography at a time under the constraint to minimize the mass flux residual. Once this step reaches a mass flux residual similar to Bedmachine, it is then turned over to small chain regenerations further minimizing the mass flux residual. 


<img width="518" height="691" alt="Antartica (2)" src="https://github.com/user-attachments/assets/5f41386d-b8ca-462a-b637-3304430954c9" />

Fgure 1: (a) Grounding line outline of Antarctica with pink outline of the study region (Tussebreen) and labels of the most prominent glaciers on either side Jutulstraumen (left) and Belgica (right). Zoomed in the Tussebreen region displaying the mask and radar data coverage in polar stereographic coordinates. 

Environment:
This was done in the conda environment gstatsMCMC

Usage:
TBD

Data:
(Will add actual data but place holders)
Bedmachine
BedMap3
Antarctica grounding line
