# SSM DRMGL Manual (English Version)

Subaru SSM2 compatible HUD / LAP / ACC / REC application.  
This document explains installation, connection, screen descriptions, logging, recording, and experimental protocols.

---

# 1. Installation and Preparation

## 1.1 Requirements
- Android 8.0 or later  
- USB-Serial capable device (FT232RL recommended)  
- SSM2 cable (requires 12V / GND input)  
- GPS (for LAP mode)

## 1.2 Installation
- Install APK or AAB on your Android device.  
- On first launch, allow the following permissions:
  - Photos & Videos: required to save recordings (MP4).  
  - Location: required for LAP mode (GPS-based lap timing).  
  - Storage: required to save logs (CSV).

## 1.3 Initial Setup
- Connect the SSM2 cable to the vehicle and to the Android device.  
- Provide 12V and GND to the cable as required.  
- Launch the app and press **Cnct** to start SSM2 initialization.  
- Once initialization succeeds, HUD values will start updating.  
- Adjust LAP / ACC settings as needed (weight, units, etc.).

---

# 2. Connection

## 2.1 SSM2 Connection
- Connect the USB-Serial adapter to the Android device.  
- Provide 12V / GND to the SSM2 cable.  
- Press **Cnct** in the app.  
- BF / A8 initialization will run; if successful, ECU data (PID) will be shown on the HUD.

## 2.2 If Connection Fails
- Check that 12V and GND are correctly wired to the cable.  
- Confirm that the USB-Serial adapter is recognized by the device.  
- Try turning ignition OFF → ON (IG-OFF → IG-ON).  
- Open the **Debug** screen and check initialization logs (BF / A8, TX/RX).

---

# 3. Screen Descriptions

## 3.1 Main Screen (HUD / Gauge)
- Displays main ECU PIDs in real time (RPM, coolant temperature, vehicle speed, etc.).  
- Min/Max values are tracked for some parameters.  
- **RST-HLD (short press)**: resets Min/Max values.  
- Recording overlay is shown when REC is active.  
- Gauge transparency and layout can be adjusted in **Settings**.

## 3.2 LAP Mode
- GPS-based lap timing mode.  
- LAP mode does not require SSM2; it works with GPS only.  
- **Start point registration**:
  - Long press on an area of the screen where there are no buttons.  
  - The current GPS position is stored as the lap start/finish line.  
- LAP start/stop:
  - When crossing the registered start point, lap timing begins.  
  - Each lap time is recorded and the best lap is kept.  

## 3.3 ACC Mode
- Acceleration measurement mode (e.g., 0–100 km/h).  
- Vehicle weight can be entered to estimate horsepower.  
- **Start command**:
  - Long press on an area of the screen where there are no buttons.  
  - Measurement starts when the vehicle begins to accelerate.  
- ACC mode requires **SSM2 speed PID**:
  - GPS speed is not used for ACC; only ECU speed is supported.

## 3.4 REC (Recording)
- Records HUD and overlays as MP4 video.  
- **Start recording**: short press **REC**.  
- **Stop recording**: short press **STOP**.  
- Resolution options: 480p / 720p / 1080p.  
- Overlays:
  - HUD PIDs (RPM, speed, etc.)  
  - LAP information (lap times, best lap)  
  - ACC information (acceleration results, estimated horsepower)

### Important Note (First Recording)
- On some devices, the **first recording after installation** may freeze.  
- This can happen while permissions and settings are being applied.  
- It is recommended to:
  - Install the app  
  - Grant all required permissions  
  - Adjust settings  
  - **Restart the app once**, and then start recording.

## 3.5 Debug (Communication Status)
- Shows initialization logs (BF / A8).  
- Displays raw TX / RX data.  
- Allows checking ECU responses.  
- Shows MultiRead cycle timing.  
- Displays ISO/KWP initialization logs (experimental only).

## 3.6 Settings
- Adjust gauge transparency.  
- Change gauge layout/position.  
- Configure LAP / ACC options.  
- Set recording resolution.  
- Open the in-app manual (Manual.md).

