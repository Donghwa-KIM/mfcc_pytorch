# MFCC in Pytorch


```
MFCC(
  (amplitude_to_DB): AmplitudeToDB() # db scale: input에 로그정규화를 해주면 spectrogram이 더 잘 보임
  (MelSpectrogram): MelSpectrogram(
    (spectrogram): Spectrogram()
    (mel_scale): MelScale()
  )
)
```

- Parameter
  - `sample_rate`=16000
  - `n_mfcc`= 40
  - `log_mels`=False
    - log scale을 spectrogram 전에 사용하기 때문에 사용하지 않음
  - `n_fft`: 1024 (window_size)
  - `stride`: 512

- Dataset
  - frame_length = -(-audio_length // stride)
    - audio_length = 107743
    - stride = 512
    - -(-107743// 512) = 211
  - 107743(오디오길이)/16000(샘플링 레이트) = 6.733초
  - 1024(frame_length)/16000 = 0.064초
  - 전체데이터에 대한 frame length의 histogram

![seq_hist](/figure/seq_hist.png)



## Requirements
```
pip install torchaudio
```
