# Readme

The code will extract out data given the csv file and plot it. The extract_data_trad.ipynb file will essentially extract out data from the videos for traditional meters and store these results in a CSV file. The clean_visualise_ipynb file will extract these results from the CSV and visualise them. 

The csv_file_smart_meter contains folders of experiments done and within the folders are the raw data files of the smart meter results. 

The csv_file_traditional contains folders of experiments which have extracted data from the video and stored inside the csv file.

The output_dir folder is simply a directory in which our code will extract video frames and store it in such directory. Right now this directory contains images of my latest video I uploaded to extract out the data.

## Build instructions

You can follow the instructions for each cell inside the notebook or ipynb file. One thing to note is the extact data ipynb file will not work properly unless an Open AI key is provided and the video, in my case I did not store all video files in gitlab as it takes up storage.

### Requirements

* Python 3.10.8
* Packages: 
    * opencv-python
    * openai
    * pytesseract
    * boto3
    * pandas
    * matplotlib
    * numpy
    * scipy

* Tested on Windows 10

### Build steps

Pip install the given packages above one by one before running the notebook. 

