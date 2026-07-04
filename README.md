# SSM DRMGL

SSM DRMGL is an Android dashboard and logger application for Subaru vehicles using the **SSM2 protocol**.  
It provides real‑time ECU monitoring, data logging, gauge display, and video recording with overlay.

**Current Status (2026/06):**
- **SSM2 (4800 bps)** → Fully supported & confirmed working
- **SSM1 / ISO9141‑2 / KWP2000** → Experimental, disabled by default
- **Meter Unit (K‑Line)** → Under investigation, not enabled

SSM : Subaru Select Monitor  
D : Drive  
R : Record  
M : Monitor  
G : Gauge  
L : Logger

---

## Features

- Real‑time ECU monitoring (**SSM2**)
- Multi‑PID data logging (CSV)
- Gauge & dashboard UI
- Video recording with data overlay
- USB‑OTG communication
- Markdown‑based in‑app documentation

---

## Additional Features

### Lap Timer (LAP Mode)
A lightweight lap‑timing system inspired by classic Subaru diagnostic tools.

- Long‑press near the start/finish line to register the start point
- Each pass records a new lap time
- Best lap time is stored and displayed

### ACC Measurement (0–100 km/h)
A performance measurement tool **unique to SSM DRMGL**.

- Measures time & distance to reach a target speed
- Target speed configurable
- Vehicle weight input
- Calculates estimated horsepower
- Best ACC result displayed

### Gear Position Indicator
Displays current gear based on RPM & speed.

### Recording (REC)
- Short press → Start/Stop
- Resolution configurable in **Settings**

---

## Supported Hardware (Current)

- **FTDI‑based K‑Line cables**
- **Tactrix OpenPort 1.3 (compatible)**

---

## Experimental Hardware Support (Disabled by Default)

- CDC/ACM USB‑Serial adapters
- CH34x
- PL2303
- Other K‑Line interfaces

Bluetooth ELM327 devices are **not supported**.

---

## Supported Vehicles

- Subaru Impreza WRX / STI (GDB‑C, EJ20)
- Subaru Legacy / Forester models using **SSM2 over K‑Line**

---

# ⚠ Protocol Support Status

## ✔ SSM2 (4800 bps) — Fully Supported
- BF Init / A8 Init
- Fast / Slow MultiRead
- Stable on FireHD & Xperia devices

---

## ⚠ ISO9141‑2 (5‑Baud Init) — Experimental
- 5‑Baud init implemented
- ECU response (55 EA) not confirmed
- Disabled by default

---

## ⚠ KWP2000 (10400 bps) — Experimental
- FastInit / 5‑Baud / StartComm implemented
- No response on Subaru kei cars
- Disabled by default
- Requires caution due to shared K‑Line with **SRS ECU**

---

## ⚠ Meter Unit (K‑Line) — Under Investigation
- Subaru‑specific custom protocol
- Format varies by model/year

---

# ⚠ Safety Notice (Important)

Some Subaru vehicles share the **K‑Line** between multiple ECUs, including:

- Engine ECU
- Meter Unit
- **SRS (Airbag) ECU**

To ensure safety:

- ISO/KWP initialization is **disabled by default**
- SRS‑related address ranges are **blocked**
- Experimental protocols should be tested **only with volunteer vehicles**
- Normal operation uses **SSM2 only**

---

## Cable Wiring & Connection Guide

### FTDI K‑Line Basic Wiring

- **K‑Line → FTDI RX**
- **K‑Line → FTDI TX**
- **Ground → FTDI GND**

### Optional (for ISO/KWP experiments)

- **DTR → L‑Line**
- **RTS → L‑Line**

---

## How to Use

### DBGLP (Debug Loopback Mode)
Used to verify cable recognition.

### CONNECT
For devices where USB recognition does not automatically start communication.

### Debug Screen
Shows initialization, raw TX/RX, ECU responses, and errors.

### Settings
Gauge layout, units, transparency, donation, documentation.

### RST‑HLD
Resets gauge Min/Max values.

### StartLog
Starts CSV logging (1‑second interval).

### Rec (Recording)
- Short press → Start/Stop recording
- Resolution is set in **Settings**

---

## App Architecture

- CameraX
- OpenGL ES
- MediaCodec
- USB‑Serial
- Jetpack Compose
- DataStore

Pipeline:  
CameraX → SurfaceTexture → OpenGL → MediaCodec → MP4

---

## Known Issues

- Some FTDI adapters require LatencyTimer tuning
- Frame drops may occur during recording
- SSM1 not implemented
- ISO/KWP behavior varies by vehicle
- Meter protocol differs by model/year

---

## Support the Project

