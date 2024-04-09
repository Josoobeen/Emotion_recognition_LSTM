# The guide for LSTM Emotion Recognition

## Datasets
The Dataset is from https://aihub.or.kr/

## Preprocessing
Korean Character Embedding is used for input data. I didn't use Higher or complax embedding for this modle simple.
1. Erase all character without Korean and space
2. Use Character Embedding (1 character in container)
\
output data is made 0, 1, 2.
0 is bad emotion.
1 is neutrality emotion
2 is good emotion.
I use Softmax Activation.

## Model
This LSTM Model is made by Tensorflow and keras.





## 한국어 설명
간단한 AI 모델에서 Binary 한 결과 값을 가지는 모델로 텍스트 데이터의 감정 정보를 부정적인지, 긍정적인지 인식할 수 있는 모델이 있습니다. AI 모델에서 가장 기초 모델 중 시계열 정보를 학습할 수 있는 LSTM 모델로 알아봅시다.

감정 인식을 위한 데이터는 https://aihub.or.kr/ 에서 가져왔습니다. 해당 사이트에서 감정 분석 데이터를 다운받아 훈련시키면 됩니다.

# 데이터 전처리 Data Preprocessing
주석(#)을 제거한 뒤 실행하면 설치된 자동으로 압축이 풀립니다.
압축이 풀린 뒤에는 압축 파일을 제거하고 다음 코드를 실행합니다.

다음 코드에서는 압축 해제된 파일의 주소값을 가져옵니다.
약 2300개가 되니, 손으로 일일이 불러올 수 없어요.

텍스트는 한글 외 모든 글자를 지우고, 긍정, 중립, 부정 데이터를 3개의 container에 있는 softmax 값으로 도출합니다.

# Vocaburary 형성
단어 책을 만들며, 숫자 index와 단어 character를 하나씩 배정합니다.
char2idx 는 단어를 숫자로 바꿀 때 사용되고, idx2char는 숫자를 단어로 바꿀 때 사용합니다.

복잡한 형태로 만들긴 했지만, 내용은 input으로 들어갈 데이터의 길이를 똑같이 맞춰주며, 데이터 사용이 편리하도록 numpy 배열로 바꿔줍니다.


# LSTM AI 모델
모델은 input 데이터의 크기를 가진 입력과, 각 숫자로 배정된 값을 특정 값을 가지도록 Embedding 합니다.
3개의 LSTM 레이어를 거쳐, 시계열 정보와 학습을 합니다.
마지막 Dense 레이어에서 도출된 값을 토대로 3개의 container에서 확률을 계산합니다.
softmax 함수는 정답 값을 제외한 나머지 loss는 모두 0이 되고, 1일 값에서는 log(y)의 loss로 계산됩니다.

즉, y=1일때 loss는 0 y=0일때 loss는 -∞이 됩니다.


# 모델 학습
학습을 진행합니다.
노트북으로 학습한거라 속도는 느렸지만 GPU가 달린 데스크탑을 사용한다면 1스텝에 1초 이하로 소요됩니다.
loss는 0.3까지 떨어졌지만 제 서버컴퓨터로 진행했을 때 loss : 0.02까지 1분도 걸리지 않았습니다.


# 결과 도출
사진 설명을 입력하세요.
원하는 text를 test_input에 넣고 실행하면, 확률에 따른 결과 값이 도출됩니다.
다만, character Embedding이기에 부족할 수 있으며, 필요하다면 단어 단위로 Embedding을 한 후 사용할 수 있습니다.
