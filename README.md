# Stream: Biomedical Data Design Project Repository

**Contributors:** Zhenyu Xiao*, Haobin Zhou*, Yimeng Xu, and Emma Cardenas.

**Affiliation:** Department of Biomedical Engineering, Johns Hopkins University

## <a>Project Overview</a>

This repository is part of the **Biomedical Data Design** course, where we focus on tracking patient recovery in real time by processing streaming data. The primary data source for this project is the **eICU Collaborative Research Database**, accessible on their [official website](https://physionet.org/content/eicu-crd/2.0/) after completing the required course on data security and ethics.

Included here are the source code, weekly presentation slides, and additional resources necessary to understand and engage with our project.

## <a>Getting Started:</a>
This project is written in Python 3. You can run this project online using [Colaboratory](#Colaboratory) and upload your data to your Google Drive (Recommended), or run it on your [local machine](#Local).

### <a name="Colaboratory">Google Colaboratory</a>
When using Google Colaboratory, most of the CSV files will be generated in the directory 'My Drive/Colab Notebooks', only the model input data will be stored in 'Stream/Models' automatically. 

#### STEP 1: Clone Github Repo into Colaboratory
To clone the Github Repository into Google Colaboratory, click and run [this link](https://colab.research.google.com/drive/10gxtdar30BKisl2nQVtBzF25HMZpFht3?usp=drive_linkhttps://colab.research.google.com/drive/10gxtdar30BKisl2nQVtBzF25HMZpFht3?usp=drive_link). You will create a folder named 'Stream' in your Google Drive.


#### STEP 2: Upload eICU
Upload eICU files (unzipped) to your Google Drive and rename the path as: 'EICU/eicu-collaborative-research-database-2.0'


#### STEP 3: Extract Available Patient IDs

Run the file 'Stream/Preprocess/func_check_patient_num.ipynb'. This notebook will filter patients with unavailable features and generate the file 'Final_available_patients.csv'. 


#### Step 4: Extract Data & Align

Run these notebooks in 'Stream/Preprocess' to extract data and interpolate with GPR (except 'Patient_Results.ipynb'):
* BloodPressure.ipynb
* Glasgow.ipynb
* HeartRate.ipynb
* Pao2fio2-fio2.ipynb
* Pao2fio2-pao2.ipynb
* Temp.ipynb
* Urine.ipynb
* lab1.ipynb
* lab2.ipynb
* lab3.ipynb
* lab4.ipynb
* lab5.ipynb
* lab6.ipynb
* Patient_Results.ipynb

***This step will be time-consuming if using the whole eICU database.***


#### Step 5: Concatenate Data & Run

Run 'Stream/Preprocess/Organize_all_data.ipynb' to merge all the features into '13features.csv'.

As written in Section 4 of the paper, we used 3 machine learning models and 1 deep learning model.

For **Machine Learning models**, run the notebook 'Stream/Preprocessing/ml_models.ipynb' or use [this file](https://drive.google.com/file/d/10RkQjXARP12Cg5cZ0VMmo3SdQujcRlHw/view?usp=drive_link), then run the notebook 'Stream/Models/ml_models.ipynb' to evaluate the performance of ML models.

For **LSTM**, run the notebook 'Stream/Preprocessing/Balance_LSTM.ipynb' to generate the balanced data or use the files in [this link](https://drive.google.com/drive/folders/16Yx3xpf1utNfylB_NOchDhEWlTB2L7U5?usp=drive_link), then run the notebook 'Stream/Models/LSTM.ipynb' to evaluate the performance of LSTM (you may use GPU to accelerate this final process). 


### <a name="Local">Local Machine</a>
To run the project locally:
- Adjust file paths in the code to your local directories.
- Set up your environment using Anaconda and CUDA as needed. See the installation guide below for details.

#### Installation Guide
Here we provide an example of how to install the environment on a local machine using Anaconda and CUDA 11.8. For non-GPU & other CUDA version installation, please refer to the [PyTorch website](https://pytorch.org/get-started/locally/) when installing PyTorch. We remark that this repository does not depend on a specific CUDA version, feel free to use any CUDA version suitable on your own computer.

``` Bash
# create conda environment
conda create -n bdd python=3.9 -y
conda activate bdd
conda install numpy pandas matplotlib scikit-learn xgboost jupyter pytorch torchvision torchaudio pytorch-cuda=11.8 -c pytorch -c nvidia
```

Even though here we provide 'environment.yaml', it may have redundancy. We recommend you try to install other required packages by running the code and finding which required package hasn't been installed yet.

