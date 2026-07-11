# 📄 SSM DRMGL — Release Notes  

[日本語セクションはこちら](#日本語)

**Version:** v0.90  
**Release:** 1st Test Release  
**Date:** 2026‑06

SSM DRMGL is a dashboard & logger application for Subaru vehicles using the **SSM2 protocol**.  
This release focuses on stable SSM2 communication, HUD improvements, recording pipeline, and new measurement tools.

---

# 🚀 New Features / Improvements (v0.90)

## ✔ Stable SSM2 (4800 bps)
- BF Init / A8 Init stabilized  
- Fast / Slow MultiRead optimized  
- Verified on FireHD & Xperia devices  
- Reduced load during multi‑PID polling

## ✔ HUD / Gauge Improvements
- Unified alpha transparency  
- Reduced rendering load  
- Added RST‑HLD (Min/Max reset)

## ✔ ACC Measurement (0–100 km/h)
- Measures time & distance  
- Vehicle weight input  
- Estimated horsepower calculation  
- Best ACC stored

## ✔ LAP Timer
- Long‑press to register start point  
- Auto lap detection  
- Best lap stored  
- Improved visibility

## ✔ Recording (REC)
- CameraX → GL → MediaCodec → MP4 pipeline  
- Overlay rendering  
- Selectable resolution (480p / 720p / 1080p)  
- Stable on FireHD & Xperia

## ✔ Gear Position Estimation
- Gear ratios configurable  
- Real‑time gear calculation

## ✔ USB‑OTG / FTDI
- Stable FTDI communication  
- DTR / RTS control implemented  
- OpenPort 1.3 compatible

---

# 🧪 Experimental Features (Disabled by Default)

## ⚠ ISO9141‑2 (5Baud Init)
- Init implemented  
- ECU response not confirmed  
- Disabled for safety

## ⚠ KWP2000 (10400 bps)
- FastInit / 5Baud / StartComm implemented  
- No response on Subaru kei cars  
- Disabled due to shared K‑Line with **SRS ECU**

## ⚠ Meter Unit (K‑Line)
- Subaru‑specific protocol  
- Under investigation

---

# 🛠 Fixed Issues
- FTDI LatencyTimer tuning  
- HUD rendering optimization  
- Frame sync improvements  
- USB auto‑connect reliability  
- Settings UI cleanup

---

# ⚠ Known Issues
- Frame drops during recording  
- FTDI latency differences  
- ISO/KWP behavior varies by vehicle  
- Meter protocol differs by model/year  
- SSM1 not implemented  
- Device heating during long recording

---

# 🔧 Verified Devices
- FireHD‑10  
- Xperia 10 III  
- FTDI (FT232RL)  
- OpenPort 1.3 (compatible)

---

# 📥 Download

👉 **[SSM DRMGL APK （v0.90）](https://github.com/maoh3/SSM_DRMGL_DOC/releases/download/SSM_DRMGL_0090_1st_testr-release/SSM_DRMGL_00.90_testrelease.apk)**


Release Page:  
https://github.com/maoh3/SSM_DRMGL_DOC/releases/tag/SSM_DRMGL_0090_1st_testr-release

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
**バージョン:** v0.90  
**リリース:** 初回テスト版  
**日付:** 2026‑06

SSM DRMGL は Subaru 車両向けの **SSM2 ダッシュボード & ロガーアプリ**です。  
本リリースでは SSM2 の安定化、HUD 改善、録画パイプライン、ACC 計測などが利用可能です。

---

# 🚀 新機能 / 改善点（v0.90）

## ✔ SSM2（4800bps）安定化
- BF / A8 初期化の安定化  
- Fast / Slow MultiRead の最適化  
- FireHD / Xperia で安定動作  
- Multi‑PID の負荷軽減

## ✔ HUD / ゲージ改善
- α値を統一  
- 描画負荷を軽減  
- RST‑HLD（Min/Max リセット）追加

## ✔ ACC 計測（0–100 km/h）
- 加速時間・距離を計測  
- 車重入力で推定馬力算出  
- ベスト ACC を保持

## ✔ ラップ計測（LAP）
- 長押しでスタート地点登録  
- 自動ラップ検出  
- ベストラップ保持  
- UI 改善

## ✔ 録画（REC）
- CameraX → GL → MediaCodec → MP4  
- オーバーレイ表示  
- 解像度選択（480p / 720p / 1080p）  
- FireHD / Xperia で動作確認

## ✔ ギアポジション推定
- ギア比設定  
- 速度と RPM から推定

## ✔ USB‑OTG / FTDI
- FTDI 安定動作  
- DTR / RTS 制御  
- OpenPort 1.3 互換

---

# 🧪 実験的機能（デフォルト無効）

## ⚠ ISO9141‑2（5Baud）
- 初期化は実装済み  
- ECU 応答未確認  
- 安全のため無効化

## ⚠ KWP2000（10400bps）
- FastInit / 5Baud / StartComm 実装済み  
- Subaru 軽では応答なし  
- **SRS ECU と K‑Line 共有のため危険 → 無効化**

## ⚠ メーターユニット（K‑Line）
- Subaru 独自プロトコル  
- 調査中

---

# 🛠 修正点
- FTDI LatencyTimer の調整  
- HUD 描画負荷の軽減  
- フレーム同期改善  
- USB 自動接続の安定化  
- 設定画面の整理

---

# ⚠ 既知の問題
- 録画中にフレームドロップ  
- FTDI ケーブルによる遅延差  
- ISO/KWP は車種依存  
- メータープロトコルは車種差が大きい  
- SSM1 未実装  
- 長時間録画で端末温度上昇

---

# 🔧 動作確認デバイス
- FireHD‑10  
- Xperia 10 III  
- FTDI（FT232RL）  
- OpenPort 1.3（互換）

---

# 📥 ダウンロード

👉 **[SSM DRMGL APK をダウンロード（v0.90 初回テストリリース）](https://github.com/maoh3/SSM_DRMGL_DOC/releases/download/SSM_DRMGL_0090_1st_testr-release/SSM_DRMGL_00.90_testrelease.apk)**


リリースページ  
https://github.com/maoh3/SSM_DRMGL_DOC/releases/tag/SSM_DRMGL_0090_1st_testr-release

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