### Loopback Function (Experimental)
- By providing **12V + GND** to the cable, you can test the app without a vehicle.  
- When loopback is active and **Cnct** is pressed:
  - The app returns dummy ECU responses.  
  - TX/RX behavior and HUD updates can be tested.  

---

# 4. Logging and Recording

## 4.1 Logs (CSV)
- Logs contain:
  - PID values from MultiRead  
  - LAP results  
  - ACC results  
- **Logging interval**:
  - Logs are written every **1 second**.  
  - This interval is independent from the internal MultiRead cycle.  
- Logs are saved while SSM2 is connected.  
- LAP / ACC results are also stored.  
- Logs are saved in the app’s internal storage area.  
- On Android 13 and later, Photos & Videos permission is required for proper file access.

### Notes
- Logs are in CSV format.  
- Long SSM2 sessions will produce large log files.  
- If PID updates are unstable, logs will reflect that instability.

## 4.2 Recording (MP4)
- Records HUD and overlays as MP4 video.  
- **Start**: short press **REC**.  
- **Stop**: short press **STOP**.  
- Resolution: 480p / 720p / 1080p.  
- Overlays include PID, LAP, and ACC information.  
- Files are saved in the app’s internal storage.  
- On Android 13 and later, Photos & Videos permission is required.

### Notes
- Recording increases device load.  
- Some devices may experience frame drops.  
- Long recordings may cause device heating.  
- If SSM2 connection is unstable, overlays may appear intermittent.

### First Recording Warning
- After tool installation, the **first recording** may freeze mid-way.  
- It is recommended to:
  - Install the app  
  - Complete settings and permission approvals  
  - **Restart the app**  
  - Then start recording.

## 4.3 Relationship Between Logs and Recording
- **Logs (CSV)**:
  - Raw PID data  
  - LAP / ACC results  
  - Suitable for analytical use.  
- **Recording (MP4)**:
  - Visual HUD display  
  - Overlays for PID / LAP / ACC  
  - Suitable for visual review and sharing.  
- Logs and recording operate independently:
  - Logs continue even while recording is active.

---

# 5. Experimental Protocol (ISO/KWP)

## 5.1 Overview
- ISO/KWP support includes:
  - ISO9141 (5-baud initialization)  
  - KWP2000 (Fast initialization)  
- These are different from Subaru SSM2.  
- For safety, **there is no user-facing enable switch**.  
- When SSM2 is connected, ISO/KWP initialization may run internally,  
  but **no ECU exploration or PID retrieval is performed**.

## 5.2 ECU Responses and Caution
- Possible responding ECUs:
  - Engine ECU (depends on vehicle)  
  - Meter Unit  
  - **SRS (airbag) ECU may respond (important)**  
- On some Subaru vehicles, multiple ECUs share the K-Line.  
- During ISO/KWP initialization, SRS ECU may respond instead of Engine ECU.

## 5.3 Initialization and Logs
- ISO/KWP initialization flow:
  - Try ISO9141 (5-baud init).  
  - Try KWP2000 (Fast init).  
  - If any response is received, it is logged in the **Debug** screen.  
- Important:
  - Even if initialization succeeds, **no PID retrieval or ECU exploration is performed**.  
  - Only initialization logs are shown.

## 5.4 Behavior (Current Implementation)
- For safety, the implementation:
  - Tests only **Engine ECU–targeted address ranges**.  
  - Does **not** access unnecessary address regions.  
  - Does **not** perform ECU scanning or PID reading.  
  - User cannot enable or disable ISO/KWP; related code is commented out.

## 5.5 Limitations
- Some vehicles may not respond at all.  
- SRS ECU may respond, which can affect safety systems.  
- Stability is not guaranteed.  
- This feature is **not recommended for normal use**.

## 5.6 Safety Notes
- ISO/KWP is experimental and may affect safety-related ECUs.  
- **Do not use this feature while driving.**  
- If communication errors occur:
  - Turn off Cnct.  
  - Perform IG-OFF → IG-ON.  

