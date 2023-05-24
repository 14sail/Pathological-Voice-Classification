# 多模態病理嗓音分類
AI CUP 2023 春季賽TEAM_3071

## 開發環境
* Pyhton version: 3.7.5
* tensorflow: 2.4.4
* Keras: 2.4.3
* Keras-Applications: 1.0.8
* scikit-learn: 0.22.1
* audioflux: 0.1.6
* focal-loss: 0.0.7

## 模型架構
<img width="424" alt="image" src="https://github.com/14sail/Pathological-Voice-Classification/assets/112383122/f30c4827-a69b-40df-b1fc-af686de3e516">

### 多尺度SincNet模型
<img width="410" alt="image" src="https://github.com/14sail/Pathological-Voice-Classification/assets/112383122/df19b8da-affc-461c-b772-4540a37e16da">

### Mel頻譜圖與MFCC圖轉換
<img width="326" alt="image" src="https://github.com/14sail/Pathological-Voice-Classification/assets/112383122/b305db18-a796-4302-bcd2-18cb6466e513">

## 程式碼
1.：資料處理

2.：sincnet模型建立

3.：Mel頻譜的EfficientNet-B0

4.：MFCC的EfficientNet-B4

5.：機器學習演算法

6.：集成學習
