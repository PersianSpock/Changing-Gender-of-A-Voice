# Changing-Gender-of-A-Voice
Entrance Project For Dadepardaz Afagh
The project consists of 4 parts:
1. Dataset prepration 
2. Gender Detection
3. S2T using wav2vec
4. T2S using pyttsx3

Dataset used:

Mozilla's Common Voice large dataset is used here, and some preprocessing has been performed:

Filtered out invalid samples.
Filtered only the samples that are labeled in genre field.
Balanced the dataset so that number of female samples are equal to male.
Used Mel Spectrogram feature extraction technique to get a vector of a fixed length from each voice sample, the data folder contain only the features and not the actual mp3 samples (the dataset is too large, about 13GB).
If you wish to download the dataset and extract the features files (.npy files) on your own, preparation.py is the responsible script for that, once you unzip it, put preparation.py in the root directory of the dataset and run it.

This will take sometime to extract features from the audio files and generate new .csv files.

Training For Gender Detection:

You can customize your model in utils.py file under the create_model() function and then run:

python gd_train.py

Testing:

gd_test.py is the code responsible for testing your audio files or your voice:

python test.py --help
Output:

usage: gd_test.py [-h] [-f FILE]

Gender recognition script, this will load the model you trained, and perform
inference on a sample you provide (either using your voice or a file)

optional arguments:
-h, --help            show this help message and exit
-f FILE, --file FILE  The path to the file, preferred to be in WAV format
For instance, to get gender of the file test-samples/27-124992-0002.wav, you can:

python gd_test.py --file "test-samples/27-124992-0002.wav"
Output:

Result: male
Probabilities:     Male: 96.36%    Female: 3.64%
There are some audio samples in test-samples folder for you to test with, it is grabbed from LibriSpeech dataset.

To make inference on your voice instead, you need to:

python gd_test.py
Wait until you see "Please speak" prompt and start talking, it will stop recording as long as you stop talking.
