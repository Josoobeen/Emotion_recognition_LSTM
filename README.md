# The guide for LSTM Emotion Recognition

## Datasets
The Dataset is from https://aihub.or.kr/

## Preprocessing
Korean Character Embedding is used for input data. I didn't use Higher or complax embedding for this modle simple.
1. Erase all character without Korean and space
2. Use Character Embedding (1 character in container)
\
output data is made 0 or 1.
0 is bad emotion.
1 is good emotion.
I use Sigmoid activation, output will appear between 0 and 1

## Model
This LSTM Model is made by Tensorflow and keras.
