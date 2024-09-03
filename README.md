# Siemens-Prisma-3T-MRI-Scanner-gui-for-ECG-analysis

## Requierments:

MatlabR2023b

## Installations:

Download the files : Simens ECG Signal Processing.mlappinstall, Simens ECG Signal Processing.prj and config.mat, to a local working dirctory on your pc.
open matlab on your working dirctory and double click on Simens ECG Signal Processing.mlappinstall.

This will install the App on your Matlab toolbar:

![image](https://github.com/user-attachments/assets/986f1de0-979a-45d9-9bff-4354b50f584f)

Image 1: App icon in Matlab toolbar 
## Preperation of Data:

The App is designed for a certain data architecture, that can be defined in the configuration file.
The design is as follow:  {Path_data}\{sub_ - subject directory}\{Loc}

The data in the folder is the log files acquired by the Siemens MRI scanner.
For example:

![image](https://github.com/user-attachments/assets/ea1113b7-8540-4587-805e-d1f17d59c63c)

Image 2: Siemens log files

For each run the MRI will provide AcquisitionInfo with a time stampt and task/run name and four ECG logs , each corresponding to ECG electrode(channel) attached to the subject.

## Preperation of Configuration File:
In the ataached files provided the config.m as an example.
The config.m file contains: 
1. Path_data - this is the dirctory containing all subfolders of each subject.
2. Loc - in each subject folder the location od the directory of Siemens's ECG log files.
3. Outputpath  - the directory where the results will be saved.
4. Tasks  - the names of the tasks of the log files for example in the image above "Cartman_Game" (the same as appear in the AcquisitionInfo log) .

![image](https://github.com/user-attachments/assets/b4e55bcb-d89b-4230-a2da-82c975d4d339)

![image](https://github.com/user-attachments/assets/0c6c946b-81c6-4461-9b31-b68d425de7cf)

Image 3: config.m file

The easiest way to prepare your own config file is to load an existing file and just change it .

We will open the App from matlab app tool bar (double click on Icon in image 1):

***only open the App when you are in matlab working directory where the config file is located.

this will open the following window:

![image](https://github.com/user-attachments/assets/71d9e507-7f39-4638-857d-c9206bb751bd)

press on "Load Existing File" and choose config.m

![image](https://github.com/user-attachments/assets/877dd233-0967-48de-97d8-bf1a3e2d89a4)

Now you can manually change to your own configuration.

***pay attention to "/" if there is or not at the end of the path.

To remove task stand on the task you wish to remove and press "Remove task"

To add task enter task name (as it apear in the AcquisitionInfo log) and press "Add task"
than enter config name and press "Save confif File".

## Run
1. double click on Icon in image 1.
2. "Load Existing File" and choose the correct config.m you created and press "Start"
3. You will be transfered to the data loading window:
   ![image](https://github.com/user-attachments/assets/c9256b5a-af04-46fa-901c-e255f3b8ae04)
4. Press "ECG Data Directory" if your configuration is set you will see the folder with all subjects, just continue with Select Folder immdiatly don't change any thing (here you need to make sure that your data architecture as dexcribed in "Preperation of Data ").
   ![image](https://github.com/user-attachments/assets/eeaa24f1-99a1-4be6-b57c-89b12ca3e800)
5.Now all Subject list will be loaded into Subject. Choose the Subject you want to visualize and tag , Choose the desired Task and Electrode (default is 1).
In case of several runs per task on the List Box will apeare all logs for that task.
**Sometimes there will be Acquisition log but not the corresponding ECG1,ECG2,ECG3 and ECG4 logs, make sure that you have those.
**All electrode (channels) should work the same, we will only change electrode number if for some reason the data looks noisey on the first channel so we will look for better signal input on the rest of the channels

![image](https://github.com/user-attachments/assets/cccb5b8c-c6f3-45ea-adb4-3b075e862c0c)
 choose a desired log file and press "Next".
 6. Lets Tag away :) in the next window we can visualized the clean signal (if you don't see the signal just press >> and << and it will apeare)
 ![image](https://github.com/user-attachments/assets/0590c48f-b1d8-45d5-8ac7-f6aa8d8f0bc9)



