# data_science_coursework

README

This is a data analysis pipeline written using spike2py and Neo in Python to visualise and apply signal corrections to data from the prototype phase of a virtual reality setup for mice. The goal is to analyse behavioural input while mice navigate a linear track, receiving reward at the designated point (in this case the end of the track). This pipeline may also be used to analyse the behavioural data produced by a fully functioning virtual reality setup recording data through Spike2.

To run:
1.	Please ensure Python is running at version 3.8 or later.
a.	Note: This notebook will not run on Google Colab as it uses Python version 3.6.9. The scripts in this notebook, in particular Spike2Py, require Python 3.8 onwards as ‘typing. Literal’ is only available from this version onwards.
2.	Place the folder “neo” from the uploaded coursework folder, or from: “https://pypi.org/project/neo/0.5.2/” in the “\site-packages” folder in your Anaconda3 directory. This filepath should look something like: “C:\Users\USERNAME\Anaconda3\Lib\site-packages”
3.	Download all Python scripts and files ‘VR_prototype_traces.mat’, and ‘VR_prototype_traces.smr’. Place these files into the same directory as your Jupyter notebook. This filepath will look something like 'C:\\Users\USERNAME’.
a.	Note that Neo requires files to me in .smr format, whereas spike2py requires files to be in .mat format. See below on how to change .smr files to .mat.
4.	Load the ‘VR_analysis.ipynd’ file and run all scripts inside.
5.	You can edit the values for lowpass(cutoff = x) to introduce a higher or lower (measured in Hz) low pass filter to the data, reducing any noise.
6.	If you wish to change the file being analysed, in the spike2py code section: 
from spike2py.trial import TrialInfo, Trial
trial_info = TrialInfo(file='VR_prototype_traces.mat')
data = Trial(trial_info)
trial_info
In the neo code section, change: 
reader = neo.io.Spike2IO(filename='VR_prototype_traces.smr', try_signal_grouping=False)
to include your filename.
Change the file name within TrialInfo(file=’VR_prototype_traces.mat’) to the file you have chosen. Please note that data analysed by spike2py must be in .mat format. Spike2Py will automatically detect channel names based on their names in Spike2 – ensure these names are changed in the Python script to reflect your data.

In order to convert .smr files to .mat files, run the script located within the folder Spike2-batch-export-to-Matlab-master, titled: ‘Spike2_batch_export_to_Matlab’ within Spike2. You will be directed to select the directory in which your .smr file(s) exists. This script will then produce .mat files in the same directory, which you may use with spike2py. Note: make sure these new .mat files are placed in the correct filepath for the VR analysis script to run.
