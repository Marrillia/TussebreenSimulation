# Tussebreen Bed Topography Simulation
## Gator glaciology lab 2025: Antarctic bed topography MCMC simulation for the Tussebreen glacier located in the Sor Rondane region. 
 <img width="200" height="200" alt="30" src="https://github.com/user-attachments/assets/0f77dfcb-015d-4556-95ed-c05cbe17ae87" />

### Authors: Lillian Barrett, Emma MacKie, Niya Shao


## Overview:
The bed topography under the Antarctic ice sheet is largely unknown. By creating geologically realistic rough simulations of the bed topography, ice sheet modelers can give more accurate predictions about sea level rise. To generate this realistic  topography we want it to be as physically real as possible, so we focus not only on roughness but also on minimizing the mass flux residual. This is done by taking the sequential gaussian simulation and running it through a bi-step monte carlo markov chain. Using a large block chain to regenerate large chunks of the topography at a time under the constraint to minimize the mass flux residual. Once this step reaches a mass flux residual similar to Bedmachine, it is then turned over to small chain regenerations further minimizing the mass flux residual. 

## Figures:

<img width="509" height="252" alt="0" src="https://github.com/user-attachments/assets/b0a984a0-24b1-4311-be58-089d1ea36802" />

The ice velocity magnitude of Tussebreen with vector field overlay. The grounding line can be seen (black).

<img width="432" height="451" alt="0 (1)" src="https://github.com/user-attachments/assets/2e2e6d9f-3280-498b-929b-ba041736cff4" />

The Bedmachine simulated bed elevation of Tussebreen. The grounding line can be seen (black).

The MCMC simulated bed elevation of Tussebreen. The grounding line can be seen (black).

The MCMC mass flux residual (left) and the Bedmachine mass flux residual (right). The grounding line can be seen (black).

## Environment:
A conda environment was used in conjunction with the `gstatsMCMC.yml` file. 

### To make the new enviroment:
`conda env create -f gstatsMCMC.yml`
### To activate:
`conda activate gstatsMCMC`


## Usage:
1. Make the environment.
2. Crop the region. For Tussebreen, xmin = 536250 xmax = 897750 and ymin = 1717250 ymax = 2151250 in polar stereographic coordinates.
3. Run the `T1_LoadData.ipynb` notebook, make sure you use the cropped region here.
4. Run `T2_StatisticalAnalysis.ipynb` notebook. This step gives a lot of important data including; normalized bed elevation data, the semivariogram, and the initial Sequential Gaussian Simulated bed topography.
5. Run `T3_LargeScaleChain.ipynb` notebook. This step is the start of Markov Chain Monte Carlo, as it breaks the region up into large blocked chunks resimulating the chunk with the constraint of minimizing the massflux residual. Each iteration is then accepted or not. For Tussebreen this step was repeated, so far, 3.5 million times.
6. Run `T4_SmallScaleChain.ipynb` notebook. This works the same as `T3_LargeScaleChain.ipynb` but on a smaller scale. The goal here is to end with a mass flux residual as close to zero as possible, aiming for at least less than Bedmachine.

## Refrences:
Shao, N., MacKie, E., Field, M., & McCormack, F. (2025). A Markov chain Monte Carlo approach for geostatistically simulating mass-conserving subglacial topography. EarthArXiv. https://doi.org/10.31223/X5SB2R

Morlighem, M. (2022). MEaSUREs BedMachine Antarctica. (NSIDC-0756, Version 3). [Data Set]. Boulder, Colorado USA. NASA National Snow and Ice Data Center Distributed Active Archive Center. https://doi.org/10.5067/FPSU0V1MWUB6

Pritchard, H.D., Fretwell, P.T., Fremand, A.C. et al. Bedmap3 updated ice bed, surface and thickness gridded datasets for Antarctica. Sci Data 12, 414 (2025). https://doi.org/10.1038/s41597-025-04672-y

