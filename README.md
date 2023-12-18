# Gender-recognition-by-Voice
This repository is about building a deep learning model using TensorFlow 2 to recognize gender of a given speaker's audio. Read this tutorial for more information.

Requirements
TensorFlow 2.x.x
Scikit-learn
Numpy
Pandas
PyAudio
Librosa


Installing the required libraries:

pip3 install -r requirements.txt

# Dataset used 
Mozilla's Common Voice(https://www.kaggle.com/datasets/mozillaorg/common-voice) large dataset is used here, and some preprocessing has been performed:

Filtered out invalid samples.
Filtered only the samples that are labeled in genre field.
Balanced the dataset so that number of female samples are equal to male.
Used Mel Spectrogram feature extraction technique to get a vector of a fixed length from each voice sample, the data folder contain only the features and not the actual mp3 samples (the dataset is too large, about 13GB).
If you wish to download the dataset and extract the features files (.npy files) on your own, preparation.py is the responsible script for that, once you unzip it, put preparation.py in the root directory of the dataset and run it.

This will take sometime to extract features from the audio files and generate new .csv files.

Training
You can customize your model in utils.py file under the create_model() function and then run:

python train.py
Testing
test.py is the code responsible for testing your audio files or your voice:

python test.py --help
Output:

usage: test.py [-h] [-f FILE]

Gender recognition script, this will load the model you trained, and perform
inference on a sample you provide (either using your voice or a file)

optional arguments:
-h, --help            show this help message and exit
-f FILE, --file FILE  The path to the file, preferred to be in WAV format
For instance, to get gender of the file test-samples/27-124992-0002.wav, you can:

python test.py --file "test-samples/27-124992-0002.wav"


Output:

Result: male
Probabilities:     Male: 96.36%    Female: 3.64%
There are some audio samples in test-samples folder for you to test with, it is grabbed from LibriSpeech dataset.

To make inference on your voice instead, you need to:

python test.py
Wait until you see "Please speak" prompt and start talking, it will stop recording as long as you stop talking.

About
Building a Deep learning model that predicts the gender of a speaker using TensorFlow 2



