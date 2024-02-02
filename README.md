# XR-AR_NTC
# Augmented Reality and Cloud Gaming Network Traffic Discrimination
This is for XR/AR network traffic classification & Paper reproducibility.
## 1- Abstract
The Extended Reality (XR) technologies continue to advance, driven by hardware and software growth in this scope. In addition to use cases e.g. games and education which run a completely immersive, computer-generated environment by Virtual Reality (VR), there are some requirements that need to keep the user interactive with the real world and overlay the digital object onto the real world e.g. repair, maintenance, health care which it is done by Augmented Reality (AR). The AR applications and users are rising with having matured the VR Head Mounted Display (HMD) and software. The AR is sensitive to the computing resource, so it needs to offload its functionality to improve its flexibility but it makes it sensitive to delay; in addition, its  interaction with the real world makes this sensitivity more drastic. The discrimination of the network traffic belonging to AR, as the first step for appropriate resource allocation, is becoming more critical with the growth of its application and remote rendering capability.  In this paper, we propose a decision Tree (DT) and Random Forest (RF) model to classify the network traffic into AR, Cloud Gaming (CG) and others. Secondly, the features are examined to detect the AR and CG network traffic accurately. Thirdly, the model is evaluated with existing datasets to show its performance in accuracy, precision, recall, and f-score. Finally, a dataset for AR and CG are collected to be used in this research and published to pave the way for other research on AR network traffic discrimination. This paper is useful for those who are working on network traffic classification specifically AR network traffic classification.
## 2- The dataset features
a) IPI (Inter Packet Interval)
b) FS (Frame Size)
c) IFI (Inter Frame Interval)
## 3- Datasets with the features
### 3-1-Generating Features based on Johnson'U and the parameters in [23]
##### Run the 5_Generate_UL_DL_DS_.ipynb and set the numbr of samples and the address to store the csv files as below:

                                # Set the number of samples for generating
                                    n_sample = 1000
                                    
                               # Save the combined dataset to a CSV file (***************** Add your address to Save th CSV files)
                                    combined_dataset_LR.to_csv('AR_UL_LR.csv', index=False)
                                    combined_dataset_MR.to_csv('AR_UL_MR.csv', index=False)
                                    combined_dataset_HR.to_csv('AR_UL_HR.csv', index=False)
                                    combined_dataset_AR70.to_csv('AR_DL70.csv', index=False)
                                    combined_dataset_AR90.to_csv('AR_DL90.csv', index=False)
  The dataset will be generated for Uplink & Downlink sperated as below:
                                #####               Uplink 
                                          Low Resolution    --> 'AR_UL_LR.csv'|
                                          Medeum Resolution --> 'AR_UL_MR.csv'|
                                          High Resolution   --> 'AR_UL_HR.csv'|
                                #####               Downlink 
                                          Rate is 70Hz --> 'AR_DL70.csv'|
                                          Rate is 90Hz --> 'AR_DL90.csv'|
  

### 3-2-Extrct the features from PCAP(PCAPNG) files extracted
##### Run the 3_ReadPCAP_ExtractFeatures.ipynb and set the folder your pcap file is located as below...

                              # The root Directory (Enter your address)
                                  root_directory = r'Directory includes PCAP or PCAPnj Files'

                              # set the extension to find from the rood directory
                                  extension = '.pcapng'  # ('.pcap' or '.pcapng')
The csv files will be stored in the same folder. The next cell in the Python code merge the CSV files 
as DS.csv and then add direction (UL or DL) and preprocess the csv file. The final output is DS3.csv. 

### 3-3-Extrct the features from CSV files extracted from Wireshark
##### Run the 4_Read&Extract_Features_CSV.ipynb  and set the folder your pcap file is located as below...

                               # The root Directory (Enter your address)
                                  root_directory = r'Directory includes PCAP or PCAPnj Files'

                               # set the extension to find from the rood directory
                                  extension = '.csv'  # ('.pcap' or '.pcapng')
The csv files will be stored in the same folder. The next cell in the Python code merge the CSV files 
as DS.csv and then add direction (UL or DL) and preprocess the csv file. The final output is DS3.csv. 

## 4- Train and evaluate the DT model
### 4-1- Evaluation
Evaluation is done with Accuracy, precision, recall, f-score, and confusion matrix

#### 4-2- Run the 1_MultiClass_DT_ARCG.ipynb and only set the training dataset with the features in CSV format as below.
                               
                               # Load datasets
                              ### Enter your Dataset file address with csv format
                                  ar_data = pd.read_csv(r'AR.csv')
                                  cg_data = pd.read_csv(r'CG.csv')
                                  others_data = pd.read_csv(r'others.csv')
### 4-3- Test the model with other datasets
In Cell numbr 6 only set the test dataset you can test the DT model
                              
                              # Load the test dataset (Mentioned in Table (IV) of the Paper)
                                  AR_Test = pd.read_csv(r'AR-Test.csv')
                                  CG_Test = pd.read_csv(r'CG_Test.csv')
                                  Other_Test = pd.read_csv(r'Other_Test.csv')


## 5- Train and evaluate the RF model
### 5-1- Evaluation
Evaluation is done with Accuracy, precision, recall, f-score, and confusion matrix

#### 5-2- Run the 2_MultiClass_RF_ARCG.ipynb and only set the training dataset with the features in CSV format as below.
                               
                               # Load datasets
                              ### Enter your Dataset file address with csv format
                                  ar_data = pd.read_csv(r'AR.csv')
                                  cg_data = pd.read_csv(r'CG.csv')
                                  others_data = pd.read_csv(r'others.csv')
### 5-3- Test the model with other datasets
In Cell numbr 5 only set the test dataset you can test the DT model
                              
                              # Load the test dataset (Mentioned in Table (IV) of the Paper)
                                  AR_Test = pd.read_csv(r'AR-Test.csv')
                                  CG_Test = pd.read_csv(r'CG_Test.csv')
                                  Other_Test = pd.read_csv(r'Other_Test.csv')

## 6- Collected Dataset
It is available in https://kaggle.com/datasets/a906acd0ce4c8ee03048bf10c06573547ddca5a5c775ba592306bd04038f3a56

## 7- Conclusion
This document helps the reader of the paper to be able to reproduce the model and use it..

