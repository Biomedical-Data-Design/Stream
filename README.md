# Stream

Zhenyu Xiao, Haobin Zhou, Yimeng Xu, and Emma Cardenas.

We are a group of students from Johns Hopkins University. Our project is focusing on **Track patient recovery in real-time by processing streaming data** in the course Biomedical Data Design.

This repository will contain our source codes and progress every week.

The database we are using is **eICU Database**, you can access the database on their website after completing the course on data security and ethics: https://physionet.org/content/eicu-crd/2.0/

## <a name="Tutorial">Tutorial:</a>
The project is written in Python 3. You can use the software online using [Colaboratory](#Colaboratory) and upload your data to your Google Drive, or run it on your local machine. 

### <a name="Colaboratory">Colaboratory:</a> the platform independent and online solution

**STEP 1: Clone Github Repo into Colab**

To clone the Github Repo, click and run [this link](https://colab.research.google.com/drive/10gxtdar30BKisl2nQVtBzF25HMZpFht3?usp=drive_linkhttps://colab.research.google.com/drive/10gxtdar30BKisl2nQVtBzF25HMZpFht3?usp=drive_link). This will create a folder named 'Stream' in your Google Drive.


**STEP 2: Upload eICU**

Upload eICU files (unzipped) to your Google Drive and rename the path as: 'EICU/eicu-collaborative-research-database-2.0'


**STEP 3: Extract Available Patient IDs**

Go to file 'Stream/Preprocess/func_check_patient_num.ipynb' and run the notebook. This notebook will extract patients with all 13 features available and generate the file 'Final_available_patients.csv'. The generated file should be in 'My Drive/Colab Notebooks'. This step shall take a few minutes if using the whole eICU database.


**Step 4: Extract Data & Align**

Run all features' extract functions and interpolate functions in the 13 other notebooks in 'Stream/Preprocess'. They are named as follows:
* BloodPressure.ipynb
* Glasgow.ipynb
* HeartRate.ipynb
* lab1.ipynb
* lab2.ipynb
* lab3.ipynb
* lab4.ipynb
* lab5.ipynb
* lab6.ipynb
* Pao2fio2-fio2.ipynb
* Pao2fio2-pao2.ipynb
* Temp.ipynb
* Urine.ipynb

The preprocessed data will be saved in 'My Drive/Colab Notebooks' directory in the format of 'feature_name.csv'. 


**Step 5: Concatenate Data for Models**

First, run 'Stream/Preprocess/Patient_Results.ipynb' to generate 'mortality_data.csv'. Then, run 'Stream/Preprocess/Organize_all_data.ipynb' to merge all the features into one file.

As written in the paper, we used 3 machine learning models and 1 deep learning model.

For the 3 machine learning models, you can use the file in [this link](https://drive.google.com/file/d/10RkQjXARP12Cg5cZ0VMmo3SdQujcRlHw/view?usp=drive_link) as the input data and run the notebook 'Stream/Models/ml_models.ipynb'.

For the deep learning model, you can use the files in [this link](https://drive.google.com/drive/folders/16Yx3xpf1utNfylB_NOchDhEWlTB2L7U5?usp=drive_link) as the input data and run the notebook 'Stream/Models/LSTM.ipynb'.

