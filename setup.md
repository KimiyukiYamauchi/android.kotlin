# 目次

- [Android Studioのインストール](#android-studioのインストール)
  - [Snap を使う](#snap-を使う)

---

## Android Studioのインストール

### Snap を使う

#### 1. Snap が入っているか確認

Ubuntu では通常、最初から入っています。

```bash
snap version
```

エラーが出なければ OK です。

---

#### 2. Android Studio をインストール

```bash
sudo snap install android-studio --classic
```

- --classic は必須（SDK などにアクセスするため）
- 数分かかる場合があります

#### 3. 起動方法

GUIから

- アプリ一覧 → Android Studio

ターミナルから

```bash
android-studio
```

#### 4. 初回起動時の設定

初回起動時に以下が表示されます：

- ✅ Import Android Studio Settings?  
  → 初めてなら Do not import settings
- ✅ Setup Wizard  
  → Standard を選択
- ✅ SDK / Emulator / Platform Tools  
  → そのままインストールで OK

#### 5. 必須ツールの追加

##### ① JDK（通常は内蔵されているので不要）

Android Studio には JetBrains Runtime (JDK) が含まれています。  
👉 基本的に別途インストール不要

##### ② KVM（エミュレータ高速化・重要）⚠️

```bash
sudo apt update
sudo apt install qemu-kvm libvirt-daemon-system libvirt-clients bridge-utils
sudo usermod -aG kvm $USER
sudo usermod -aG libvirt $USER
```

##### ③ 仮想化が有効か確認

```bash
kvm-ok
```

`KVM acceleration can be used` と出れば OK 👍

#### よくあるトラブル

##### ❌ Emulator が起動しない

- BIOS / UEFI で Virtualization (VT-x / AMD-V) を有効にする
- KVM 設定後、再起動していない

##### ❌ adb が認識されない

```bash
sudo apt install android-sdk-platform-tools
```

#### おすすめ設定

- Settings → Editor → Font  
  → JetBrains Mono / 14–16pt
- Settings → Plugins  
  → Kotlin / Material Theme UI
- SDK Manager  
  → 最新 API + 1つ前の API を入れておく
