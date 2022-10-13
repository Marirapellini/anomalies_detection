# anomalies_detection
Pre-processing and Auto-encoders to detect anomalies in the BRIL detectors

In order to run the scripts:
1. after having accessed to the lxplus, add to the .bashrc the following: /cvmfs/sft.cern.ch/lcg/views/LCG_101/x86_64-centos7-gcc11-opt/setup.sh
2. set up a virtual environment on VSCode (add to the current user on lxplus the folder my_env. To do so:
a)in the folder, create a new virtual environment: python -m venv projectname
b) run source projectname/bin/activate to activate it
c) from inside the environment install ipykernel using pip: pip install ipykernel
d) run ipython kernel install --user --name=projectname to install a new kernel
4. choose my_env as kernel

In order to generate the dataframe for the BCM1F data:
1. add read_data.py  
2. use the FILLDATABCM1F script to generate the dataframe by using the function get_raw_data after having created the tunnel #sshfs -oProxyCommand="ssh -W %h:%p mrapelli@cmsusr.cern.ch"  mrapelli@brildev1:/brildata/22 try/

In order to plot the BCM1F dataframe: 
1. add read_data.py
2. use plots_bcm1f.ipynb to plot the fills; use the function get_raw_data and generate_plots after having created the tunnel #sshfs -oProxyCommand="ssh -W %h:%p mrapelli@cmsusr.cern.ch"  mrapelli@brildev1:/brildata/22 try/

In order to perform PCA use scripts PCA both for LumiData and BCM1F data.
In order to train the autoencoder, use the autoencoder scripts (the model is really sensible to the split between the train and test dataset).

There is also a script for training a LSTM (RNN).

The split between training and testing dataset is done by analyzing visually each fill and by deciding which fills are good for training and which one have 
anomalies that have to be detected (these would belong to the test dataset); at least 51% of the total number of fills should belong to the train dataset. 

Train data set: bcm1f_fills_8078.csv, bcm1f_fills_8076.csv, bcm1f_fills_8073.csv, bcm1f_fills_8072.csv, bcm1f_fills_8068.csv, bcm1f_fills_8063.csv, bcm1f_fills_8062.csv, bcm1f_fills_8059.csv, bcm1f_fills_8058.csv, bcm1f_fills_8057.csv, bcm1f_fills_8046.csv, bcm1f_fills_8043.csv ,bcm1f_fills_8033.csv, bcm1f_fills_8030.csv, bcm1f_fills_8023.csv, bcm1f_fills_8022.csv, bcm1f_fills_8018.csv, bcm1f_fills_7978.csv, bcm1f_fills_7967.csv, bcm1f_fills_7966.csv, bcm1f_fills_7965.csv, bcm1f_fills_7923.csv, bcm1f_fills_7921.csv

Test data set: bcm1f_fills_8151.csv, bcm1f_fills_8067.csv, bcm1f_fills_8057.csv, bcm1f_fills_8027.csv, bcm1f_fills_8020.csv, bcm1f_fills_8019.csv, bcm1f_fills_8017.csv, bcm1f_fills_8016.csv, bcm1f_fills_8007.csv, bcm1f_fills_7969.csv, bcm1f_fills_7963.csv, bcm1f_fills_7960.csv

