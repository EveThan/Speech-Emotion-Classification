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
If you are running the program and storing the files locally, you would not have to connect to Google Drive like I did. Edit the code cells under the markdown "Getting the sound files" to grab the sound files from wherever you placed them. 

Simply run the next code cells in order to visualize the different features of a sound file. If you would like to change the sound file that you want to inspect, edit the code cell below the markdown "Analyzing one sound file".

```python
# Take one of the sound file and analyze it
#voice_file = files[200]
voice_file = '03-02-06-01-01-02-16.wav'

voice_file
```

For example, "files[200]" is replaced with '03-02-06-01-01-02-16.wav' here. 

Run the rest of the code cells in order to split the dataset into training and test sets, train a neural network on our training set, and evaluate the model on the test set. 

## What I have learned
- Used glob to return all file paths that match a specific pattern.
- Used librosa to extract the different features of a given sound file such as its mel features and chroma features.
- Used tensorflow.keras to create a dense neural network with batch normalization and dropout to recognize emotions in the sound files.
- Used sklearn to evaluate the performance of the model by using the classification_report and confusion_matrix functions.

## Main libraries or modules used
- pandas
- numpy
- glob
- collections
- librosa
- soundfile
- Ipython.display
- matplotlib
- sklearn
- tensorflow.keras

## Approaches
librosa.feature is mainly used to extract the different features of a given sound file. In this project, the mel features, chroma features, mfcc features, and number zero crossings are recorded for each sound file to be used as features for the machine learning model. 
- The mel spectrogram is a spectrogram that is converted to a Mel scale. The Mel scale mimics how the human ear works, with research showing humans don’t perceive frequencies on a linear scale.
- The chroma features keep track of the intensity of different pitch classes in the spectrum. In order to produce a chromagram, the data of the sound file needs to first be converted from time-amplitude to the time-frequency domain. 
- The mfcc features or the mel frequency cepstral coefficients (MFCCs) of a signal are said to be able to concisely describe the overall shape of a spectrum.
- The zero crossing rate is the rate at which the signal changes from positive to negative or back. This feature has been used heavily in both speech recognition and music information retrieval. It usually has higher values for highly percussive sounds like those in metal and rock.

The files are split into training and test sets where 80% of them belong to the training set and the rest belong to the test set. A 7-layer dense neural network is created and trained on the training set. The last layers uses the Softmax activation function so that probabilities can be produced for each emotion and the one with the highest probability will be the emotion predicted for a given sound file. After training the model with 1500 epochs, the model is has a validation accuracy of around 60% and test accuracy of 57%.

## Comments
There are other features that can be included such as spectral centroid and spectral rolloff. However, when I included these additional features in the program, the resulting accuracy or F1 score is lower. It might be because when more features are considered, more variations are introduced into the dataset that make it harder for the model to observe a pattern and predict well. More neural network layers or different combinations of the sound features can be used to see which neural network architecture and feature combinations can result in a model that performs better.

## References
- RAVDESS dataset <br>
Livingstone SR, Russo FA (2018) The Ryerson Audio-Visual Database of Emotional Speech and Song (RAVDESS): A dynamic, multimodal set of facial and vocal expressions in North American English. PLoS ONE 13(5): e0196391. https://doi.org/10.1371/journal.pone.0196391.
- Music Feature Extraction in Python <br>
https://towardsdatascience.com/extract-features-of-music-75a3f9bc265d
- How to Detect COVID-19 Cough From Mel Spectrogram Using Convolutional Neural Network <br>
https://www.analyticsvidhya.com/blog/2021/06/how-to-detect-covid19-cough-from-mel-spectrogram-using-convolutional-neural-network/
- librosa
https://librosa.org/doc/latest/index.html

~ Project created in August 2021 ~
