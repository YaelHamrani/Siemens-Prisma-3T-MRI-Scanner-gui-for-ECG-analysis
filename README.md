# Siemens-Prisma-3T-MRI-Scanner-gui-for-ECG-analysis

## Requierments:

MatlabR2023b

## Installations:

Download the files : Simens ECG Signal Processing.mlappinstall, Simens ECG Signal Processing.prj and config.mat, to a local working dirctory on your pc.
Open matlab on your working dirctory and double click on Simens ECG Signal Processing.mlappinstall.

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

For each run the MRI will provide an AcquisitionInfo log with a time stamp and task/run name, and four ECG logs, each corresponding to ECG electrode(channel) attached to the subject.

## Preperation of Configuration File:
In the attached files provided config.m is used as an example.
The config.m file contains: 
1. Path_data - this is the dirctory containing all subfolders of each subject.
2. Loc - in each subject folder the location of the directory of Siemens's ECG log files.
3. Outputpath - the directory where the results will be saved.
4. Tasks - the names of the tasks of the log files. For example in the image above "Cartman_Game" (the same as appeared in the AcquisitionInfo log) .

![image](https://github.com/user-attachments/assets/b4e55bcb-d89b-4230-a2da-82c975d4d339)

![image](https://github.com/user-attachments/assets/0c6c946b-81c6-4461-9b31-b68d425de7cf)

Image 3: config.m file

The easiest way to prepare your own config file is to load an existing file and just change it .

Open the App from matlab app tool bar (double click on Icon in image 1):

***only open the App when you are in matlab working directory where the config file is located.

This will open the following window:

![image](https://github.com/user-attachments/assets/71d9e507-7f39-4638-857d-c9206bb751bd)

Press on "Load Existing File" and choose config.m

![image](https://github.com/user-attachments/assets/877dd233-0967-48de-97d8-bf1a3e2d89a4)

Now you can manually change to your own configuration.

***pay attention to "/" if there is or not at the end of the path.

To remove a task stand on the task you wish to remove and press "Remove task".

To add a task enter the task name (as it appears in the AcquisitionInfo log) and press "Add task".
Then enter config name and press "Save confif File".

## Run
1. Double click on the Icon in Image 1.
2. "Load Existing File" and choose the correct config.m you created and press "Start".
3. You will be transfered to the data loading window:

   ![image](https://github.com/user-attachments/assets/c9256b5a-af04-46fa-901c-e255f3b8ae04)
4. Press "ECG Data Directory". If your configuration is set you will see the folder with all subjects, just continue with Select Folder immediatly, don't change anything (here you need to make sure that your data architecture is as described in "Preperation of Data ").

    ![image](https://github.com/user-attachments/assets/eeaa24f1-99a1-4be6-b57c-89b12ca3e800)
5. Now all subjects will be loaded into "Subject". Choose the Subject you want to visualize and tag. Choose the desired Task and Electrode (default is 1).
In case of several runs per task, the List Box will show all logs for that task.
**Sometimes there will be an AcquisitionInfo log but not the corresponding ECG1,ECG2,ECG3 and ECG4 logs, so make sure that you have those as well.
**All electrodes (channels) should work the same, only change the electrode number if for some reason the data looks noisy on the first channel. In this case, look for a better signal input for the rest of the channels

    ![image](https://github.com/user-attachments/assets/cccb5b8c-c6f3-45ea-adb4-3b075e862c0c)

    Choose a desired log file and press "Next".

 6. Let's tag away :) in the next window we can visualize the clean signal (if you don't see the signal just press >> and << and it will appear).

    ![image](https://github.com/user-attachments/assets/0590c48f-b1d8-45d5-8ac7-f6aa8d8f0bc9)

    The red circles are the tags of the R-peaks, the yellow * are a local maxima used as reference. To correctly tag a window use the "Remove Peaks" and "Add Peak" buttons. As appears in the image above not all red circles are in place , press "Remove Peaks", stand on each red circle you wish to remove (it will remove the closest one to the cross (+) that appears on the graph), now press "Add Peak" and put the cross (+) marker on the peak. This will add a red circle on the closest * local maxima. In case you identify a R-peak that is not marked with *, use the "Special Add" button to place the cross (+) exactly on the R-peak (in this case you have to be very precise). To move between time windows use the >> and << buttons.

    The red circles R-peaks use findpeaks matlab function: https://www.mathworks.com/help/wavelet/ug/r-wave-detection-in-the-ecg.html. At the beginning of each file loading 
    process, you can try and adjust all parameters of findpeaks function: "MinPeakHeight", "MinPeakProminence" and "MinPeakDistance".  * Only do this once per file before 
    tagging! Don't change every time window. Below is an example of a well tagged window:

    ![image](https://github.com/user-attachments/assets/c37cf388-a9cf-4da3-b0a9-40868b8f8c7f)
7. Press "Save Peaks" to save the newly tagged R-Peaks. This will create a subfolder of the task in the output directory path you entered in the configuration file. It is possible to exit a file and return to it to continue tagging. Every time you save for the same log file the old file will be saved in the old dir. Below is an example of the output directory, where the outputdir in config.m was "yaelcodes/Maayan/PhysioOutput/HR", when saving for the first time , the "MIST" directory automatically created.

    ![image](https://github.com/user-attachments/assets/6e63bac6-98b4-475d-b1db-1aabb4986a35)

8. Output: Each log file corresponds to a mat file where we have pkx and pky values, these values correspond to the signals R-peaks x and y. The pkx are the values of the time in seconds where R-peak occurred, which can easily evaluate the mean HR and HRV per task.

   ![image](https://github.com/user-attachments/assets/c7e44882-8720-4faa-a4d0-d01ea5dbe9dd)

9. Load new file: Use << button on the App upper left side to load a new file. This will redirect you to the loading window (3.)
     
    

