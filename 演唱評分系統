import librosa.display
import matplotlib.pyplot as plt
import numpy as np

#載入聲音檔
from google.colab import files
uploaded = files.upload()
uploaded = files.upload()
# 讀取聲音檔
path = 'P1.mp3'
path2 = 'P2.mp3'
# y：波形資料
# sr：取樣頻率（Hz）
y, sr = librosa.load(path, sr=44100, mono = True)
y2, sr2 = librosa.load(path2, sr=44100, mono = True)
# 繪製波形圖
plt.figure()
librosa.display.waveshow(y, sr=sr)
plt.title('origin')
plt.show()

librosa.display.waveshow(y2, sr = sr2)
plt.title('cover')
plt.show()

# 偵測節拍
tempo, beat_frames = librosa.beat.beat_track(y=y, sr=sr)
tempos, beat_frames2 = librosa.beat.beat_track(y=y2, sr=sr)
# 將 frames 轉為實際時間
times = librosa.frames_to_time(beat_frames, sr=sr)
times2 = librosa.frames_to_time(beat_frames2, sr=sr)

print('節拍長度陣列：',times)
print(times2)

wavescore = 50
timescore = 50
wavecount = []
timecount = []
#計算頻率差距
for i in range(len(y2)):
  if abs(y[i] - y2[i]) > 0.7:
    wavescore -= 1
    wavecount.append(i)
print(wavescore)
#計算節拍差距
for i in range(len(times)):
  if abs(times[i] - times2[i]) > 0.8:
    timecount.append(i)
    timescore -= 1
#計算總分
score = timescore + wavescore
#輸出分析結果
print('分析結果：\n音準分數：',wavescore,'\n節拍分數：',timescore,'\n總分：',score)
