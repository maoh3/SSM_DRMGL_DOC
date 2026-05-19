# SSM DRMGL

SSM DRMGL is an Android dashboard and logger application for Subaru vehicles using the SSM2 protocol.  
It provides real‑time ECU monitoring, data logging, gauge display, and video recording with overlay.

This version currently supports **SSM2 only**.  
Support for **SSM1**, **KWP2000**, and **ISO9141‑2** is planned for future releases.

D : Drive  
R : Record  
M : Monitor  
G : Gauge  
L : Logger

---

## Features

- Real‑time ECU monitoring (SSM2)
- Multi‑PID data logging (CSV)
- Gauge & dashboard UI
- Video recording with data overlay
- USB‑OTG communication
- Markdown‑based in‑app documentation

---

## Supported Hardware (Current)

Currently supported:

- **FTDI‑based K‑Line cables**
- **Tactrix OpenPort 1.3**

These devices have been tested and confirmed working.

---

## Planned Hardware Support (Future)

The following devices are planned for future support:

- CDC/ACM USB‑Serial adapters
- CH34x
- PL2303
- Other K‑Line interfaces
- Additional diagnostic cables

Bluetooth ELM327 devices will **not** be supported.

---

## Supported Vehicles

Confirmed working:

- Subaru Impreza WRX / STI (GDB, EJ20)
- Subaru Legacy / Forester models using SSM2 over K‑Line

Additional vehicle support will be expanded in future updates.

---

## Planned Protocol Support

Future versions aim to support:

- **SSM1**
- **KWP2000**
- **ISO9141‑2**

These protocols require additional research and testing.

---

## App Architecture

- **CameraX** for camera preview
- **OpenGL ES** for gauge rendering and overlay
- **MediaCodec** for hardware‑accelerated video encoding
- **USB‑Serial** for ECU communication
- **Jetpack Compose** for UI
- **DataStore** for persistent settings

Processing pipeline:

```
CameraX → SurfaceTexture → OpenGL → MediaCodec → MP4
```

---

## Logging Format (CSV)

Each log entry includes:

- Timestamp
- PID name
- Raw value
- Converted value
- Units

Example:

```
123456, EngineSpeed, 0x1A 0xF0, 680, rpm
```

---

## Donations

If you would like to support the development of SSM DRMGL,  
you can donate using either of the following methods:

### **Google Play (In‑App Donation)**
Convenient one‑tap donation using your Google account.  
Available options may vary by region.

### **External Donation Page**
Supports international payments with lower fees.  
You can choose preset amounts or enter a custom amount.

Your support helps ongoing development, maintenance, and future protocol research.

If you made a donation and want your request to be prioritized,
please include your Donation ID (Google Play Order ID, PayPal Transaction ID,
or Supporter Code shown on the donation page) when creating a GitHub Issue.

---

## Known Issues

- Some FTDI adapters may require LatencyTimer tuning
- Frame drops may occur on certain devices during video recording
- SSM1 is not yet implemented
- KWP2000 initialization varies by vehicle

---

## Disclaimer

This application is provided **as‑is** without any warranties.  
Use it at your own risk.

- The developer is **not responsible** for any damage, malfunction, or unexpected behavior caused by ECU communication, data logging, or vehicle operation.
- Do not operate the application while driving.
- Always ensure safe conditions before using diagnostic or logging functions.
- Vehicle behavior may vary depending on model, year, and modifications.
- Logged data should not be used as the sole basis for tuning or mechanical decisions.

By using this application, you agree that the developer assumes **no liability** for any direct or indirect consequences.

---

## License

All Rights Reserved.

This software, including its source code, documentation, and associated assets,  
may not be copied, modified, distributed, or reverse‑engineered without explicit permission  
from the developer.

---

# 日本語版 README

# SSM DRMGL

SSM DRMGL は、Subaru 車両向けの SSM2 プロトコルを使用した  
Android 用ダッシュボード & ロガーアプリです。  
ECU のリアルタイム監視、データロギング、ゲージ表示、  
およびオーバーレイ付き動画録画を提供します。

