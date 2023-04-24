# NEURON simulation files

This folder contains the code used to obtain the Node of Ranvier (NOR) currents in the NORs, to be imported into COMSOL. 
The code is freely modified based on MRG [axon model](https://senselab.med.yale.edu/ModelDB/showmodel.cshtml?model=3810#tabs-1) created by McIntyre, Richardson and Grill (DOI: [10.1152/jn.00353.2001](https://journals.physiology.org/doi/full/10.1152/jn.00353.2001)).
Changes have been made to make the simulation output compliant with the [COMSOL setup](https://github.com/fabianadelbono/PNrec/tree/main/Code/2.%20COMSOL).

## Model Inputs
The following changes to the original model have been made: 
1. The number of NORs has been set to values fitting a total fibre length of 60 mm, and is different for each diameter according to the internodal distance;
2. The number of the other sections, dependant on the number of NORs, has been parametrised accordingly;
3. Current is injected in the first NOR instead of the central one.
These changes have been made on the MRGaxon.hoc files. 

## Model Outputs
Furthermore, additional code has been created to obtain the desired output, namely formatted .txt files for each NOR containing the current values over time. 
Code has been written on files that are sequentially executed within mosinit.hoc
- vec_generationLoop.hoc is a script that executes the steps necessary to save the membrane currents as a vector;
- currentConversion.hoc is a script that converts each current i_membrane in a point process;
- fileCretionLoop.hoc creates the files;

The current outputs are formatted .txt files, where the first column contains the time steps and the second
column contains the value of the converted membrane current.

Currently, in this repository, one folder for each simulated diameter has been created, containing the scripts and current outputs. 
For running simulations, [NEURON](https://neuron.yale.edu/neuron/) must be installed, and mosinit.hoc has to be executed. 
