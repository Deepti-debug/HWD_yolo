# handwash_detection
Given a video of handwash, train a model to detect the different hand wash steps involved and output the following:
  • display time spent on each activity (hand wash step), and overall time spent in washing hands. 
  • If overall time spent less than 20 sec, it is non-compliance.
  • If some steps skipped or some steps not done, it is non-compliance.
  • Display the final compliance or non compliance.

Project Aim - To ensure that hand wash is performed in hospitals, homes and in office premises according to WHO norms.
-------------------------------------------------------------------------------------------------------------

Here is the Kaggle dataset which contains many such hand wash videos:
https://www.kaggle.com/realtimear/hand-wash-dataset


Please take a look at the colab notebook in the attachment at the end of this readme file.

The jupyter notebook contains:

The model recognises the missing step and saves these 3 information in the text file:

    • a model trained on YOLOv5 algorithm to detect 7 different hand wash steps.
  
    • For testing the model performance, a new video with only 6 steps (intentionally) is used
    • The model recognises the missing step and outputs these 3 information:
      • The video duration.
      • Which step is missing.
      • Whether it is non-compliance or compliance with the hand wash norms.
  
Dataset Format - 
-----------------------
• To train the model, the dataset is annotated in YOLO format. Have a look at the dataset directory structure in HandWashDataset_yoloFormat.
• 101 frames of 7 classes are annotated
• 81 X 7 frames are used in training set (HandWashDataset_yoloFormat/TrainingData/images/train)
• 20 X 7 frames are used in validation set (HandWashDataset_yoloFormat/TrainingData/images/val)
• Test videos are stored in HandWashDataset_yoloFormat/TestingData


Colab Notebook:
[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1-LVe0ewmRyOwZN8Kr20DDEjDhK73gpLp?authuser=1)
