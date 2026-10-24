These are folders which contain the raw data csv depending on the tests. This will only store the CPU energy consumption tests. Each folder here is a load and within each folder contains another directory of the names of the software meter, within those folder contains the raw CSV data file. I will give a breakdown of how I got these raw data for each of the software meter.

2.)hwinfo ->  I utilised the logging feature inside hwinfo UI interface to collect these data, these data was collected via 5 minutes for each load. The data stored here is the CPU energy consumption under different loads.

3.)intel_gadget -> I utilised the intel power gadget UI to log data for 5 minutes and the data is stored in the csv file as shown. The data stored here is the CPU enegry consumption under different loads.

5.)hardware_monitor -> I utilised the code from the extract_data_ohm.ipynb to extract out open hardware monitor data for 5 minutes and store it in a csv file for each load. The data stored here is the CPU energy consumption under different loads. 