## Data
These are folders which contain the raw data csv depending on the tests. I will provide a brief overview of how each folder collected these data.

1.) hwinfo/ -> I utilised the logging feature inside hwinfo UI interface to collect these data, these data was collected via 5 minutes for each load(folder inside this directory). The data stored here is the CPU energy consumption under different loads(the folder inside this directory).

2.)hwinfo_gpu/ -> it is the same as hwinfo/ directory with the exemption that the data stored was GPU energy consumption and different load test were done.

3.)nvidia-sim/ -> I utilised the command line interface to log data directly from nvidia sim. These data were again collected via 5 minutes for each load(folder inside this directory). The data stored here is the GPU energy consumption under different loads.

4.)ohm/ -> I utilised the code from the experiment_data_intel to extract out open hardware monitor data for 5 minutes and store it in a csv file for each load(folder inside this directory). The data stored here is the CPU energy consumption under different loads. 

5.)ohm_gpu/ -> it is the same as ohm/ directory with the exemption that the data stored was GPU energy consumption and different load test were done.



