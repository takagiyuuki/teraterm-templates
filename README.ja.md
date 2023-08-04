[English](README.md) | 日本語

<h1 align="center">
  teraterm-templates
</h1>

リモートログオンクライアント TeraTerm を利用し、対象のサーバーにSSH接続後コマンドを実行するマクロです。
TeraTermの詳細は以下のサイトで確認してください。

- [Tera Term Home Page](https://ttssh2.osdn.jp/#Development)
- [MACRO for Tera Term](https://ttssh2.osdn.jp/manual/4/ja/macro/)

## 使い方

1. **リポジトリをダウンロードする**

```bash
git clone https://github.com/takagiyuuki/teraterm-templates.git
```

2. **サーバー情報を登録する**

`conf/conf.ttl`を編集してサーバー情報を登録する

```ini
hostnamestr     = '' ; server's hostname
ipaddressstr    = '' ; server's ip address
portstr         = '' ; server's SSH port number(default: 22)
userstr         = '' ; server's SSH login user
pswdstr         = '' ; server's SSH login password
sshkeystr       = '' ; server's SSH pravate key file(default: keys\id_rsa)
```

3. **実行するコマンドを`cmd/cmd.txt`に記載する**

デフォルトでは以下のコマンドが記述されているので、適宜削除・追記する

```bash
date
hostname
whoami
echo "hallo. World"
```

4. **ログイン方法を選択する**

パスワード認証、公開鍵認証のどちらか選択する

- パスワード認証の場合、`sshlogin = 'cmd\login-pswd.ttl'`のコメントアウトを外す
- 公開鍵認証の場合、`sshlogin = 'cmd\login-keys.ttl'`のコメントアウトを外し、`keys\`に秘密鍵を保存する

```ini
; Login 
; sshlogin = 'cmd\login-pswd.ttl'    ; password authentication
; sshlogin = 'cmd\login-keys.ttl'    ; public key authentication
```

5. **`main.ttl`を実行する**

cmand promptで以下のコマンドを実行、または「main.ttl」をダブルクリックする

```batch
cd ~\teraterm-template
.\main.ttl
```
