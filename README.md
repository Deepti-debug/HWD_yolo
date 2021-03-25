# handwash_detection
Given a video of handwash, this model detects the 7 different hand wash steps involved in the video and output the following:

    • Display time spent on each activity (hand wash step), and overall time spent in washing hands. 
    • If overall time spent less than 20 sec, it is non-compliance.
    • If some steps skipped or some steps not done, it is non-compliance.
    • Display the final compliance or non compliance.
    

Project Aim - To ensure that hand wash is performed in hospitals, homes and in office premises according to WHO norms.
-------------------------------------------------------------------------------------------------------------

The model recognises the missing step and saves these 3 information in the text file:
    
    • a model trained on YOLOv5 algorithm to detect 7 different hand wash steps.
    • For testing the model performance, a new video with only 6 steps (intentionally) is used.
    • The model recognises the missing step and outputs these 3 information:
      • The video duration.
      • Which step is missing.
      • Whether it is non-compliance or compliance with the hand wash norms.
  
  
Dataset Information - 
---------------------

Here is the Kaggle dataset which contains hand wash videos for 7 hand wash steps:
https://www.kaggle.com/realtimear/hand-wash-dataset 

• To train the model, the dataset is annotated in YOLO format. <br/>
• Have a look at the dataset directory structure in HandWashDataset_yoloFormat.
    
    • For each step, the video is first converted into frames.
    • 101 frames of 7 classes are annotated.
    • 81 X 7 frames are used in training set (HandWashDataset_yoloFormat/TrainingData/images/train).
    • 20 X 7 frames are used in validation set (HandWashDataset_yoloFormat/TrainingData/images/val).
    • Test videos are stored in HandWashDataset_yoloFormat/TestingData.
    

Setting up YOLOv5 - 
-------------------

    • The model has been trained using YOLOv5. The dependencies to install YOLOv5 can be found in https://github.com/ultralytics/yolov5.
    • Our model has been trained on PyTorch framework.
    

Training - 
----------

    • The image input size is (640,640,3).
    • The model is trained for 100 epoch with a batch size of 16.
    • The trained model gives validation mAP (mean Average Precision), precision and recall of 0.996, 0.993, 1, respectively.
    
    | Steps  | Images | Labels | P     | R | mAP    |
    |--------|--------|--------|-------|----|-------|
    | All    | 140    | 140    | 0.993 | 1  | 0.996 |
    | Step1  | 140    | 20     | 0.99  | 1  | 0.995 |
    | Step2  | 140    | 20     | 0.99  | 1  | 0.996 |
    | Step3  | 140    | 20     | 1     | 1  | 0.996 |
    | Step4  | 140    | 20     | 0.997 | 1  | 0.995 |
    | Step5  | 140    | 20     | 0.991 | 1  | 0.996 |
    | Step6  | 140    | 20     | 0.99  | 1  | 0.996 |    
    | Step7  | 140    | 20     | 0.994 | 1  | 0.996 |
    
    • Results are plotted as follows:
    ![alt text](http://url/to/results.png)
    
    
Please take a look at the following colab notebook.
It consists of preprocessing of images, model training and model prediction output.

Colab Notebook:
[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1-LVe0ewmRyOwZN8Kr20DDEjDhK73gpLp?authuser=1)
