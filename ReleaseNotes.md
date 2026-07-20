# 📄 SSM DRMGL — Release Notes

[日本語セクションはこちら](#日本語)

**Version:** v0.91  
**Release:** 2nd Release  
**Date:** 2026‑07

SSM DRMGL is a dashboard & logger application for Subaru vehicles using the **SSM2 protocol**.  
This release focuses on HUD improvements, G‑Ball upgrades, ACC/LAP stability, and preliminary ELM327 support.

---

# 🚀 New Features / Improvements (v0.91)

## ✔ Revision Display Added
- HUD now shows **Rev 0.91**  
- Helps users confirm the running version directly on-screen

## ✔ AFR Gauge Simplified
- Removed **Max/Min hold** feature  
- Gauge now focuses on the **practical AFR operating range**  
- Improved real‑time monitoring visibility

## ✔ Knock Indicator Updated (IAM → LIT)
- IAM removed  
- New indicators: **LIT + FBKC**  
- Normal ranges:  
  - **LIT: 60–65**  
  - **FBKC: 0–10**

## ✔ G‑Ball Major Upgrade
- Added **LPF (Low‑Pass Filter)** to reduce road noise  
- Added **Street (0.3G)** and **Circuit (1.0G)** sensitivity modes  
- Added **front/back** and **left/right inversion** options  
  - Allows users to compensate for phone orientation differences  
- More stable and customizable G‑force visualization

## ✔ ACC Measurement Improvements
- Horsepower calculation method revised  
- Previous “instant HP” was too localized  
- New method provides more stable readings  
- Developer tested with **0–50 km/h** due to environment limitations

## ✔ LAP Mode Fixes & Enhancements
- Fixed issue where LAP could end prematurely before crossing the start line  
- Added **start‑line blinking indicator** (3 seconds) when crossing  
- More reliable lap detection and visual feedback

## ✔ Preliminary ELM327 Support (Debug Only)
- Added basic ELM327 logging in Debug screen  
- Based on Subaru R2 (EN07) testing  
- Mode01 decoding not implemented  
- Volunteers welcome (see issue #06)

---

# 🛠 Fixed Issues
- ACC/LAP mode switching stability  
- HUD transparency consistency  
- Start‑line registration reliability  
- G‑Ball smoothing improvements  
- Minor UI cleanup

---

# ⚠ Known Issues
- Frame drops during recording  
- FTDI latency differences  
- ISO/KWP behavior varies by vehicle  
- Meter protocol differs by model/year  
- SSM1 not implemented  
- ELM327 support is experimental (Debug only)

---

# 🔧 Verified Devices
- FireHD‑10  
- Xperia 10 III  
- FTDI (FT232RL)  
- OpenPort 1.3 (compatible)  
- ELM327 (Bluetooth) — Debug only

---

# 📥 Download

👉 **SSM DRMGL APK (v0.91)**  
https://github.com/maoh3/SSM_DRMGL_DOC/releases/download/SSM_DRMGL_0091_release/SSM_DRMGL_00.91_release.apk

Release Page:  
https://github.com/maoh3/SSM_DRMGL_DOC/releases/tag/SSM_DRMGL_0091_release

---

# 🛡️ Safety & Disclaimer

- This app is **not an official Subaru tool**  
- ECU behavior varies by vehicle  
- No guarantee of data accuracy  
- Developer is not responsible for:
  - Vehicle damage  
  - ECU malfunction  
  - Communication errors  
  - Accidents caused by distraction  
- Do not operate while driving  
- Use at your own risk

---

## 日本語

# 🇯🇵 日本語版 Release Notes

# 📄 SSM DRMGL — リリースノート  
**バージョン:** v0.91  
**リリース:** 第2版  
**日付:** 2026‑07

SSM DRMGL は Subaru 車両向けの **SSM2 ダッシュボード & ロガーアプリ**です。  
本リリースでは HUD 改善、G‑Ball の大幅アップデート、ACC/LAP の安定化、  
ELM327 の仮対応などを追加しています。

---

# 🚀 新機能 / 改善点（v0.91）

## ✔ Revision 表示を追加
- HUD に **Rev 0.91** を表示  
- 実行中のバージョンが一目で確認可能

## ✔ AFR ゲージの簡素化
- **Max/Min ホールド機能を削除**  
- 通常使用領域にフォーカスしたゲージ表示へ変更  
- モニタリングがより実用的に

## ✔ ノック指標を IAM → LIT に変更
- IAM を廃止  
- 新指標：**LIT + FBKC**  
- 正常範囲：  
  - **LIT：60〜65**  
  - **FBKC：0〜10**

## ✔ G‑Ball の大幅アップデート
- **LPF（ローパスフィルタ）追加**で路面ノイズを低減  
- **Street（0.3G）/ Circuit（1.0G）** の感度切替  
- **前後・左右反転機能**を追加  
  - 端末の置き方の個人差を吸収  
- より滑らかで安定した G 表示に

## ✔ ACC 計測の改善
- 馬力計算方式を安定化  
- 旧方式（瞬間馬力）は局所的すぎたため変更  
- 開発者は **0〜50 km/h** で検証

## ✔ LAP モードの修正と強化
- スタートライン通過前に LAP が切れる不具合を修正  
- スタートライン通過時に **3 秒間点滅**する機能を追加  
- ラップ検出の信頼性向上

## ✔ ELM327 の仮対応（Debug のみ）
- Debug 画面でログ確認が可能  
- R2（EN07）ベースの簡易実装  
- Mode01 の解析は未実装  
- 協力者募集中（issue #06）

---

# 🛠 修正点
- ACC/LAP モード切替の安定化  
- HUD α値の統一  
- スタートライン登録の信頼性向上  
- G‑Ball の平滑化  
- UI の軽微な整理

---

# ⚠ 既知の問題
- 録画中のフレームドロップ  
- FTDI ケーブルによる遅延差  
- ISO/KWP は車種依存  
- メータープロトコルは車種差が大きい  
- SSM1 未実装  
- ELM327 は仮対応（Debug のみ）

---

# 🔧 動作確認デバイス
- FireHD‑10  
- Xperia 10 III  
- FTDI（FT232RL）  
- OpenPort 1.3（互換）  
- ELM327（Bluetooth）※Debug のみ

---

# 📥 ダウンロード

👉 **SSM DRMGL APK（v0.91）**  
https://github.com/maoh3/SSM_DRMGL_DOC/releases/download/SSM_DRMGL_0091_release/SSM_DRMGL_00.91_release.apk

リリースページ  
https://github.com/maoh3/SSM_DRMGL_DOC/releases/tag/SSM_DRMGL_0091_release

---

# 🛡️ 安全性・免責事項

- 本アプリは **車両メーカー公式ツールではありません**  
- ECU の挙動は車種・年式・状態により異なります  
- データの正確性は保証されません  
- 車両故障・ECU 誤動作・通信トラブルについて  
  **開発者は一切責任を負いません**  
- HUD は視界妨害の可能性があります  
- 運転中の操作は禁止  
- 使用は自己責任でお願いします

---

# 🔒 プライバシーポリシー

https://maoh3.github.io/SSM_DRMGL_DOC/PrivacyPolicy
