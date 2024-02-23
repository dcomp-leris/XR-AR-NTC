# From Pixels to Packets: Traffic Classification of Augmented Reality and Cloud Gaming

## 1- Abstract
Augmented Reality (AR) real-time interaction between users and digital overlays in the real world demands low latency to ensure seamless experiences. To address computational and battery constraints, AR devices often offload processing-
intensive tasks to edge servers, enhancing performance and user experience. With the increasing adoption and complexity of AR applications, especially in remote rendering, accurately classifying AR network traffic becomes essential for effective resource allocation. This paper explores two methods based on Decision Tree (DT) and Random Forest (RF) to classify network traffic among AR, Cloud Gaming (CG), and other categories. We rigorously analyze specific features to precisely identify AR and CG traffic. Our models demonstrate robust performance, achieving accuracy rates ranging from 88.40% to 94.87% against pre-existing datasets. Moreover, we contribute with a novel dataset encompassing AR and CG traffic, curated specifically for this study and made publicly available to facilitate reproducible research in AR network traffic classification.

## 2- The dataset features
(a) IPI (Inter Packet Interval), (b) FS (Frame Size), and (c) IFI (Inter Frame Interval).

## 3-Generate Dataset using Statistical Distribution Model

### 3-1-Generating Features based on Johnson'U and the parameters in [23]
##### Run the **5_Generate_UL_DL_DS_.ipynb** and set the number of samples and the address to store the CSV files as below:

                                # Set the number of samples for generating
                                    n_sample = 1000
                                    
                                # Save the combined dataset to a CSV file (***************** Add your address to Save the CSV files)
                                    combined_dataset_LR.to_csv('AR_UL_LR.csv', index=False)
                                    combined_dataset_MR.to_csv('AR_UL_MR.csv', index=False)
                                    combined_dataset_HR.to_csv('AR_UL_HR.csv', index=False)
                                    combined_dataset_AR70.to_csv('AR_DL70.csv', index=False)
                                    combined_dataset_AR90.to_csv('AR_DL90.csv', index=False)
  The dataset will be generated for Uplink & Downlink separated as below:
                                #####               Uplink 
                                          Low Resolution    --> 'AR_UL_LR.csv'|
                                          Medeum Resolution --> 'AR_UL_MR.csv'|
                                          High Resolution   --> 'AR_UL_HR.csv'|
                                #####               Downlink 
                                          Rate is 70Hz --> 'AR_DL70.csv'|
                                          Rate is 90Hz --> 'AR_DL90.csv'|
  

### 3-2-Extract the Features from PCAP(PCAPNG) Source Files 
##### Run the **3_ReadPCAP_ExtractFeatures.ipynb** and set the folder your PCAP file is located as below...

                              # The root Directory (Enter your address)
                                  root_directory = r'directory includes PCAP or PCAPnj Files'

                              # set the extension to find from the rood directory
                                  extension = '.pcapng'  # ('.pcap' or '.pcapng')
The CSV files will be stored in the same folder. The next cell in the Python code merges the CSV files
as DS.csv, then adds direction (UL or DL) and preprocesses the CSV file. The final output is DS3.csv which is located in the root directory. 

### 3-3-Extract the features from CSV files
##### Run the **4_Read&Extract_Features_CSV.ipynb** and set the folder your PCAP file is located as below...

                               # The root Directory (Enter your address)
                                  root_directory = r'directory includes PCAP or PCAPnj Files'

                               # set the extension to find from the root directory
                                  extension = '.csv'  # ('.pcap' or '.pcapng')
The CSV files will be stored in the same folder. The next cell in the Python code merges the CSV files 
as DS.csv and then adds direction (UL or DL) and preprocesses the CSV file. The final output is DS3.csv. 

## 4- Train and Evaluate the DT Model
### 4-1- Evaluation
Evaluation is done with Accuracy, precision, recall, f-score, and confusion matrix

#### 4-2- Run the **1_MultiClass_DT_ARCG.ipynb** and only set the training dataset with the features in CSV format as below.
                               
                               # Load datasets
                              ### Enter your Dataset file address with CSV format
                                  ar_data = pd.read_csv(r'AR.csv')
                                  cg_data = pd.read_csv(r'CG.csv')
                                  others_data = pd.read_csv(r'others.csv')
### 4-3- Test the model with other datasets
In Cell number 6 only set the test dataset you can test the DT model
                              
                              # Load the test dataset (Mentioned in Table (IV) of the Paper)
                                  AR_Test = pd.read_csv(r'AR-Test.csv')
                                  CG_Test = pd.read_csv(r'CG_Test.csv')
                                  Other_Test = pd.read_csv(r'Other_Test.csv')


## 5- Train and evaluate the RF model
### 5-1- Evaluation
Evaluation is done with Accuracy, precision, recall, f-score, and confusion matrix

#### 5-2- Run the **2_MultiClass_RF_ARCG.ipynb** and only set the training dataset with the features in CSV format as below.
                               
                               # Load datasets
                              ### Enter your Dataset file address with csv format
                                  ar_data = pd.read_csv(r'AR.csv')
                                  cg_data = pd.read_csv(r'CG.csv')
                                  others_data = pd.read_csv(r'others.csv')
### 5-3- Test the model with other datasets
In Cell number 5 only set the test dataset you can test the DT model
                              
                              # Load the test dataset (Mentioned in Table (IV) of the Paper)
                                  AR_Test = pd.read_csv(r'AR-Test.csv')
                                  CG_Test = pd.read_csv(r'CG_Test.csv')
                                  Other_Test = pd.read_csv(r'Other_Test.csv')

## 6- Collected Dataset

The collections are available:

AR --> https://kaggle.com/datasets/a906acd0ce4c8ee03048bf10c06573547ddca5a5c775ba592306bd04038f3a56

CG--> https://www.kaggle.com/datasets/carloshfm/cloud-gaming-network-telemetry/data

## 7- Conclusion
This document helps the reader of the paper to be able to reproduce the model and use it.

## 8- License

All the assets in this repo is released under the [BSD-3 License](https://opensource.org/license/bsd-3-clause/). You are free to use, modify, and distribute this software, provided that you include the original copyright notice and disclaimers. The BSD-3 License is a permissive open-source license that encourages collaboration and innovation. It grants you the freedom to adapt this software to your needs while respecting the original author's contributions. Feel free to contribute to the project or build upon it for your own projects. Please review the LICENSE file on the root of this repo for the full terms and conditions of this license.

