# Git for Windows 2.54.0 インストール手順（VSCode利用向け）

VSCodeでGit/GitHubを使うための、素早く進めるための推奨設定です。  
基本方針は **「VSCodeで使いやすく、Windowsで安全・標準的に使える設定」** です。

---

## 事前方針

- VSCodeでGitを使う
- GitHubとの連携も想定
- 初心者〜通常利用向け
- 特別なチームルールがない前提

---

## 1. Select Components

画面名：

```text
Select Components
```

### 推奨設定

| 項目 | 設定 | 理由 |
|---|---:|---|
| Additional icons | 任意 | デスクトップアイコンが不要ならOFF |
| On the Desktop | OFF推奨 | VSCode利用なら基本不要 |
| Windows Explorer integration | ON | 右クリックメニューからGit Bashを開ける |
| Open Git Bash here | ON | フォルダ上でGit Bashを開けて便利 |
| Open Git GUI here | OFFでOK | VSCode中心ならあまり使わない |
| Git LFS | ON | 大きいファイルを扱う可能性に備えられる |
| Associate .git* configuration files with the default text editor | ON | Git設定ファイルをエディタで開きやすくなる |
| Associate .sh files to be run with Bash | ON | `.sh` ファイルをBashで実行できる |
| Check daily for Git for Windows updates | OFFでOK | 手動更新で十分 |
| Add a Git Bash Profile to Windows Terminal | 任意 | Windows Terminalを使うならON |
| Scalar | OFFでOK | 大規模リポジトリ向けなので通常は不要 |

### 迷ったら

```text
Windows Explorer integration: ON
Open Git Bash here: ON
Git LFS: ON
Associate .git* files: ON
Associate .sh files: ON
Scalar: OFF
```

設定後、**Next** を押します。

---

## 2. Choosing the default editor used by Git

画面名：

```text
Choosing the default editor used by Git
```

### 選ぶもの

```text
Use Visual Studio Code as Git's default editor
```

### 理由

Gitのコミットメッセージ編集などでVSCodeを使えるようになります。  
Vimは慣れていないと操作が難しいため、VSCode利用なら避けるのがおすすめです。

設定後、**Next** を押します。

### VSCodeが選択肢に出ない場合

いったんそのまま進めても、後で以下のコマンドで設定できます。

```bash
git config --global core.editor "code --wait"
```

---

## 3. Adjusting the name of the initial branch in new repositories

画面名：

```text
Adjusting the name of the initial branch in new repositories
```

### 選ぶもの

```text
Override the default branch name for new repositories
```

入力欄：

```text
main
```

### 理由

最近のGitHubやVSCodeでは、初期ブランチ名に `main` を使うのが一般的です。  
`master` よりも `main` にしておくと、GitHubとの連携で迷いにくくなります。

設定後、**Next** を押します。

---

## 4. Adjusting your PATH environment

画面名：

```text
Adjusting your PATH environment
```

### 選ぶもの

```text
Git from the command line and also from 3rd-party software
```

### 理由

VSCode、PowerShell、コマンドプロンプト、Git Bashから `git` コマンドを使えるようになります。  
VSCodeでGitを使うならこの設定が最も無難です。

設定後、**Next** を押します。

---

## 5. Choosing the SSH executable

画面名：

```text
Choosing the SSH executable
```

### 選ぶもの

```text
Use bundled OpenSSH
```

### 理由

Gitに付属しているOpenSSHを使う設定です。  
特別なSSH設定をしていない通常利用では、この設定で問題ありません。

設定後、**Next** を押します。

---

## 6. Choosing HTTPS transport backend

画面名：

```text
Choosing HTTPS transport backend
```

### 選ぶもの

```text
Use the native Windows Secure Channel library
```

### 理由

Windowsの証明書ストアを使ってHTTPS接続します。  
VSCode、GitHub、通常のGit利用では扱いやすい設定です。

設定後、**Next** を押します。

---

## 7. Configuring the line ending conversions

画面名：

```text
Configuring the line ending conversions
```

### 選ぶもの

```text
Checkout Windows-style, commit Unix-style line endings
```

### 理由

Windowsでは扱いやすい改行にしつつ、Gitにコミットするときは一般的なUnix形式にそろえてくれます。  
VSCode + GitHub利用では無難な設定です。

設定後、**Next** を押します。

---

## 8. Configuring the terminal emulator to use with Git Bash

画面名：

```text
Configuring the terminal emulator to use with Git Bash
```

### 選ぶもの

```text
Use MinTTY (the default terminal of MSYS2)
```

### 理由

Git Bashを単体で開いたときに、見やすく使いやすいターミナルになります。  
VSCode内のターミナルとは別なので、このままで問題ありません。

設定後、**Next** を押します。

---

## 9. Choose the default behavior of `git pull`

画面名：

```text
Choose the default behavior of `git pull`
```

### 選ぶもの

```text
Fast-forward or merge
```

### 理由

初心者〜通常利用では一番無難です。  
`git pull` したとき、可能ならfast-forwardし、必要ならmerge commitを作成します。

設定後、**Next** を押します。

---

## 10. Choose a credential helper

画面名：

```text
Choose a credential helper
```

### 選ぶもの

```text
Git Credential Manager
```

### 理由

GitHubのログイン情報を安全に保存できます。  
VSCodeでGitHubにpush/pullするとき、毎回ログインしなくて済みます。

設定後、**Next** を押します。

---

## 11. Configuring extra options

画面名：

```text
Configuring extra options
```

### 推奨設定

| 項目 | 設定 | 理由 |
|---|---:|---|
| Enable file system caching | ON | Gitの動作が少し速くなる |
| Enable symbolic links | OFF | 通常利用では不要。権限まわりで面倒になることがある |

設定後、**Install** を押します。

---

## 最終チェックリスト

インストール時に、以下のようになっていればOKです。

```text
Default editor: Visual Studio Code
Initial branch name: main
PATH: Git from the command line and also from 3rd-party software
SSH: Use bundled OpenSSH
HTTPS backend: Use the native Windows Secure Channel library
Line endings: Checkout Windows-style, commit Unix-style line endings
Terminal emulator: Use MinTTY
git pull behavior: Fast-forward or merge
Credential helper: Git Credential Manager
File system caching: ON
Symbolic links: OFF
```

---

## インストール後の確認

インストールが終わったら、VSCodeのターミナル、PowerShell、またはGit Bashで以下を実行します。

```bash
git --version
```

例：

```text
git version 2.54.0.windows.1
```

のように表示されれば、Gitのインストールは成功です。

---

## 最初に設定しておくとよいGitユーザー情報

GitHubにコミットする予定がある場合は、最初に名前とメールアドレスを設定します。

```bash
git config --global user.name "あなたの名前"
git config --global user.email "あなたのメールアドレス"
```

確認：

```bash
git config --global --list
```

---

## VSCodeでGitを使うときの確認ポイント

1. VSCodeを開く
2. 左側の「Source Control」アイコンを開く
3. Gitリポジトリのフォルダを開く
4. 変更したファイルが表示されるか確認する
5. 必要に応じてGitHubにサインインする

---

## まとめ

VSCodeでGitを使うなら、基本的には以下の方針で選べば大丈夫です。

```text
VSCodeをエディタにする
mainブランチを使う
GitをVSCodeやPowerShellから使えるようにする
Git Credential Managerを使う
余計な大規模開発向け機能やシンボリックリンクはOFF
```
