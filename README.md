# XR-AR_NTC
# Augmented Reality and Cloud Gaming Network Traffic Discrimination
This is for XR/AR network traffic classification & Paper reproducability.
## 1- Abstract
The Extended Reality (XR) technologies continue to advance, driven by hardware and software growth in this scope. In addition to usecases e.g. game and education which is run a completely immersive, computer-generated environment by Virtual Reality (VR), there are some requirements which need to keep the user interactive with real world and overlay the digital object onto the real world e.g. repair, maintenance, health care which it is done by Augmented Reality (AR). The AR applications and users are rising with having been matured the VR Head Mounted Display (HMD) and software. The AR is sensitive to the computing resource, so it needs to offload its functionality to improve its flexibility but it makes it sensitive to delay; in addition, its  interaction with the real world makes this sensitivity more drastic. The discrimination of the network traffic belonging to AR, as the first step for appropriate resource allocation, is becoming more critical with the growth of its application and remote rendering capability.  In this paper, we propose a decision Tree (DT) and Random Forest (RF) model to classify the network traffic into AR, Cloud Gaming (CG) and others. Secondly, the features are examined to detect the AR and CG network traffic accurately. Thirdly, the model is evaluated with existing datasets to show its performance in accuracy, precision, recall, and f-score. Finally, a dataset for AR and CG are collected to used in this research and published to pave the way for other research on the AR network traffic discrimination. This paper is useful for those are working on the network traffic classification specifically AR network traffic classification.
## 2- The dataset features
a) IPI (Inter Packet Interval)
b) FS (Frame Size)
c) IFI (Inter Frame Interval)
## 3- Training the Decision Tree (DT) Model
The training dataset for three applications (AR,CG and others) needed to be loaded and trained by the model. 
Dataset will be divided into 90% for training and 10% for evaluation. 
### 2-1-1 Training Dataset 
#### 2-1-1-1- AR Training Dataset
The features
**(a)** generated with statistical model
You need to run the python code listed in this repository (5-Generate_UL_DL_DS.ipynb) and generate the datasets for three features IPI, FS, and IFI. 
This code was developed basd on reference [23] in the paper. 
The output will be five csv files for uplink and downlink:

#####               Uplink 
                        Low Resolution    --> 'AR_UL_LR.csv'|
                        Medeum Resolution --> 'AR_UL_MR.csv'|
                        High Resolution   --> 'AR_UL_HR.csv'|
#####               Downlink 
                        Rate is 70Hz --> 'AR_DL70.csv'|
                        Rate is 90Hz --> 'AR_DL90.csv'|
**(b)** extrct from the PCAP                         
To add the VR to Downlink, we need to extract the IPI, FS, IFI from the PCAP datasets published in [37]. With tune the folder address in python code in '3_ReadPCAP_ExtractFeatures.ipynb'
the dataset witll be extrcted in csv files.
-----------------------------------------------------------
**(C)** Concatinate the Datasets and shuffle the samples are doint with this instruction in Python.

             ** df = pd.concat(UL1,UL2,UL3, ignore_index=True, sort=False).sample(frac=1)**

