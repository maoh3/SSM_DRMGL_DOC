# 🎥 SSM DRMGL – HUD Demo  
(English + Japanese)
[日本語セクションはこちら](#日本語)


---

## **English Version**

This page provides early demo videos of the SSM DRMGL HUD system.  
At the moment, full driving data from the GDB is not yet available, so two temporary videos are provided:

---

### **1. GDB Tachometer Test (Parking Lot – Stationary)**  
This video shows the HUD reading and displaying tachometer data while the GDB remains stationary in a parking lot.  
The accelerator is lightly pressed to confirm that the RPM values are correctly captured and rendered in real time.

- Real‑time RPM updates  
- Camera2 + GLRenderer overlay  
- Basic ECU data verification  
- Practical behavior check on the actual vehicle (without moving)

**Demo Video:**  
<img width="568" height="320" alt="ezgif-75166a57f197100c" src="https://github.com/user-attachments/assets/cc1ee8b9-d188-42ea-b552-201750919a98" />


---

### **2. In‑Car Driving Test (Subaru R2 – Non‑Monitored Vehicle)**  
This video was recorded during a driving test using a Subaru R2 (EN07).  
Because this vehicle does not provide readable ECU data through the current protocol implementation,  
the HUD meters do not move.  
The camera mount was unstable, causing visible shaking,  
but the HUD rendering itself was smooth and stable throughout the drive.

- HUD stability during motion  
- Smooth GLRenderer behavior despite camera shaking  
- Layout and visibility check  
- Real‑world in‑car environment test  
- R2 (EN07) used as a non‑monitorable test vehicle

**Demo Video:**  
<img width="800" height="450" alt="r2_run" src="https://github.com/user-attachments/assets/532de418-d7b3-4c32-9095-a987cc5c142b" />


---

### **Future Plan**  
A final combined demo will be released later:  
**real driving footage + fully working tachometer / speed / G‑ball data from the GDB.**

This will represent the complete HUD experience with all sensors and overlays functioning together.

---

---
## 日本語

## **日本語版**

このページでは、SSM DRMGL HUD の動作を確認できるデモ動画を掲載しています。  
現在、GDB の本走行データがまだ取得できていないため、  
**暫定的に 2 種類の動画を公開しています。**

---

### **1. GDB（駐車場・停車状態）でのタコメータ動作テスト**  
GDB を駐車場に停車したまま、アクセルを軽くあおって  
HUD がタコメータの回転数を正しく取得・描画できているかを確認した動画です。  
車両自体は動かしていません。

- 回転数のリアルタイム描画  
- Camera2 + GLRenderer による HUD オーバーレイ  
- ECU データの基本動作確認  
- 実車での HUD 動作チェック（停車状態）

---

### **2. 車載テスト（Subaru R2 – ECUモニタ不可車両）での走行動画**  
こちらは、HUD を **Subaru R2（EN07）** に車載して実際に走行した際の動画です。  
この車両では現状のプロトコル実装では ECU データを取得できなかったため、  
**メーターは動いていません。**

また、使用したスタンドが貧弱だったため映像は揺れていますが、  
**HUD の描画自体は滑らかで安定していることを確認できました。**

- 走行中の HUD の揺れ・視認性  
- カメラ揺れとは別に HUD 描画は滑らか  
- GLRenderer の描画安定性  
- R2（EN07）を用いた車載環境テスト  
- ECU モニタ不可車両での動作チェック

---

### **今後の予定（最終版デモ）**  
最終的には、

**「GDB のメーターが動く動画」＋「走行中の HUD 動作動画」  
この2つを融合した “本走行デモ動画” を公開予定です。**

HUD の実用性を示す完全版デモとして仕上げる予定です。

---

