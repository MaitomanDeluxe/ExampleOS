# 仮想ターミナルエミュレータ (HTML Only)

このプロジェクトは、**コマンドプロンプト (cmd.exe)**、**PowerShell**, および **Linux (Ubuntu) ターミナル** の機能をHTMLとJavaScriptのみで再現したものです。ブラウザ上で動作し、OS不要・インストール不要で使用できます。

## https://maitomandeluxe.github.io/HTML-Terminal-Emulator/

## 🔧 構成ファイル一覧

| ファイル名       | 説明                           |
|------------------|--------------------------------|
| `index.html`     | ターミナル選択画面             |
| `cmd.html`       | コマンドプロンプトのエミュレータ |
| `shell.html`     | PowerShellのエミュレータ        |
| `linux.html`     | Ubuntu風Linuxターミナル         |

## 🚀 使用方法

### 1. 起動方法

1. `index.html` をブラウザで開く。
2. 表示されるボタンから、起動したいターミナル（CMD / PowerShell / Linux）を選択。

### 2. 各ターミナルの機能

---

### 🖥 Cmd.exe (`cmd.html`)

- サポートコマンド: `help`, `cd`, `dir`, `mkdir`, `rmdir`, `echo`, `cls`, `exit`, `type`
- 仮想ファイルシステム対応（`C:\Users\...` 構造）
- ユーザー名部分はローカルIPアドレスに自動置換
- `exit` でタブを閉じる（window.close）

---

### ⚡ PowerShell (`shell.html`)

- 実装コマンド：
  - `Get-Help`, `Get-Command`, `Get-Member`
  - `Get-ChildItem`, `Set-Location`, `Clear-Host`, `Get-Process`, `Exit`
  - `Get/Set/Add/Remove-Content`, `Start/Stop-Service`, `Get-Service`, etc.
- 入力補完（Tabキー）：
  - 入力途中例：`Ge` → `Get-Help` → `Get-Command` → `Get-Member`（ループ補完）
  - 自動で正しい大文字形式に変換（例：`get-help` → `Get-Help`）
- 入力中のコマンドが有効でない場合は赤く表示
- IPアドレスがプロンプト（`PS C:\Users\<IP>>`）に表示

---

### 🐧 Linuxターミナル (`linux.html`)

- 実装コマンド：`ls`, `pwd`, `cd`, `echo`, `clear`, `exit`
- 入力履歴ナビゲーション：↑ ↓
- 入力補完（Tabキー）：例 `l` → `ls`
- 入力エラー時に赤色で警告
- ユーザー名・ホスト名としてIPアドレスを使用（例：`127.0.0.1@ubuntu:~$`）

---

## 🌐 特記事項

- すべてのターミナルはJavaScriptのみで動作しており、サーバーやNode.js不要。
- `window.close()` によるタブ閉鎖は、一部ブラウザで制限されることがあります（ユーザー操作による起動でのみ許可される）。
- IPアドレス取得には `https://api.ipify.org` を使用しています（外部通信あり）。

---

## 📁 ローカルでの使用方法

1. このプロジェクトをローカルにダウンロードまたはクローン。
2. `index.html` をダブルクリックまたはブラウザで開く。

```bash
git clone https://github.com/your-name/virtual-terminal
cd virtual-terminal
start index.html
