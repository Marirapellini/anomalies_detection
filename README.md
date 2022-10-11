# anomalies_detection
Pre-processing and Auto-encoders to detect anomalies in the BRIL detectors

In order to run the scripts:
1. add to the .bashrc the following: /cvmfs/sft.cern.ch/lcg/views/LCG_101/x86_64-centos7-gcc11-opt/setup.sh
2. set up a virtual environment on VSCode (add to the current user on lxplus the folder my_env) (https://anbasile.github.io/posts/2017-06-25-jupyter-venv/)
3. choose my_env as kernel

In order to generate the dataframe for the BCM1F data:
1. add read_data.py  
2. use the FILLDATABCM1F script to generate the dataframe by using the function get_raw_data after having created the tunnel #sshfs -oProxyCommand="ssh -W %h:%p mrapelli@cmsusr.cern.ch"  mrapelli@brildev1:/brildata/22 try/

In order to plot the BCM1F dataframe: 
1. add read_data.py
2. use plots_bcm1f.ipynb to plot the fills; use the function get_raw_data and generate_plots after having created the tunnel #sshfs -oProxyCommand="ssh -W %h:%p mrapelli@cmsusr.cern.ch"  mrapelli@brildev1:/brildata/22 try/

In order to perform PCA use scripts PCA both for LumiData and BCM1F data.
In order to train the autoencoder, use the autoencoder scripts (the model is really sensible to the split between the train and test dataset).

There is also a script for training a LSTM (RNN).

The split between training and testing dataset is done by analyzing visually each fill and by deciding which fills are good for training and which one have anomalies that have to be detected (these would belong to the test dataset); at least 51% of the total number of fills should belong to the train dataset. 