現在サポートしているのは **SSM2 のみ** です。  
将来的に **SSM1 / KWP2000 / ISO9141‑2** の対応を予定しています。

D : Drive  
R : Record  
M : Monitor  
G : Gauge  
L : Logger

---

## 機能

- ECU のリアルタイムモニタリング（SSM2）
- 複数 PID のデータロギング（CSV）
- ゲージ & ダッシュボード UI
- オーバーレイ付き動画録画
- USB‑OTG 通信
- アプリ内 Markdown ドキュメント表示

---

## 現在の対応デバイス

現時点で動作確認済みのデバイス：

- **FTDI ベースの K‑Line ケーブル**
- **Tactrix OpenPort 1.3**

これらのデバイスは実機で動作確認済みです。

---

## 将来対応予定デバイス

以下のデバイスは将来的に対応予定です：

- CDC/ACM USB‑Serial アダプタ
- CH34x
- PL2303
- その他の K‑Line インターフェース
- 追加の診断ケーブル

Bluetooth ELM327 デバイスには **対応しません**。

---

## 動作確認済み車種

- Subaru Impreza WRX / STI（GDB, EJ20）
- Subaru Legacy / Forester（SSM2 + K‑Line 対応車）

今後、対応車種は順次拡大予定です。

---

## 今後の対応予定プロトコル

- **SSM1**
- **KWP2000**
- **ISO9141‑2**

これらのプロトコルは追加の調査・検証が必要です。

---

## アプリ構成

- **CameraX**：カメラプレビュー
- **OpenGL ES**：ゲージ描画・オーバーレイ
- **MediaCodec**：ハードウェアエンコード
- **USB‑Serial**：ECU 通信
- **Jetpack Compose**：UI
- **DataStore**：設定保存

処理パイプライン：

```
CameraX → SurfaceTexture → OpenGL → MediaCodec → MP4
```

---

## ログ形式（CSV）

各ログエントリには以下が含まれます：

- タイムスタンプ
- PID 名
- 生データ（Raw）
- 変換後の値
- 単位

例：

```
123456, EngineSpeed, 0x1A 0xF0, 680, rpm
```

---

## 寄付について

SSM DRMGL の開発・保守を支援していただける場合、  
以下の方法で寄付が可能です。

### **Google Play（アプリ内寄付）**
Google アカウントでワンタップ寄付が可能です。  
地域により利用可能な金額が異なる場合があります。

### **外部寄付ページ**
国際決済に対応し、手数料が低い方式です。  
プリセット金額または自由金額を選択できます。

いただいた支援は、今後の開発・保守・プロトコル調査に活用されます。

寄付をいただいた方で、要望の優先対応を希望される場合は、
GitHub Issue 作成時に「寄付ID（Google Play の注文番号、PayPal の取引ID、
または寄付ページに表示されたサポーターコード）」を記載してください。

---

## 既知の問題

- 一部の FTDI アダプタは LatencyTimer の調整が必要な場合があります
- 動画録画中に端末によってはフレームドロップが発生することがあります
- SSM1 は未実装
- KWP2000 の初期化は車種により挙動が異なります

---

## 免責事項

本アプリは **現状のまま（AS IS）** 提供されます。  
使用に伴うすべてのリスクは利用者が負うものとします。

- ECU 通信・データロギング・車両操作に起因する  
  いかなる損害・故障・不具合についても  
  開発者は **一切の責任を負いません**。
- 運転中の操作は絶対に行わないでください。
- 診断・ロギング機能の使用は安全な環境で行ってください。
- 車両の状態や改造内容により挙動が変わる場合があります。
- ログデータは整備・チューニング判断の唯一の根拠として使用しないでください。

本アプリを使用することで、  
開発者は直接的・間接的な結果に対し **一切の責任を負わない** ことに同意したものとみなします。

---

## ライセンス

All Rights Reserved.

本ソフトウェア（ソースコード、ドキュメント、関連アセットを含む）は、  
開発者の明示的な許可なく、複製・改変・再配布・リバースエンジニアリングを行うことを禁止します。
