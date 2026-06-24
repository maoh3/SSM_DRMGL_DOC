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
A lightweight lap‑timing system inspired by the style of classic Subaru diagnostic tools.

- Long‑press the screen near the start/finish line to register the start point
- Each time the vehicle passes the point, a new lap time is recorded
- Best lap time is stored and displayed

### ACC Measurement (0–100 km/h)
A performance measurement tool **original to SSM DRMGL**.

- Measures time and distance required to reach a target speed (default: 100 km/h)
- Target speed can be changed in Settings
- Vehicle weight can be registered
- Calculates estimated horsepower based on acceleration and mass
- Best ACC result is displayed during the session

### Gear Position Indicator
Displays the current gear based on RPM and vehicle speed.

- Set individual gear ratios and final drive in Settings
- Calculates gear position in real time
- Useful for vehicles without a factory gear indicator

### Recording (REC)
- Short press → Start/Stop recording
- Recording resolution is configured in **Settings**

LAP timing and gear estimation follow the spirit of older tools like WinSSM,  
while **ACC measurement is a new feature unique to SSM DRMGL**.

---

## Supported Hardware (Current)

Confirmed working:

- **FTDI‑based K‑Line cables**
  - TX / RX supported
  - DTR / RTS supported (for future ISO/KWP experiments)
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

Confirmed working:

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
- Requires caution due to shared K‑Line with SRS ECU

---

## ⚠ Meter Unit (K‑Line) — Under Investigation
- Subaru‑specific custom protocol (SSM2‑like)
- Format varies by model/year
- Disabled until more data is collected

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

## Disclaimer

This software is provided **as‑is**.
Use at your own risk.

---

## License

All Rights Reserved.

---

# 🇯🇵 日本語版 README

# SSM DRMGL

SSM DRMGL は、Subaru 車両向けの **SSM2 プロトコル専用**
Android ダッシュボード & ロガーアプリです。

現在の安定版では **SSM2（4800bps）のみ対応**。
**SSM1 / ISO9141‑2 / KWP2000 ** は
**実験段階（デフォルト無効）** です。

---

## 機能

- ECU リアルタイムモニタリング（SSM2）
- CSV ロギング
- ゲージ & ダッシュボード表示
- オーバーレイ付き動画録画
- USB‑OTG 通信
- アプリ内ドキュメント

---

## 追加機能

### ラップ計測（LAP モード）
簡易サーキットや周回テスト向けのラップタイマー。

- スタート地点付近で画面を長押ししてスタート位置を登録
- 通過するたびにラップタイムを自動計測
- ベストラップを保持・表示

### ACC 計測（0–100 km/h）
**SSM DRMGL 独自の加速計測ツール**。

- 設定した速度（デフォルト 100 km/h）に到達するまでの時間と距離を計測
- 車重を登録することで推定馬力を算出
- ベスト ACC を保持・表示

### ギアポジション表示
速度と RPM から現在のギアを推定表示。

- 各ギア比とファイナルを設定画面で登録
- リアルタイムでギアを算出

### 録画（REC）
- 短押し：録画開始 / 停止
- 録画解像度は **Setting 画面** で設定

ラップ計測とギア表示は、従来の診断ツールの流れを踏襲した機能であり、  
**ACC 計測は SSM DRMGL 独自の新機能**です。

---

## 現在の対応デバイス

- **FTDI ベースの K‑Line ケーブル**
- **Tactrix OpenPort 1.3（互換）**

---

## 将来対応予定デバイス（デフォルト無効）

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

---

## ⚠ ISO9141‑2（5Baud Init）— 実験段階
- 5Baud 初期化は実装済み
- 55EA 応答は未確認

---

## ⚠ KWP2000（10400bps）— 実験段階
- FastInit / 5Baud / StartComm 実装済み
- Subaru 軽では応答なし
- SRS ECU と K‑Line を共有する車種があるため注意

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
（説明は英語版と同じ）

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
もし開発を応援していただける場合は、少額のサポート（寄付）を受け付けています。

寄付の有無に関わらず、すべてのユーザーに同じサポートを提供します。
いただいた支援は、今後の開発やモチベーション維持に役立てさせていただきます。

応援していただけると嬉しいです。

---

## 免責事項

本アプリは **現状のまま** 提供されます。
使用に伴うすべてのリスクは利用者が負います。

---

## ライセンス

All Rights Reserved.