SSM DRMGL is a personal hobby project developed in my free time.  
If you would like to support the development, you can make a small contribution.

All users receive the same level of support regardless of donation status.  
Your contribution simply helps keep the project alive and motivates future updates.

Thank you for your support!

---

# 🛡️ Disclaimer (Detailed)

SSM DRMGL is an **unofficial, experimental application** developed as a personal hobby project.  
Please read the following disclaimers carefully before using the app.

---

### 🚗 Vehicle / ECU Disclaimer
- This application is **not an official tool** provided by any vehicle manufacturer.  
- ECU behavior varies by model, year, and vehicle condition.  
- The accuracy or completeness of ECU data is **not guaranteed**.  
- The developer assumes **no responsibility** for:
  - Vehicle malfunction  
  - ECU misbehavior  
  - Communication errors  
  - Any damage caused by using this application

---

### 🧪 Experimental Features Disclaimer
- HUD / Camera2 / GLRenderer / SSM2 / ISO9141 / KWP2000 are **experimental**.  
- Modified or malfunctioning vehicles may not operate correctly.

---

### 👁️ Driving Safety Disclaimer
- HUD display and screen interaction may cause **distraction or visibility obstruction**.  
- Do **not** operate the app while driving.  
- The developer is not responsible for accidents, violations, or incidents caused by distraction.

---

### 🔌 Power / Device Load Disclaimer
- Long‑term use may cause device heating.  
- Vehicle power sources may cause **voltage drops or battery load**.  
- The developer is not responsible for any device or vehicle damage caused by electrical conditions.

---

### 📱 Application Warranty Disclaimer
- This is a **personal hobby project**.  
- No warranty, support, or guaranteed updates are provided.  
- Features may change or be removed without notice.

---

### 🔒 Privacy & Data Disclaimer
- The app is distributed outside Google Play to avoid mandatory disclosure of personal address information.  
- No vehicle data or logs are transmitted externally.  
- See **PrivacyPolicy.md** for details.

---

### 📄 Agreement
By using this application, you agree to all disclaimers listed above.

---

## License

All Rights Reserved.

---

## Support / Issues

If you find a bug or have a feature request, please open an issue:

https://github.com/maoh3/SSM_DRMGL_DOC/issues

---

## Privacy Policy

https://maoh3.github.io/SSM_DRMGL_DOC/PrivacyPolicy

---

# 🇯🇵 日本語版 README
# SSM DRMGL（日本語版）

SSM DRMGL は、Subaru 車両向けの **SSM2 プロトコル専用**  
Android ダッシュボード & ロガーアプリです。

リアルタイム ECU モニタリング、CSV ロギング、ゲージ表示、  
オーバーレイ付き動画録画などを行うことができます。

**現在の安定状況（2026/06 時点）**
- **SSM2（4800bps）** → 安定動作・確認済み  
- **SSM1 / ISO9141‑2 / KWP2000** → 実験段階（デフォルト無効）  
- **メーターユニット（K‑Line）** → 調査中（未対応）

SSM : Subaru Select Monitor  
D : Drive  
R : Record  
M : Monitor  
G : Gauge  
L : Logger

---

## 機能

- ECU リアルタイムモニタリング（SSM2）
- CSV ロギング（Multi‑PID）
- ゲージ & ダッシュボード表示
- オーバーレイ付き動画録画
- USB‑OTG 通信
- Markdown ベースのアプリ内ドキュメント

---

## 追加機能

### ラップ計測（LAP モード）
簡易サーキットや周回テスト向けのラップタイマー。

- スタート地点付近で長押しして登録  
- 通過するたびにラップタイムを自動計測  
- ベストラップを保持・表示

### ACC 計測（0–100 km/h）
**SSM DRMGL 独自の加速計測ツール**。

- 設定した速度までの時間・距離を計測  
- 車重を登録すると推定馬力を算出  
- ベスト ACC を保持・表示

### ギアポジション表示
速度と RPM から現在のギアを推定表示。

### 録画（REC）
- 短押し：録画開始 / 停止  
- 解像度は **Setting 画面** で設定

---

## 対応デバイス（確認済み）

- **FTDI ベースの K‑Line ケーブル**  
- **Tactrix OpenPort 1.3（互換）**

---

## 実験的対応デバイス（デフォルト無効）

- CDC/ACM USB‑Serial  
- CH34x  
- PL2303  
- その他 K‑Line インターフェース

Bluetooth ELM327 は **非対応**。

---

## 動作確認済み車種

- Subaru Impreza WRX / STI（GDB‑C, EJ20）  
- Subaru Legacy / Forester（SSM2 + K‑Line 対応車）

---

# ⚠ プロトコル対応状況

