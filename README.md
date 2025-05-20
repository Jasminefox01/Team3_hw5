# 🧠 Fall Detection System using MediaPipe & Random Forest

本專案實作一個使用姿態關鍵點與機器學習模型（Random Forest）的跌倒偵測系統，並部署於 Raspberry Pi 上可即時運作。

---

## 📌 專案目標

- 使用 [MediaPipe Pose](https://google.github.io/mediapipe/solutions/pose) 擷取人體骨架關鍵點
- 利用標註資料訓練機器學習模型（SVM / Random Forest）以判斷是否跌倒
- 將模型部署至 Raspberry Pi，實現即時偵測與視覺警示輸出

---

## 🧩 專案架構

HW5_FALL_DETECTION/
├── RandomForest/
│ ├── fall_detect_rf.py # 模型訓練程式（使用 Random Forest）
│ ├── pose_train_data.csv # 已標註的關鍵點訓練資料
│ ├── rf_fall_model.pkl # 訓練完成的模型檔
│ └── rf_scaler.pkl # 特徵標準化模型
├── Pi4/
│ └── camera_stream_rf.py # Raspberry Pi 部署用 Flask 串流偵測系統

---

## 🧪 PC上進行模型訓練與測試

### ✨ Step 1. 安裝必要套件
pip install pandas scikit-learn joblib

### ✨ Step 2. 執行訓練
cd RandomForest
python fall_detect_rf.py

訓練完成後會輸出：

模型指標（Accuracy / Recall / F1-score）

模型檔案：rf_fall_model.pkl

標準化器：rf_scaler.pkl

pkl

🎥 Raspberry Pi 部署與即時偵測
📦 安裝必要套件
pip install opencv-python mediapipe flask joblib

🚀 執行 Flask 偵測伺服器
cd Pi4
python camera_stream_rf.py
打開瀏覽器並進入 http://<raspberry_pi_ip>:5000/ 即可看到即時跌倒偵測畫面。


