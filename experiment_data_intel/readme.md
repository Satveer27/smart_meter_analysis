# Readme

This folder will extract and visualise all the data and tests done for Intel CPU for software vs software meters. The extract_data_ohm file will essentially log data from Hardware Monitor during tests. This is only used if you want to start a new test and log with hardware monitor. The clean_and_visualise.ipynb file will essentially take every single data from all the folders and visualise such data. It also does cleaning and aggregates data into files.

The intel_tests folder stores folders of experiments which contain csv files of experiments done in various meters. These are the raw data and these are results of tests done only for measuring the CPU.

The gpu_experiments folder is similar to intel_tests folder with the exception that the tests measure gpu energy consumption not CPU and had varied tests

The intel_overall_experiments stores a folders of different software meters which contain csv files of all their tests and experiments accumulated into 1 file. So for example, we did a tests using a laptop idle state, all 3 experiments data will be accumulated into 1 file and stored in this directory. This is not raw data but cleaned data.

The gpu_overall_experiments is the same as intel_overall_experiments with the exception that the tests measure gpu energy consumption not CPU and had varied tests.

The archives are previous failed experiments, but the result is stored just for reference.
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


