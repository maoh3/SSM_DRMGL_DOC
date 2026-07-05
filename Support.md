# 🛠 Support Policy — SSM DRMGL

This document describes the **support policy**, **issue reporting rules**, and **limitations** for SSM DRMGL.  
SSM DRMGL is a personal hobby project developed in spare time, and support is provided on a best‑effort basis.

---

# 📌 1. Support Scope

SSM DRMGL is an **unofficial, experimental application** that communicates with vehicle ECUs.  
For safety reasons, support is limited to the following areas:

### ✔ Supported
- SSM2 (4800 bps) communication  
- FTDI / OpenPort 1.3 connection issues  
- HUD / Gauge display problems  
- Recording (CameraX → GL → MediaCodec) issues  
- ACC / LAP / Gear indicator behavior  
- General app bugs  
- Documentation corrections

### ❌ Not Supported
- Full ISO9141‑2 / KWP2000 / SSM1 communication  
- Meter Unit (K‑Line) experimental protocol  
- Custom ECU modifications  
- Vehicle electrical issues  
- Problems caused by faulty cables or wiring  
- Requests requiring reverse‑engineering of Subaru proprietary systems  
- Dangerous operations involving SRS ECU or shared K‑Line vehicles

---

# 🔧 2. About ISO/KWP Experimental Protocols (Initialization Only)

ISO9141‑2 and KWP2000 are **not fully implemented**,  
but the **communication initialization routines** are available for testing:

- 5‑Baud Init  
- FastInit  
- StartComm  

These routines only perform **communication initialization**,  
and do **not** modify, reset, or write to the ECU.

Full communication, PID reading, and vehicle‑specific decoding are **not implemented**  
and remain disabled by default for safety.

At this stage:

> **Without a proper cable, nothing can be tested.  
> If you are interested, please start by discussing how to build or prepare a compatible cable.**

If you can confirm ECU responses during initialization and provide logs,  
it may help future development.  
Any testing is done at your own discretion,  
and if any issues or failures occur, **no support or compensation can be provided**.

---

# ⚠ 3. Safety Limitations

Because this app interacts with vehicle ECUs, the following are **strictly outside the support scope**:

- Vehicle malfunction  
- ECU misbehavior  
- Communication errors caused by wiring or hardware  
- Issues caused by modified or malfunctioning vehicles  
- Any accident or incident caused by distraction while driving

Please use the app **at your own responsibility**.

---

# 📝 4. Before Opening an Issue

Before creating an Issue, please check:

1. README.md  
2. ReleaseNotes.md  
3. Download.md  
4. Known Issues section  

Many common questions are already documented.

---

# 🐞 5. Issue Reporting Template

When opening an Issue, please include the following information:

### 🔧 Device Information
- Android device model  
- Android version  
- CPU architecture (optional)

### 🚗 Vehicle Information
- Vehicle model  
- Year  
- Engine type (EJ20, EJ25, etc.)

### 🔌 Cable Information
- FTDI / OpenPort / other  
- Vendor / chipset  
- Wiring method (K‑Line → RX/TX, etc.)

### 📡 App Information
- App version (e.g., v0.90)  
- Mode used (SSM2 / ACC / LAP / REC / Debug)

### 🐛 Problem Details
- What happened  
- Expected behavior  
- Steps to reproduce  
- Screenshots or logs (if possible)

Providing complete information helps resolve issues faster.

---

# 🚫 6. Unsupported Requests

The following requests will be closed without action:

- “Enable full ISO/KWP communication”  
- “Access SRS ECU”  
- “Decode Meter Unit protocol”  
- Vehicle malfunction diagnosis  
- ECU tuning / rewriting  
- Any dangerous operation involving shared K‑Line vehicles

---

# 💬 7. Response Policy

- Support is **best‑effort**  
- Response time is **not guaranteed**  
- Development is done in personal spare time  
- Feature requests may be accepted or declined depending on feasibility

---

# ☕ 8. Donation Policy

Donations are **optional** and **do not affect support priority**.  
All users receive equal support regardless of donation status.

For donation information, please see:

👉 **SupportProject.md**

---

# 🛡 9. Disclaimer

- This app is provided **as‑is**  
- Use at your own risk  
- The developer is not responsible for:
  - Vehicle damage  
  - ECU malfunction  
  - Communication errors  
  - Accidents caused by distraction  
  - Any loss or damage resulting from app usage

---

# 📮 10. Issue Page

Issues can be submitted here:

