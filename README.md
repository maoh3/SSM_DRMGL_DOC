# 🚙 SSM DRMGL Sample GDB-C 

<img width="360" height="200" alt="ezgif-53b295e254941383" src="https://github.com/user-attachments/assets/00c0b493-be20-4a39-99b4-2983aa9fc0f1" />

[日本語セクションはこちら](#日本語)

# 📚 Documentation Index (GitHub Pages)

- Demo (Screenshots & Examples)  
  [https://maoh3.github.io/SSM_DRMGL_DOC/demo/demo.html](https://github.com/maoh3/SSM_DRMGL_DOC/blob/main/demo.md)

- Cable Board (K-Line / FTDI Wiring Guide)  
  [https://maoh3.github.io/SSM_DRMGL_DOC/cable_board/cable_board.html](https://github.com/maoh3/SSM_DRMGL_DOC/blob/main/Cable_board.md)

- Manual  
  https://maoh3.github.io/SSM_DRMGL_DOC/Manual.html

- Download APK  
  https://maoh3.github.io/SSM_DRMGL_DOC/Download.html

- Support  
  https://maoh3.github.io/SSM_DRMGL_DOC/Support.html

- SupportProject  
  https://maoh3.github.io/SSM_DRMGL_DOC/SupportProject.html

- Release Notes  
  https://maoh3.github.io/SSM_DRMGL_DOC/ReleaseNotes.html

- Privacy Policy  
  https://maoh3.github.io/SSM_DRMGL_DOC/PrivacyPolicy.html

---

# SSM DRMGL  
Android Dashboard, Logger & Recorder for Subaru SSM2 Vehicles  
**Confirmed working on Subaru Impreza WRX/STI (GDB, EJ20)**  

SSM DRMGL is an Android dashboard, logger, and video recorder designed for Subaru vehicles using the **SSM2 protocol**.  
It provides real‑time ECU monitoring, multi‑PID logging, gauge display, and video recording with overlay.

This project is a **personal hobby**, developed in spare time.  
All experimental protocols are disabled by default for safety.

---

# 📌 Current Status (2026/07)

- **SSM2 (4800 bps)** — Fully supported & stable  
- **ISO9141‑2 / KWP2000** — *Initialization only*, disabled by default  
- **SSM1 / Meter Unit (K‑Line)** — Under investigation  
- **Experimental USB‑Serial devices** — Disabled by default

SSM : Subaru Select Monitor  
D : Drive / R : Record / M : Monitor / G : Gauge / L : Logger

---

# 🚗 Features

- Real‑time ECU monitoring (**SSM2**)  
- Multi‑PID CSV logging  
- Gauge & dashboard UI  
- Video recording with data overlay  
- USB‑OTG communication  
- In‑app documentation (Markdown)

---

# 🧩 Additional Features

## Lap Timer (LAP Mode)
- Long‑press near the start/finish line to register  
- Each pass records a new lap  
- Best lap stored and displayed

## ACC Measurement (0–100 km/h)
- Measures time & distance to target speed  
- Configurable target speed  
- Vehicle weight input  
- Estimated horsepower calculation  
- Best ACC stored

## Gear Position Indicator
- Gear estimation from RPM & speed

## Recording (REC)
- Short press → Start/Stop  
- Resolution configurable in **Settings**

---

# 🔌 Supported Hardware

- **FTDI‑based K‑Line cables**  
- **Tactrix OpenPort 1.3 (compatible)**

---

# 🧪 Experimental Hardware (Disabled by Default)

- CDC/ACM USB‑Serial  
- CH34x  
- PL2303  
- Other K‑Line interfaces  

Bluetooth ELM327 devices are **not supported**.

---

# 🚙 Supported Vehicles (Confirmed)

- Subaru Impreza WRX / STI (GDB‑C, EJ20)  
- Subaru Legacy / Forester using **SSM2 over K‑Line**

---

# ⚠ Protocol Support Status

## ✔ SSM2 (4800 bps) — Fully Supported
- BF Init / A8 Init  
- Fast / Slow MultiRead  
- Stable on FireHD & Xperia

---

## ⚠ ISO9141‑2 / KWP2000 — Initialization Only

Implemented initialization routines:

- 5‑Baud Init  
- FastInit  
- StartComm  

These routines only test **communication initialization**  
and do **not** modify or reset the ECU.

Full communication, PID reading, and decoding are **not implemented**.

> **If you are interested in ISO/KWP experiments,  
> please start by discussing how to build or prepare a compatible cable.  
> Without a proper cable, nothing can be tested.**

If initialization responses are confirmed,  
logs may help future development.

All experiments are **at your own discretion**,  
and any failures or issues **cannot be supported or compensated**.

---

## ⚠ Meter Unit (K‑Line)
- Subaru‑specific protocol  
- Format varies by model/year  
- Under investigation

---

# ⚠ Safety Notice

Some Subaru vehicles share the **K‑Line** between multiple ECUs:

- Engine ECU  
- Meter Unit  
- **SRS (Airbag) ECU**

To ensure safety:

- ISO/KWP are **disabled by default**  
- SRS‑related address ranges are **blocked**  
- Experimental protocols should be tested only by volunteers  
- Normal operation uses **SSM2 only**

---

# 🔧 Cable Wiring Guide

### FTDI K‑Line Basic Wiring
- K‑Line → RX  
- K‑Line → TX  
- GND → GND

### Optional (ISO/KWP experiments)
- DTR → L‑Line  
- RTS → L‑Line

---

# 📱 How to Use

- **DBGLP** — Debug loopback  
- **CONNECT** — Manual USB connect  
- **Debug Screen** — Shows init, raw TX/RX, responses  
- **Settings** — Layout, units, transparency, docs  
- **RST‑HLD** — Reset gauge Min/Max  
- **StartLog** — CSV logging  
- **Rec** — Start/Stop video recording

---

# 🏗 App Architecture

- CameraX  
- OpenGL ES  
- MediaCodec  
- USB‑Serial  
- Jetpack Compose  
- DataStore  

Pipeline:  
CameraX → SurfaceTexture → OpenGL → MediaCodec → MP4

---

# 🐞 Known Issues

- Some FTDI adapters require LatencyTimer tuning  
- Frame drops may occur during recording  
- SSM1 not implemented  
- ISO/KWP behavior varies by vehicle  
- Meter protocol differs by model/year

---

# 🤝 Support the Project

SSM DRMGL is a personal hobby project.  
Donations do **not** affect support priority.

SupportProject:  
https://maoh3.github.io/SSM_DRMGL_DOC/SupportProject.html

---

# 🛡️ Disclaimer

SSM DRMGL is an **unofficial, experimental application**.  
Use at your own risk.

The developer is not responsible for:

- Vehicle malfunction  
- ECU misbehavior  
- Communication errors  
- Electrical issues  
- Accidents or incidents caused by distraction  
- Any damage resulting from app usage

Privacy Policy:  
https://maoh3.github.io/SSM_DRMGL_DOC/PrivacyPolicy.html

---

# 🐛 Issues

Bug reports & feature requests:  
https://github.com/maoh3/SSM_DRMGL_DOC/issues

---
## 日本語

# 🇯🇵 日本語版 README

# SSM DRMGL（日本語版）

Subaru SSM2 車両向け Android ダッシュボード & ロガー  
**動作確認済み：Impreza WRX/STI（GDB・EJ20）**

リアルタイム ECU モニタリング、CSV ロギング、ゲージ表示、  
オーバーレイ付き動画録画などが可能です。

---

# 📌 現在の安定状況（2026/07）

- **SSM2（4800bps）** → 安定動作  
- **ISO9141‑2 / KWP2000** → *通信初期化のみ*（デフォルト無効）  
- **SSM1 / メーターユニット** → 調査中  
- **実験的 USB‑Serial** → デフォルト無効

---

# 🚗 機能

- ECU リアルタイムモニタリング  
- CSV ロギング  
- ゲージ表示  
- オーバーレイ付き動画録画  
- USB‑OTG 通信  
- アプリ内ドキュメント

---

# 🧩 追加機能

### ラップ計測（LAP）
- 長押しでスタート地点登録  
- 通過で自動ラップ計測  
- ベストラップ保持

### ACC 計測（0–100 km/h）
- 設定速度までの時間・距離  
- 車重入力で推定馬力  
- ベスト ACC 表示

### ギア表示
- RPM と速度から推定

### 録画（REC）
- 短押しで開始/停止  
- 解像度は設定画面で変更

---

# 🔌 対応ケーブル

- FTDI K‑Line  
- OpenPort 1.3（互換）

---

# ⚠ ISO/KWP（通信初期化のみ）

以下の **通信初期化処理のみ** 実装済み：

- 5Baud Init  
- FastInit  
- StartComm  

ECU の内部状態を書き換える処理はありません。

> **適切なケーブルが無い場合、何もテストできません。  
> 興味がある方は、まずケーブルの作り方についてご相談ください。**

初期化応答が取れた場合、  
ログ提供で実装が進む可能性があります。

実車テストは任意で、  
故障が起きても **対応・補償はできません**。

---

# ⚠ 安全性

Subaru の一部車種は **K‑Line を複数 ECU が共有**します。  
特に **SRS（エアバッグ）ECU** は敏感です。

- ISO/KWP → デフォルト無効  
- SRS アドレス帯 → ブロック  
- 実験は協力者のみ  
- 通常利用は SSM2 のみ

---

# 🛡 免責事項

本アプリは **非公式・実験的** です。  
利用は自己責任でお願いします。

開発者は以下の責任を負いません：

- 車両故障  
- ECU 誤動作  
- 通信エラー  
- 電源トラブル  
- 事故・違反  
- その他すべての損害

---

# 🐛 Issue

https://github.com/maoh3/SSM_DRMGL_DOC/issues

---

# 🔒 プライバシーポリシー

https://maoh3.github.io/SSM_DRMGL_DOC/PrivacyPolicy.html
