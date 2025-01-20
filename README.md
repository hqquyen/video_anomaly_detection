# Video-based Anomaly Detection

This repo aims to detect the anomaly events from the video.

## 1. Install the enviroment
### Install Anaconda
```
conda create --name anomaly python==3.8.0
conda activate anomaly
```
### Install All Packages
```
pip install -r requirements.txt
```

### Feature Extractor Pretrained

Use the feature extractor pretrained to extract features for training. It can be found here:
https://drive.google.com/file/d/1cMvEPmbbBKxZumuuddG9fYphXutMUeXv/view?usp=sharing

## 2. Dataset
Construct your dataset as follow:
```
datasets
└── videos
    └── events
        ├── anomaly_event
        │   ├── anomaly_event_01.mp4
        │   ├── anomaly_event_02.mp4
        │   └── ...
        └── normal_event
            ├── normal_event_01.mp4
            ├── normal_event_02.mp4
            └── ...
```
NOTE: The name of the normal video have to contain the "normal" word

## 3. Execution
### Features Extraction
```python feature_extractor.py --dataset_path "path-to-video-folder" --model_type "feature-extractor" --pretrained_3d "path-to-feature-extractor-pretrained"```

Arguments:
* dataset_path - path to the directory containing videos to extract features
* model_type - which type of model to use for feature extraction
* pretrained_3d - path to the pretrained to use for feature extraction



### Training
```python train.py --features_path "path-to-dataset-features" --annotation_path "path-to-train-dataset-annotation"```

Arguments:
* features_path - path to the directory containing the extracted features
* annotation_path - path to the training annotations file



## 4. Demo

### Video Demo

```python video_demo.py --feature_extractor "path-to-feature-extractor-pretrained" --feature_method "feature-extractor-method" --ad_model "path-to-model-weights" --n_segments "number-of-segments"```

Arguments:
* feature_extractor - path to the pretrained to use for feature extraction
* feature_method - which type of model to use for feature extraction
* ad_model - path to the trained anomaly detection model
* n_segments - the number of segments to chunk the video to


The GUI lets you load a video and run the Anomaly Detection code (including feature extraction) and output a video with a graph of the Anomaly Detection prediction below.
