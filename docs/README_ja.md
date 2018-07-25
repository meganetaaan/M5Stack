# M5Stackライブラリ

[英語](../README.md)

## 使い方

### USBドライバのインストール

- [SiLabs CP2104 Driverをダウンロードします](https://www.silabs.com/products/development-tools/software/usb-to-uart-bridge-vcp-drivers)。
Windows 10 Universal driver (v10.1.1)は使わないで下さい。
誤ってUniversal版を使うと、Windowsアップデートの度にWindowsは新しい、互換性のないドライバーを使ってしまうため、定期的に手動で6.7.1に戻す必要があります。

(Note: プログラムをアップロードできない場合は下記のレガシーなv4ドライバーを試してください。この際v5ドライバーはアンインストールする必要があります。また低いボーレートを試してください。)
- [書き込み処理で再起動する問題が起きる場合、[Silabs CP210X v10 Driver Universal binary for win 10](https://www.silabs.com/documents/public/software/CP210x_Universal_Windows_Driver.zip)をダウンロードします。
ドライバーを過去にインストールしていれば再インストールの必要はなく、オンザフライで更新する必要があります。

### ESP32 Arduino Coreのインストール

- ArduinoIDEを使う場合
  + [Windows](docs/arduino-ide/windows.md)
  + [Mac](docs/arduino-ide/mac.md)
  + [Debian/Ubuntu Linux](docs/arduino-ide/debian_ubuntu.md)
  + [Fedora](docs/arduino-ide/fedora.md)
  + [openSUSE](docs/arduino-ide/opensuse.md)
- [PlatformIOを使う場合](docs/platformio.md)
- [makeコマンドでビルドする場合](docs/make.md)
- [ESP-IDFコンポーネントとして使う場合](docs/esp-idf_component.md)

### ライブラリのダウンロード

#### Arduino IDE Library Managerを使う場合

1. メニューから ```Sketch``` -> ```Include Library``` -> ```Manage Libraries...``` を選択します
2. 検索ボックスに ```m5stack``` と入力します
3. 検索結果からM5Stackライブラリの行を選択します
4. ```Install``` ボタンをクリックしてライブラリをインストールします
5. メニューから "File-> Examples" をクリックします。"M5Stack->" 配下にいくつかのサンプルプログラムがあります

#### Git を使う場合 (Windows)

1. [git](https://gitforwindows.org/)をインストールします
2. コマンドプロンプトから下記のコマンドを実行します
```sh
c:
cd %USERPROFILE%\documents\libraries
git clone https://github.com/m5stack/M5Stack.git
```

#### Git を使う場合 (Windows以外のほとんどの環境)

下記のコマンドを実行します
```sh
cd ~/Documents/Arduino/libraries/
git clone https://github.com/m5stack/M5Stack.git
```

## API

[API（英語）](https://github.com/m5stack/M5Stack/blob/master/src/M5Stack.h#L19)を参照してください。

## サンプルプログラム

[examples](examples)フォルダを参照してください。

## ハードウェア

[回路図（PDF）](https://github.com/m5stack/M5-hardware/blob/master/M5_Core_SCH(20171206).pdf)を参照してください。

### Pinout

ペリフェラル | ESP32 
---|---
ILI9341 RST | GPIO33 
ILI9341 DC | GPIO27 
ILI9341 CS | GPIO14
ILI9341 MOSI | GPIO23
ILI9341 CLK | GPIO18
ILI9341 LIGHT | GPIO32
TFCARD MOSI | GPIO23
TFCARD MISO | GPIO19
TFCARD CLK | GPIO18
TFCARD CS | GPIO4
BUTTON A | GPIO39
BUTTON B | GPIO38
BUTTON C | GPIO37
SPEAKER | GPIO25
MPU9250 SDA | GPIO21
MPU9250 SCL | GPIO22
GROVE SDA | GPIO21
GROVE SCL | GPIO22

### LoRaモジュール

ペリフェラル | ESP32 | RA-02 | 備考
---|---|---|---
MOSI     | GPIO23 | MOSI | TFCARDと共有
MISO     | GPIO19 | MISO | TFCARDと共有
SCK      | GPIO18 | SCK | TFCARDと共有
RFM95_CS | GPIO5 | NSS | M5.Begin()の前にプルアップする
RFM95_RST | GPIO36 | RST | ラベルが誤ってGPIO26になっている箇所がある
RFM95_INT | GPIO26 | DIO0 | ラベルが誤ってGPIO36になっている箇所がある

### M-BUS

![image](M-BUS.jpg)

### Awesome

[英語版READMEのAwesomeセクション](../README.md#Awesome)を参照してください。
