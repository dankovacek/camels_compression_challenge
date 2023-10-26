# Camels Compression Challenge

![Camels Compression Challenge Logo - a sequence of objects representing a progression from a finely detailed camelid to an abstract geometric object.](images/CC_Challenge_Logo.png)
An open challenge for hydrological time series data compression.

## Leaderboard

| Date | Name / Team | Score |
|---|---|---|
| - | - | 99 |

The score is the compression ratio (CR) of the test set. The lower the better.

## Motivation

The last five years of research (as of October 2023) have seen ML models reach state of the art in rainfall-runoff modelling.  Physics based model research will continue to yield insights into underlying physical processes in hydrological processes.  We are not aware of any approaches to hydrological modelling that are *reducing in complexity*.

1.  1973: Sacramento Soil Moisture Accounting Model (SAC-SMA) [1] is about 700 lines of Fortran code in three files, see [here](https://github.com/Upstream-Tech/SACSMA-SNOW17/tree/master/sacsma_source_original/sac).  Conceptual Rainfall Runoff (CRR) models typically use O(10) parameters to empirically represent water storages and interconnectivity. [6]  

2.  The [Raven hydrological modeling framework](http://raven.uwaterloo.ca/Main.html) [5] is in active development.  Its source code is < 1 MB (in compressed form).  Its architecture allows for selective inclusion of process representation (evapotranspiration, snowmelt, soil moisture, etc.), and individual calibration weight files for sub-basins (HRUs) in the order of 10-100kB.  As such, predicting at many locations could have many sub-basin calibration files.  Input data includes elevation, land cover, soil, meteorological forcings, etc.

3.  Source code for the [Neuralhydrology](https://github.com/neuralhydrology) [7] is a Deep Learning neural network Python library uses several external libraries (i.e. PyTorch), and employs a neural network with O(105) weights (30, 20, 64 neurons per layer in embedding network hidden layers for static and dynamic inputs. (Need to verify!) Input data includes meteorological forcings & static basin attributes. 


Model performance is not commonly expressed in total description length (TDL), but it could be very useful as a standard metric.  “A model that compresses well generalizes well” [4].  

The Camels Compression Challenge is motivated by the work of Marcus Hutter in Artificial Intelligence [9], and the efforts led by Steven Weijs to translate the compression problem to hydrological time series data [2, 3].

## Goals

1. Better understand links between data compression, prediction, & physical processes.  
2. Engage participants from diverse disciplines.  
3. Encourage new approaches to hydrological modeling.  


## Rules

### General

The goal of this challenge is to encourage the development of models that are simpler, more interpretable, and more generalizable.  The challenge is to compress the Camels dataset [8] to the smallest size possible, while still being able to exactly reproduce the original dataset.  

(from the [Hutter Prize wikipedia](https://en.wikipedia.org/wiki/Hutter_Prize#:~:text=The%20Hutter%20Prize%20is%20a,in%20artificial%20intelligence%20(AI).)):
>The challenge is open-ended and open to everyone.  To enter, simply submit a compression program and a decompressor that decompresses the full set of *(Camels precipitation and time series)* data to its original form.  The total size of the compressed file and decompressor (as a Win32 or Linux executable file) must be less than or equal to 99% of the *(existing leading entry)*.  

The decompressor code must include an open-source license, such as the [MIT license](https://opensource.org/license/mit/) to best synthesize and share what is learned from different approaches.

### Hardware

The final submission executable must be able to exactly reproduce the original dataset on a single-core i7 CPU with 16GB RAM within 10h of run time. 

### Data

The dataset to be used for compression is contained in the data folder of this repository.  The data corresponds to version 1.2 of the open-access published Camels dataset [8], [downloaded from GDEX](https://ral.ucar.edu/solutions/products/camels) on October 26, 2023.

## References

1.  Burnash, Robert JC, and R. Larry Ferral. A generalized streamflow simulation system: Conceptual modeling for digital computers. US Department of Commerce, National Weather Service, and State of California, Department of Water Resources, 1973.  

2.  Weijs, Steven V., Nick Van de Giesen, and Marc B. Parlange. "HydroZIP: How hydrological knowledge can be used to improve compression of hydrological data." Entropy 15.4 (2013): 1289-1310.  

3.  Weijs, Steven V., N. Van De Giesen, and M. B. Parlange. "Data compression to define information content of hydrological time series." Hydrology and Earth System Sciences 17.8 (2013): 3171-3187.

4. Delétang, Grégoire, et al. "Language modeling is compression." arXiv preprint arXiv:2309.10668 (2023).  

5.  Craig, James R., et al. "Flexible watershed simulation with the Raven hydrological modelling framework." Environmental Modelling & Software 129 (2020): 104728.  

6.  Vrugt, Jasper A., et al. "Application of stochastic parameter optimization to the Sacramento Soil Moisture Accounting model." Journal of Hydrology 325.1-4 (2006): 288-307.  

7.  Kratzert, Frederik, et al. "NeuralHydrology---A Python library for Deep Learning research in hydrology." Journal of Open Source Software 7.71 (2022): 4050.  

8.  Newman, A. J., Clark, M. P., Sampson, K., Wood, A., Hay, L. E., Bock, A., Viger, R., Blodgett, D., Brekke, L., Arnold, J. R., Hopson, T. and Duan, Q.: Development of a large-sample watershed-scale hydrometeorological dataset for the contiguous USA: dataset characteristics and assessment of regional variability in hydrologic model performance, Hydrology and Earth System Sciences, 19, 209–223, doi:10.5194/hess-19-209-2015, 2015.  

9. Legg, Shane, and Marcus Hutter. "Universal intelligence: A definition of machine intelligence." Minds and machines 17 (2007): 391-444.  




