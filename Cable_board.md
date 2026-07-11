## Cable Information

[日本語セクションはこちら](#日本語)

### Using OpenPort 1.3
When connecting via SSM2, the **Tactrix OpenPort 1.3 (compatible)** cable works without any special configuration.

However, future support for **ISO9141 / KWP2000** will require the use of the **DTR signal** for 5‑baud initialization.
Some “compatible” OpenPort 1.3 clones may not support this behavior.


(board schema)

<img width="473" height="478" alt="image" src="https://github.com/user-attachments/assets/2c96d275-66f2-4cc8-9402-8b5d2d68303f" />


SUBARU Car need 12V pull up line i add OBD 16pin(BATT), but 8pin(ACC) is useful.

<img width="1073" height="592" alt="image" src="https://github.com/user-attachments/assets/40893532-9deb-44d4-91a7-5f7a516e7703" />


### About FTDI Cables
Many inexpensive FTDI cables sold on Amazon may use **non‑genuine or third‑party FTDI‑compatible chipsets**.
These devices often cannot be configured with **MPROG**, and may not support:

- TXD invert mode
- Custom baud rate settings
- DTR/RTS control

For reliable operation, please choose a cable that is confirmed to use a **genuine FTDI chipset**.

### Recommended FTDI Cable (Genuine FTDI)
OK: https://akizukidenshi.com/catalog/g/g106693/

Example of a cable that may use a third‑party chipset:  
NG: https://www.amazon.co.jp/dp/B085NM1M48

### Subaru K‑Line Pull‑Up Requirement
Subaru ECUs require a **12V pull‑up** on the K‑Line.

I added the pull‑up from:
- OBD pin **16 (BATT)**  
  or
- OBD pin **8 (ACC)** — also works well

**Note:**  
OBD pin **8 (ACC)** is an **optional Subaru-specific line** and may not be present on all vehicles.  
If you plan to use pin 8, please check your vehicle’s wiring before connecting.

### MPROG (FTDI Device Configuration)
The following MPROG settings are required:

- **TXD Invert** → Enabled
- **Baud Rate** → Custom
- **DTR/RTS** → Enabled (for ISO/KWP experiments)

(See screenshots below.)

<img width="918" height="725" alt="FTDI_USB_Setting001" src="https://github.com/user-attachments/assets/c655eaf4-b2d0-412a-8538-0d12eba966f1" />

<img width="920" height="722" alt="FTDI_USB_Setting002" src="https://github.com/user-attachments/assets/760765fb-e85f-4b68-ab80-49c80a9a4d68" />

<img width="916" height="726" alt="FTDI_USB_Setting003" src="https://github.com/user-attachments/assets/aa56fb9f-0c5f-4e50-b29d-f95376b78004" />

<img width="915" height="725" alt="FTDI_USB_Setting004" src="https://github.com/user-attachments/assets/2b2828fc-d809-476e-87f2-495d0e9f076c" />

**Important:** TXD invert mode must be enabled.
<img width="918" height="727" alt="FTDI_USB_Setting005" src="https://github.com/user-attachments/assets/29898e4b-4275-4481-a70f-0b5c263682f2" />

<img width="920" height="726" alt="FTDI_USB_Setting006" src="https://github.com/user-attachments/assets/7535d7f1-58dc-462f-bc90-f7033e3e616c" />

## 日本語

## ケーブル情報（日本語）

### OpenPort 1.3 について
SSM2 接続時は **Tactrix OpenPort 1.3（互換含む）** が特別な設定なしで使用できます。

ただし、将来的に対応予定の **ISO9141 / KWP2000** では  
5Baud 初期化に **DTR 信号**を使用する必要があります。  
そのため、一部の「OpenPort 1.3 互換品」では正しく動作しない可能性があります。

### FTDI ケーブルについて
Amazon などで販売されている低価格の FTDI ケーブルの中には、  
**正規品ではない、または FTDI 互換チップを使用している可能性がある製品**があります。

これらのケーブルは **MPROG で設定できない**場合があり、  
以下の機能が使えない可能性があります：

- TXD インバート設定
- カスタムボーレート設定
- DTR / RTS 制御

安定した動作のため、**正規の FTDI チップを使用したケーブル**を選ぶことを推奨します。

### 推奨 FTDI ケーブル（正規品）
OK: https://akizukidenshi.com/catalog/g/g106693/

正規品ではない、またはサードパーティ製チップを使用している可能性がある例：  
NG: https://www.amazon.co.jp/dp/B085NM1M48

### Subaru の K-Line プルアップについて
Subaru の ECU は **K-Line に 12V プルアップ**が必要です。

私は以下の OBD ピンからプルアップを追加しました：

- OBD ピン **16（BATT）**  
  または
- OBD ピン **8（ACC）**

**注意：**  
OBD ピン **8（ACC）** は **Subaru 独自のオプション配線**であり、  
すべての車種に存在するわけではありません。  
使用する場合は、**必ず車両側の配線を確認してから**接続してください。

### MPROG（FTDI デバイス設定）
以下の MPROG 設定が必要です：

- **TXD Invert** → 有効
- **Baud Rate** → カスタム
- **DTR / RTS** → 有効（ISO/KWP 実験用）

（README では説明簡潔化のためスクリーンショットを省略）