## 5.7 Developer Incident (Important)
- In a past test environment, a **full-range initialization** (accessing all address regions) was performed.  
- This caused the **SRS (airbag) ECU to enter a failsafe state**.  
- Recovery required:
  - Disconnecting the battery negative terminal.  
  - Fully resetting the ECU.  
- This incident shows:
  - Accessing undefined or unintended address regions can cause other ECUs (like SRS) to react.  
  - SRS ECU may enter failsafe mode in response to unexpected initialization.  
- Current implementation:
  - Only Engine ECU–targeted address ranges are tested.  
  - Unnecessary address regions are not accessed.  
  - Exploration and PID retrieval are disabled to avoid similar issues.

---

# 6. Other Features

## 6.1 Overlay Display (HUD / LAP / ACC)
- During recording, HUD, LAP, and ACC information can be overlaid on the video.  
- Useful for reviewing runs and sharing on social media.  
- Overlays are only visible in recordings, not in logs.

## 6.2 In-App Manual (Manual.md)
- The manual (Manual.md) can be viewed inside the app.  
- Once installed, it can be read offline.  
- Contents include:
  - Installation  
  - Connection  
  - Screen descriptions  
  - Logging and recording  
  - Experimental protocols (ISO/KWP)

## 6.3 Storage Management
- Logs (CSV) and recordings (MP4) are stored in the app’s internal storage.  
- On Android 13 and later:
  - Photos & Videos permission is required.  
- Notes:
  - Long recordings produce large MP4 files.  
  - Long SSM2 sessions produce large CSV logs.  
  - If storage is low, recording may stop unexpectedly.

## 6.4 Device-Dependent Behavior
- Behavior may vary by device.  
- Recording:
  - Some devices may experience frame drops.  
  - First recording may freeze; restarting the app is recommended.  
- USB-Serial:
  - Stability may differ by device.  
  - FireHD and Xperia devices have shown relatively stable behavior in tests.

## 6.5 Troubleshooting (Quick)

### SSM2 Connection Fails
- Check 12V / GND wiring.  
- Confirm USB-Serial recognition.  
- Try IG-OFF → IG-ON.  
- Check Debug logs.

### LAP Does Not Start
- Confirm GPS permission is granted.  
- Ensure you are outdoors with GPS reception.  
- Confirm start point registration (long press on empty area).

### ACC Does Not Start
- Confirm SSM2 speed PID is being read.  
- Ensure the vehicle is stationary before starting.  
- Confirm start command (long press on empty area).

### Recording Freezes
- For first recording:
  - Complete settings and permissions.  
  - Restart the app.  
- Check storage space.  
- Check device temperature (overheating).

## 6.6 Version Information
- App name: SSM DRMGL  
- Supported OS: Android 8.0 or later  
- Update highlights:
  - HUD improvements  
  - LAP / ACC stability  
  - REC optimization  
  - ISO/KWP initialization adjustments (experimental)

---

# SSM DRMGL マニュアル（日本語版）

Subaru SSM2 対応 HUD / LAP / ACC / REC アプリです。  
本ドキュメントでは、インストール方法、接続方法、画面説明、ログ・録画、実験的プロトコルなどを説明します。

---

# 1. インストールと準備

## 1.1 必要環境
- Android 8.0 以降  
- USB-Serial 対応端末（FT232RL 推奨）  
- SSM2 ケーブル（12V / GND 入力必須）  
- GPS（LAP モード使用時）

## 1.2 インストール
- APK または AAB を端末へインストールします。  
- 初回起動時に以下の権限を許可してください：
  - 写真と動画：録画（MP4）の保存に必要  
  - 位置情報：LAP モード（GPS ラップ計測）に必要  
  - ストレージ：ログ（CSV）の保存に必要