👉 [GitHub Issues](ca://s?q=Open_GitHub_Issues)

---

# 🇯🇵 日本語版 Support Policy

# 🛠 サポート方針 — SSM DRMGL

このドキュメントは、SSM DRMGL の **サポート方針・Issue の書き方・サポート範囲・免責事項** をまとめたものです。  
SSM DRMGL は個人の空き時間で開発している趣味プロジェクトであり、サポートは **ベストエフォート** で提供されます。

---

# 📌 1. サポート範囲

SSM DRMGL は **非公式・実験的アプリケーション** であり、車両 ECU と通信します。  
安全のため、サポート範囲は以下に限定されます。

### ✔ サポート対象
- SSM2（4800bps）通信  
- FTDI / OpenPort 1.3 の接続問題  
- HUD / ゲージ表示の問題  
- 録画（CameraX → GL → MediaCodec）関連  
- ACC / LAP / ギア表示の挙動  
- 一般的なアプリの不具合  
- ドキュメントの修正

### ❌ サポート対象外
- ISO9141‑2 / KWP2000 / SSM1 の本通信  
- メーターユニット（K‑Line）の実験的プロトコル  
- ECU 改造・チューニング  
- 車両側の電装トラブル  
- ケーブルや配線不良による問題  
- Subaru 独自プロトコルの解析依頼  
- SRS ECU など危険な領域へのアクセス

---

# 🔧 2. ISO/KWP に関する補足（通信初期化のみ）

ISO9141‑2 / KWP2000 は **本通信は未実装** ですが、  
以下の **通信開始のための初期化処理のみ** テスト可能です：

- 5Baud Init  
- FastInit  
- StartComm  

これらは **通信初期化の応答を確認するための処理のみ**であり、  
ECU の内部状態を書き換える処理は一切ありません。

本通信・PID 読み取り・車種固有データ解析は未対応のため、  
安全上の理由からデフォルトでは無効化しています。

現状では：

> **適切なケーブルが無い場合、何もテストできません。  
> 興味がある方は、まずケーブルの作り方についてご相談ください。**

初期化シーケンスで ECU 応答を確認できた方は、  
ログ等をご提供いただけると実装が進む可能性があります。

実車テストは必須ではなく、  
行う場合は **ユーザー自身の判断でお願いします**。  
故障など何かが起きても、**対応や補償はできません**。

---

# ⚠ 3. 安全上の制限

車両 ECU と通信するため、以下は **サポート対象外** です。

- 車両故障  
- ECU の誤動作  
- 配線やケーブル不良による通信エラー  
- 改造車・故障車での問題  
- HUD 操作による事故・違反・トラブル

アプリの利用は **自己責任** でお願いします。

---

# 📝 4. Issue を作成する前に

Issue を作成する前に以下を確認してください：

1. README.md  
2. ReleaseNotes.md  
3. Download.md  
4. Known Issues  

多くの質問はすでに記載されています。

---

# 🐞 5. Issue の書き方テンプレート

Issue には以下の情報を記載してください：

### 🔧 端末情報
- Android 端末名  
- Android バージョン  
- CPU アーキテクチャ（任意）

### 🚗 車両情報
- 車種  
- 年式  
- エンジン型式（EJ20 / EJ25 など）

### 🔌 ケーブル情報
- FTDI / OpenPort / その他  
- メーカー / チップセット  
- 配線方法（K‑Line → RX/TX など）

### 📡 アプリ情報
- アプリバージョン（例：v0.90）  
- 使用モード（SSM2 / ACC / LAP / REC / Debug）

### 🐛 問題の詳細
- 発生した内容  
- 期待する動作  
- 再現手順  
- スクリーンショットやログ（可能なら）

情報が揃っているほど対応が早くなります。

---

# 🚫 6. 対応できない依頼

以下の依頼は対応できません：

- 「ISO/KWP を完全実装してほしい」  
- 「SRS ECU にアクセスしたい」  
- 「メーターユニットを解析してほしい」  
- 車両故障の診断依頼  
- ECU 書き換え・チューニング  
- 危険な操作を伴う依頼

---

# 💬 7. 返信ポリシー

- サポートは **ベストエフォート**  
- 返信速度は保証されません  
- 開発は個人の空き時間で行っています  
- 機能追加の要望は内容により採用・却下されます

---

# ☕ 8. 寄付について

寄付は **任意** であり、  
寄付の有無でサポート内容が変わることはありません。

寄付案内はこちら：

👉 **SupportProject.md**

---

# 🛡 9. 免責事項

- 本アプリは **現状のまま** 提供されます  
- 使用は自己責任でお願いします  
- 開発者は以下の責任を負いません：
  - 車両故障  
  - ECU 誤動作  
  - 通信エラー  
  - HUD 操作による事故  
  - その他すべての損害

---

# 📮 10. Issue ページ

不具合報告・要望はこちら：

👉 [GitHub Issues](ca://s?q=Open_GitHub_Issues)

安全にご利用ください。
