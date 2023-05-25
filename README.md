# 多模態病理嗓音分類
AI CUP 2023 春季賽TEAM_3071

## 開發環境
* Pyhton version: 3.7.5
* tensorflow: 2.4.4
* Keras: 2.4.3
* Keras-Applications: 1.0.8
* scikit-learn: 0.22.1
* audioflux: 0.1.6
* librosa 0.8.0
* focal-loss: 0.0.7

## 模型架構
<img width="500" alt="image" src="https://github.com/14sail/Pathological-Voice-Classification/assets/112383122/f30c4827-a69b-40df-b1fc-af686de3e516">

### 多尺度SincNet模型
<img width="500" alt="image" src="https://github.com/14sail/Pathological-Voice-Classification/assets/112383122/df19b8da-affc-461c-b772-4540a37e16da">

### Mel頻譜圖與MFCC圖轉換的EfficientNet
<img width="500" alt="image" src="https://github.com/14sail/Pathological-Voice-Classification/assets/112383122/b305db18-a796-4302-bcd2-18cb6466e513">

## 程式碼
1.[**data preprocessing.ipynb**](https://github.com/14sail/Pathological-Voice-Classification/blob/main/data%20preprocessing.ipynb)：資料處理
  * 本檔案將對資料進行前處理，可分為5個部份：
  > audio : 將音訊載入，並將其填充0（padding）到相同長度（3秒）
  
  > clinical : 病史資料的篩選與處理
  
  > MelSpectrogram : 將處理完的音訊進行梅爾頻譜（Mel-spectrogram）的轉換
  
  > MFCC : 將處理完的音訊進行梅爾頻率倒譜係數（Mel-Frequency Cepstral Coefficients）的轉換
  
  > label : 目標類別
  * 下方為Training Dataset的資料處理，Public Dataset 與 Private Dataset使用相同的資料處理，因此將不冗述

2.**sincnet.ipynb**：sincnet模型建立
  * 本檔案使用資料處理後的音訊資料語病史進行訓練與預測
  * 訓練結果的模型權重將存為「sincnet.h5'」

3.**mels(EfficientNetB4).ipynb**：Mel頻譜的EfficientNet-B0
  * 本檔案使用資料處理後的Mel頻譜圖進行訓練與預測
  * 為了滿足預訓練模型所需，在進入模型之前先將影像疊為三通道
  * 訓練結果的模型權重將存為「mels.h5'」
  
4.**mfcc(EfficientNetB0).ipynb**：MFCC的EfficientNet-B4
  * 本檔案使用資料處理後的MFCC圖進行訓練與預測
  * 為了滿足預訓練模型所需，在進入模型之前先將影像疊為三通道
  * 訓練結果的模型權重將存為「mfcc.h5'」

5.**ML and ensemble.ipynb**：機器學習演算法與集成學習
  * 本檔案使用資料處理後的病史資料，使用機器學習演算法進行進行訓練與預測
  > 使用訓練好的三個模型（存好的三個權重'sincnet.h5','mfcc.h5','mels.h5')與三個機器學習演算法（SVM,ExtraTree,XGB）進行集成