## 1.3 初期設定
- SSM2 ケーブルを車両と端末に接続します。  
- ケーブルに 12V / GND を入力します。  
- アプリを起動し、**Cnct** を押して SSM2 初期化を開始します。  
- 初期化が成功すると HUD に ECU の値が表示され始めます。  
- 必要に応じて LAP / ACC の設定（車重、単位など）を調整します。

---

# 2. 接続方法

## 2.1 SSM2 接続
- USB-Serial を端末に接続します。  
- SSM2 ケーブルに 12V / GND を入力します。  
- アプリで **Cnct** を押します。  
- BF / A8 初期化が実行され、成功すると HUD に ECU データ（PID）が表示されます。

## 2.2 接続できない場合
- ケーブルの 12V / GND が正しく配線されているか確認します。  
- USB-Serial が端末に認識されているか確認します。  
- IG-OFF → IG-ON を試します。  
- **Debug** 画面で初期化ログ（BF / A8、TX/RX）を確認します。

---

# 3. アプリ画面の説明

## 3.1 メイン画面（HUD / Gauge）
- ECU の主要 PID（RPM、水温、車速など）をリアルタイム表示します。  
- 一部項目は Min/Max を保持します。  
- **RST-HLD（短押し）**：Min/Max をリセットします。  
- REC 中は録画オーバーレイが表示されます。  
- ゲージの透明度・配置は **Settings** で調整できます。

## 3.2 LAP モード
- GPS によるラップタイム計測モードです。  
- LAP モードは SSM2 接続なしでも、GPS のみで動作します。  

### スタート地点登録
- 画面上の **ボタンがない場所を長押し** すると、  
  現在の GPS 位置をラップのスタート／ゴール地点として登録します。

### LAP 計測
- 登録したスタート地点を通過するとラップ計測が開始されます。  
- 各ラップタイムが記録され、ベストラップが保持されます。

## 3.3 ACC モード
- 0–100 km/h などの加速計測モードです。  
- 車重を入力することで推定馬力を算出できます。  

### 計測開始指示
- 画面上の **ボタンがない場所を長押し** すると、  
  計測開始の指示が出され、車両が加速を始めると計測が開始されます。

### 必要条件
- ACC モードは **SSM2 の車速 PID** が必須です。  
- GPS 速度は使用せず、ECU の車速のみを利用します。

## 3.4 REC（録画）
- HUD とオーバーレイを MP4 動画として録画します。  

### 操作方法
- **録画開始**：REC ボタンを短押し  
- **録画停止**：STOP ボタンを短押し  

### 設定
- 解像度：480p / 720p / 1080p  
- オーバーレイ：
  - HUD の PID（RPM、車速など）  
  - LAP 情報（ラップタイム、ベストラップ）  
  - ACC 情報（加速結果、推定馬力）

### 初回録画時の注意
- ツールインストール直後の **初回録画** は、途中で固まるケースがあります。  
- 権限確認や設定反映のタイミングで録画処理が不安定になることがあります。  
- 推奨手順：
  - アプリをインストール  
  - 必要な権限と設定をすべて完了  
  - **一度アプリを再起動**  
  - その後に録画を開始する

## 3.5 Debug（通信状態確認）
- BF / A8 初期化ログを表示します。  
- TX / RX の生データを表示します。  
- ECU 応答の有無を確認できます。  
- MultiRead の周期を確認できます。  
- ISO/KWP 初期化ログ（実験的機能）を表示します。

## 3.6 Settings（設定）
- ゲージの透明度を調整します。  
- ゲージの配置・レイアウトを変更します。  
- LAP / ACC の設定を行います。  
- REC の解像度を設定します。  
- アプリ内マニュアル（Manual.md）を表示します。

### ループバック機能（実験的）
- ケーブルに **12V + GND** を入力することで、車両なしで動作確認ができます。  
- ループバック有効時に **Cnct** を押すと：
  - ECU 応答のダミーを返します。  
  - 送受信の挙動や HUD 更新を確認できます。

---

# 4. ログと録画

## 4.1 ログ（CSV）
- ログには以下が記録されます：
  - MultiRead で取得した PID 値  
  - LAP の結果  
  - ACC の結果  

