# Readme

This folder will extract and visualise all the data and tests done for AMD CPU for software vs software meters. The clean_and_visualise.ipynb file will essentially take every single data from all the folders and visualise such data. It also does cleaning and aggregates data into files.

The all_experiment_data folder stores folders of experiments which contain csv files of experiments done in various meters. These are the raw data and these are results of tests done only for measuring the both the CPU and the GPU.

The amd_overall_experiments stores a folders of different software meters which contain csv files of all their tests and experiments accumulated into 1 file. So for example, we did a tests using a laptop idle state, all 3 experiments data will be accumulated into 1 file and stored in this directory. This is not raw data but cleaned data.

The amd_overall_experiments_gpu is the same as amd_overall_experiments with the exception that the tests measure gpu energy consumption not CPU and had varied tests.

## Build instructions

You can follow instructions given in the notebook to run the various cells. 

### Requirements

* Python 3.10.8
* Packages: 
    * pandas
    * matplotlib
    * numpy
    * scipy
    * pythonnet

* Tested on Windows 10


### Build steps

You must manually do `pip install {package name}` the package name is given above under packages. After that just simply run the cells in the notebook and you are good to go.