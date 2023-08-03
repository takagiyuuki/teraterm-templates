[English] | 日本語(README.md)

# teraterm-templates

リモートログオンクライアント TeraTerm のマクロです。
対象のサーバーにSSH接続し、あらかじめ用意したコマンドを実行するマクロです。
TeraTermの詳細は以下のサイトで確認してください。

## 使い方

1. リポジトリをダウンロードする
2. サーバー情報を登録する
以下のファイルを編集してサーバー情報を登録する
`conf/conf.ttl`

```ini
hostnamestr     = '' # サーバーのホスト名を入力
ipaddressstr    = '' # サーバーのIPアドレスを入力 
portstr         = '' # SSH接続時のポートを入力（既定値は22）
userstr         = '' # SSH接続時のログインユーザーを入力
pswdstr         = '' # SSH接続時のログインパスワード、またはSSH秘密鍵認証のパスコードを入力（不要な場合は入力しない）
supswdstr       = '' # 
sshkeystr       = '' # SSH秘密鍵のファイルパス デフォルトはkeys\id_rsa
```

1. 秘密鍵認証をする場合、以下のディレクトリに秘密鍵を保存する
`keys\`

1. 実行するコマンドを以下のファイルに記載する
`cmd/cmd.txt`
デフォルトでは以下のコマンドが記述されています。

`cmd/cmd.txt`

```bash
date
hostname
whoami
echo "hallo. World"
```

### ログイン方法を選択する

パスワード認証、公開鍵認証どちらか選択する

パスワード認証の場合、`sshlogin = 'cmd\login-pswd.ttl'`のコメントアウトを外す
公開鍵認証の場合、`sshlogin = 'cmd\login-keys.ttl'`のコメントアウトを外す

`main.ttl`

```ini
; Login 
; sshlogin = 'cmd\login-pswd.ttl'    ; password authentication
; sshlogin = 'cmd\login-keys.ttl'    ; public key authentication

```

### `main.ttl`を実行する

cmand promptで以下のコマンドを実行、または「main.ttl」をダブルクリックする

```batch
cd ~\teraterm-template
.\main.ttl
```