### 記録周期
- ログの記録周期は **1 秒ごと** です。  
- この周期は内部の MultiRead 周期とは独立しており、  
  1 秒単位で CSV に書き出されます。

### 保存
- SSM2 接続中は自動的にログが保存されます。  
- LAP / ACC の結果もログに保存されます。  
- ログはアプリ専用の内部ストレージ領域に保存されます。  
- Android 13 以降では、写真と動画の権限が必要になる場合があります。

### 注意点
- ログは CSV 形式です。  
- 長時間接続するとファイルサイズが大きくなります。  
- PID の更新が不安定な場合、その状態がログにも反映されます。

## 4.2 録画（MP4）
- HUD とオーバーレイを MP4 動画として保存します。  

### 操作
- **録画開始**：REC ボタン短押し  
- **録画停止**：STOP ボタン短押し  

### 設定
- 解像度：480p / 720p / 1080p  
- オーバーレイ：PID / LAP / ACC 情報  
- 保存先：アプリ専用の内部ストレージ領域  
- Android 13 以降では、写真と動画の権限が必要です。

### 注意点
- 録画中は端末負荷が高くなります。  
- 一部端末ではフレームドロップが発生する場合があります。  
- 長時間録画では端末の発熱に注意してください。  
- SSM2 接続が不安定な場合、オーバーレイ表示が途切れることがあります。

### 初回録画時の注意（再掲）
- ツールインストール直後の初回録画は、途中で固まるケースがあります。  
- 設定と権限承認を済ませた後、**アプリ再起動後の録画**を推奨します。

## 4.3 ログと録画の関係
- **ログ（CSV）**：
  - PID の生データ  
  - LAP / ACC の結果  
  - 走行後の解析向け  

- **録画（MP4）**：
  - HUD の映像  
  - PID / LAP / ACC のオーバーレイ  
  - 視覚的な記録・共有向け  

- 両者は独立して動作し、録画中でもログは通常通り保存されます。

---

# 5. 実験的プロトコル（ISO/KWP）

## 5.1 概要
- ISO/KWP の対応内容：
  - ISO9141（5-baud init）  
  - KWP2000（Fast init）  
- Subaru SSM2 とは異なる通信方式です。  
- 安全のため、**ユーザーが ON/OFF できる設定項目は存在しません**。  
- SSM2 接続時に内部で初期化のみ実行されますが、  
  **ECU 探索や PID 取得は行いません**。

## 5.2 対応 ECU と注意点
- 応答する可能性のある ECU：
  - Engine ECU（車種による）  
  - Meter Unit  
  - **SRS（エアバッグ）ECU が応答する可能性あり（重要）**  

- 一部 Subaru 車種では、複数 ECU が K-Line を共有しています。  
- ISO/KWP 初期化時に、Engine ECU ではなく SRS ECU が応答する場合があります。

## 5.3 初期化方式とログ
- ISO/KWP 初期化の流れ：
  - ISO9141（5-baud init）を試行  
  - KWP2000（Fast init）を試行  
  - 応答があれば **Debug** 画面にログとして表示  

### 重要な仕様
- 初期化が成功しても、**PID 取得や ECU 探索は行いません**。  
- Debug 画面には「初期化ログのみ」が表示されます。

## 5.4 動作仕様（現在の実装）
- 安全性を確保するため、実装は以下のように制限されています：
  - **Engine ECU を想定したアドレス領域のみ初期化を試行**  
  - 不要なアドレス領域へのアクセスは行わない  
  - ECU 探索や PID 取得のコードはコメントアウトされており、実行されない  
  - ユーザーが ISO/KWP を有効化・無効化することはできません

## 5.5 制限事項
- 車種によっては初期化応答が全く返らない場合があります。  
- SRS ECU が応答し、安全装置に影響する可能性があります。  
- 安定性は保証されません。  
- 通常利用では **ISO/KWP の使用は推奨されません**。

