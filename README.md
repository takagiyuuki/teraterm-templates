English | [日本語](README.ja.md)

<h1 align="center">
  teraterm-templates
</h1>

This is a macro for the remote log-on client TeraTerm that allows you to connect to a target server via SSH and execute commands. For more information about TeraTerm, please visit the following sites:

- [Tera Term Home Page](https://ttssh2.osdn.jp/#Development)
- [MACRO for Tera Term (Japanese)](https://ttssh2.osdn.jp/manual/4/ja/macro/)

## Usage

1. **Download the repository**

```bash
git clone https://github.com/takagiyuuki/teraterm-templates.git
```

2. **Register server information**

Edit `conf/conf.ttl` to register the server information:

```ini
hostnamestr     = '' ; server's hostname
ipaddressstr    = '' ; server's IP address
portstr         = '' ; server's SSH port number (default: 22)
userstr         = '' ; server's SSH login user
pswdstr         = '' ; server's SSH login password
sshkeystr       = '' ; server's SSH private key file (default: keys\id_rsa)
```

3. **Specify the commands to be executed in `cmd/cmd.txt`**

By default, the following commands are listed. Remove or add commands as needed:

```bash
date
hostname
whoami
echo "hallo. World"
```

4. **Choose the login method** (Password authentication / Public key authentication)

- For password authentication, edit `main.ttl` and uncomment `sshlogin = 'cmd\login-pswd.ttl'`
- For public key authentication, uncomment `sshlogin = 'cmd\login-keys.ttl'` and save the private key in the `keys\` directory

```ini
; Login 
; sshlogin = 'cmd\login-pswd.ttl'    ; password authentication
; sshlogin = 'cmd\login-keys.ttl'    ; public key authentication
```

5. **Execute `main.ttl`**

In the command prompt, execute the following command or double-click on `main.ttl`:

```batch
cd ~\teraterm-template
.\main.ttl
```