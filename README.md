# Speech Emotion Classification

<br>
An example of the plots obtained in the data preprocessing and inspection stage. This picture shows the chromagram of a sound file which shows the intensity of different pitch classes in the sound file.
<p align="center">
<img width="1176" alt="Screenshot 2022-02-06 at 7 06 12 PM" src="https://user-images.githubusercontent.com/46462603/152713883-f94a976f-eca1-4b6a-aca1-e4a64d57b8df.png">
</p>

<br>
The accuracy and validation accuracy of the model when it is being trained for 1500 epochs.
<p align="center">
<img width="1168" alt="Screenshot 2022-02-06 at 7 18 05 PM" src="https://user-images.githubusercontent.com/46462603/152714698-1aab4c70-d29d-4e3a-a99c-b34b49c0f747.png">
</p>

<br>

## Goal
To create a model that can classify a given voice clip into 1 of the 8 categories based on the emotion it conveys: neutral, calm, happy, sad, angry, fearful, disgust, and surprised. 

## Dataset
The Ryerson Audio-Visual Database of Emotional Speech and Song (RAVDESS) dataset can be downloaded from <a href="https://www.kaggle.com/uwrfkaggler/ravdess-emotional-speech-audio" target="_blank">RAVDESS Emotional speech audio on Kaggle</a>. There are altogether 1440 sound files from 24 professional actors (12 female, 12 male), vocalizing two lexically-matched statements in a neutral North American accent.

Each of the 1440 files has a unique file name. The filename consists of a 7-part numerical identifier (e.g., 03-01-06-01-02-01-12.wav). 
File name identifiers:

- Modality (01 = full-AV, 02 = video-only, 03 = audio-only).
- Vocal channel (01 = speech, 02 = song).
- Emotion (01 = neutral, 02 = calm, 03 = happy, 04 = sad, 05 = angry, 06 = fearful, 07 = disgust, 08 = surprised).
- Emotional intensity (01 = normal, 02 = strong). NOTE: There is no strong intensity for the 'neutral' emotion.
- Statement (01 = "Kids are talking by the door", 02 = "Dogs are sitting by the door").
- Repetition (01 = 1st repetition, 02 = 2nd repetition).
- Actor (01 to 24. Odd numbered actors are male, even numbered actors are female).

In this project, only the "Emotion" part of the file name will be considered. The features in this project will be the vectors representing the mel features, chroma features, mfcc features, and zero crossing counts of the sound files. The targets are the numbers representing the emotions of the sound files.

## Code, files, or folders needed to run the program
- <a href="https://github.com/ZhengEnThan/Speech-Emotion-Classification/blob/main/Speech_Emotion_Recognition_using_ANN.ipynb" target="_blank">Speech_Emotion_Recognition_using_ANN.ipynb</a>
- The RAVDESS sound files that can be downloaded from <a href="https://www.kaggle.com/uwrfkaggler/ravdess-emotional-speech-audio" target="_blank">RAVDESS Emotional speech audio on Kaggle</a>. 

## How to use the program
If you are running the program and storing the files locally, you would not have to connect to Google Drive like I did. Edit the code cells below the markdown "Getting the sound files" to grab the sound files from wherever you placed them. 

## References
- RAVDESS dataset <br>
Livingstone SR, Russo FA (2018) The Ryerson Audio-Visual Database of Emotional Speech and Song (RAVDESS): A dynamic, multimodal set of facial and vocal expressions in North American English. PLoS ONE 13(5): e0196391. https://doi.org/10.1371/journal.pone.0196391.