## 5.6 安全上の注意
- ISO/KWP は実験的機能であり、安全系 ECU に影響を与える可能性があります。  
- **走行中の利用は絶対に避けてください。**  
- 通信エラーが発生した場合：
  - Cnct を解除  
  - IG-OFF → IG-ON を行う  

## 5.7 製作者による実例（重要）
- 過去の検証環境において、**全領域初期化処理（すべてのアドレス領域へのアクセス）** を試行した際、  
  **SRS（エアバッグ）ECU が誤反応し、フェイルセーフ状態に入った事例があります。**

- 復帰には：
  - バッテリーのマイナス端子を一度切断し、  
  - ECU を完全リセットする必要がありました。  

### この事例が示すこと
- 定義されていない、または想定外のアドレス領域への初期化アクセスは、  
  他の ECU（SRS など）が誤って応答する原因になります。  
- SRS ECU は安全装置のため、想定外の初期化に対してフェイルセーフ動作を行う場合があります。

### 現在の実装について
- 現在の SSM DRMGL の ISO/KWP 実装では：
  - **Engine ECU を想定したアドレス領域のみ初期化を試行**  
  - 不要なアドレス領域へのアクセスは行わない  
  - ECU 探索や PID 取得は行わない  
  - 同様の事象を避けるため、安全性を優先した設計になっています。

---

# 6. その他機能

## 6.1 オーバーレイ表示（HUD / LAP / ACC）
- REC 録画時に、HUD・LAP・ACC の情報を映像に重ねて表示できます。  
- 走行の振り返りや SNS への投稿に便利です。  
- オーバーレイは録画中のみ映像に反映され、ログには含まれません。

## 6.2 アプリ内ドキュメント（Manual）
- アプリ内で Manual.md を閲覧できます。  
- インストール後はオフラインでも閲覧可能です。  
- 主な内容：
  - インストール方法  
  - 接続方法  
  - 各画面の説明  
  - ログ・録画の使い方  
  - 実験的プロトコル（ISO/KWP）

## 6.3 ストレージ管理
- ログ（CSV）と録画（MP4）は、アプリ専用の内部ストレージ領域に保存されます。  
- Android 13 以降では：
  - 写真と動画の権限が必要です。  

### 注意点
- 長時間録画では MP4 ファイルが大きくなります。  
- 長時間の SSM2 接続では CSV ログが大きくなります。  
- ストレージ残量が不足すると、録画が途中で停止する場合があります。

## 6.4 端末依存の挙動
- 端末によって挙動が異なる場合があります。  

### 録画
- 一部端末では録画時にフレームドロップが発生することがあります。  
- 初回録画は固まる場合があるため、設定と権限承認後の **アプリ再起動** を推奨します。

### USB-Serial
- 端末によって USB-Serial の安定性が異なる場合があります。  
- FireHD や Xperia では比較的安定した動作が確認されています。

## 6.5 トラブルシューティング（簡易）

### SSM2 接続できない
- ケーブルの 12V / GND を確認  
- USB-Serial が認識されているか確認  
- IG-OFF → IG-ON を試す  
- Debug ログを確認

### LAP が開始しない
- GPS 権限が許可されているか確認  
- 屋外で GPS が取得できる状態か確認  
- スタート地点登録（ボタンがない場所の長押し）が行われているか確認

### ACC が開始しない
- SSM2 の車速 PID が取得できているか確認  
- 車両が停止状態であるか確認  
- 計測開始指示（ボタンがない場所の長押し）が行われているか確認

### 録画が固まる
- 初回録画の場合：
  - 設定と権限承認を完了  
  - アプリを再起動  
- ストレージ残量を確認  
- 端末の発熱状態を確認

## 6.6 バージョン情報
- アプリ名：SSM DRMGL  
- 対応 OS：Android 8.0 以降  
- 更新内容（概要）：
  - HUD 表示の改善  
  - LAP / ACC の安定化  
  - REC 録画の最適化  
  - ISO/KWP 初期化ログの調整（実験的）

---