## ✔ SSM2（4800bps）— 安定動作
- BF / A8 初期化  
- Fast / Slow MultiRead  
- FireHD / Xperia で安定動作

---

## ⚠ ISO9141‑2（5Baud Init）— 実験段階
- 5Baud 初期化は実装済み  
- ECU 応答（55EA）は未確認  
- デフォルト無効

---

## ⚠ KWP2000（10400bps）— 実験段階
- FastInit / 5Baud / StartComm 実装済み  
- Subaru 軽では応答なし  
- デフォルト無効  
- **SRS ECU と K‑Line を共有する車種があるため注意**

---

## ⚠ メーターユニット（K‑Line）— 調査中
- Subaru 独自プロトコル（SSM2 風）  
- 車種差が大きい

---

# ⚠ 安全性に関する重要事項

Subaru の一部車種では **K‑Line を複数 ECU が共有**しています。

特に：

- **SRS（エアバッグ）ECU**

は不正フレームに敏感です。

そのため：

- ISO/KWP は **デフォルト無効**  
- SRS アドレス帯は **ブロック**  
- 実験は **協力者の実車のみ**  
- 通常利用は **SSM2 のみ**

---

## ケーブル配線

### FTDI K‑Line 基本配線

- K‑Line → RX  
- K‑Line → TX  
- GND → GND

### （任意）ISO/KWP 用ライン

- DTR → L‑Line  
- RTS → L‑Line

---

## 使い方

DBGLP、CONNECT、Debug、Setting、RST‑HLD、StartLog、Rec  
（英語版と同じ動作）

---

## アプリ構成

- CameraX  
- OpenGL ES  
- MediaCodec  
- USB‑Serial  
- Jetpack Compose  
- DataStore  

Pipeline:  
CameraX → SurfaceTexture → OpenGL → MediaCodec → MP4

---

## 既知の問題

- FTDI の LatencyTimer 調整が必要な場合あり  
- 録画中にフレームドロップが発生する場合あり  
- SSM1 未実装  
- ISO/KWP は車種依存  
- メータープロトコルは車種差が大きい

---

## 開発支援について

SSM DRMGL は個人の趣味として開発しているプロジェクトです。  
寄付の有無に関わらず、すべてのユーザーに同じサポートを提供します。

いただいた支援は、今後の開発やモチベーション維持に役立てさせていただきます。

---

# 🛡️ 免責事項（詳細版）

SSM DRMGL は個人の空き時間で開発している **非公式・実験的アプリケーション** です。  
本アプリを利用する際は、以下の免責事項を必ずご確認ください。

---

### 🚗 車両・ECU に関する免責
- 本アプリは **車両メーカー公式ツールではありません**。  
- ECU の挙動は車種・年式・状態により大きく異なります。  
- 取得されるデータの **正確性・完全性は保証されません**。  
- 本アプリの利用に伴う  
  **車両故障・ECU 誤動作・通信トラブル・その他損害** について、開発者は一切責任を負いません。

---

### 🧪 実験的機能に関する免責
- HUD / Camera2 / GLRenderer / SSM2 / ISO9141 / KWP2000 は **実験的機能** です。  
- 改造車・故障車・特殊仕様車では正常に動作しない場合があります。

---

### 👁️ 運転中の安全に関する免責
- HUD 表示や画面操作は **視界妨害・注意散漫** を引き起こす可能性があります。  
- 運転中の操作は絶対に行わないでください。  
- 本アプリの利用に起因する **事故・違反・トラブル** について、開発者は一切責任を負いません。

---

### 🔌 電源・端末負荷に関する免責
- 長時間利用で端末が高温になる場合があります。  
- 車両側の電源状態により **電圧低下・バッテリー負荷** が発生する可能性があります。  
- これらに起因する端末故障・車両側トラブルについても責任を負いません。

---

### 📱 アプリ動作保証に関する免責
- 本アプリは **個人開発の趣味プロジェクト** です。  
- 動作保証・サポート・不具合対応は提供していません。  
- 予告なく仕様変更・機能削除・公開停止を行う場合があります。

---

### 🔒 プライバシー・データに関する免責
- Google Play を利用していません（住所公開を避けるため）。  
- 車両データ・ログは外部送信されません。  
- 詳細は **PrivacyPolicy.md** を参照してください。

---

### 📄 同意事項
本アプリを利用した時点で、上記免責事項に同意したものとみなします。

---

## ライセンス

All Rights Reserved.

---

## サポート / Issue

バグ報告や機能要望はこちら：

https://github.com/maoh3/SSM_DRMGL_DOC/issues

---

## プライバシーポリシー

https://maoh3.github.io/SSM_DRMGL_DOC/PrivacyPolicy

