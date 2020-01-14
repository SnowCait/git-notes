# Trouble Shooting

## git clone

### agent returned different signature type ssh-rsa

#### エラー
```
PS> git clone git@github.com:SnowCait/example.git
warning: agent returned different signature type ssh-rsa (expected rsa-sha2-512)
...
fatal: the remote end hung up unexpectedly 9.64 GiB | 9.27 MiB/s
fatal: early EOF
fatal: index-pack failed
```

#### 環境
```powershell
PS> Get-WmiObject Win32_OperatingSystem | Select-Object Version
10.0.18363
PS> ssh -V
OpenSSH_for_Windows_7.7p1, LibreSSL 2.6.5
```

#### 解決策
[SSH - ssh_agentを使用すると、署名タイプが違うとエラー｜teratail](https://teratail.com/questions/210616)  

1. [設定] > [アプリ] > [アプリと機能] > [オプション機能の管理] から OpenSSH クライアントをアンインストール
2. OpenSSH >= 8.0 をインストール（管理者権限の PowerShell で実行）（別ディレクトリにインストールされるのでインストールとアンインストールは前後しても大丈夫そう）
```powershell
choco install -y openssh
```
3. この状態だとエラー
```powershell
PS> git clone git@github.com:SnowCait/example.git
error: cannot spawn C:\Windows\System32\OpenSSH\ssh.exe: No such file or directory
fatal: unable to fork
```
4. 環境変数 `GIT_SSH` に `C:\Program Files\OpenSSH-Win64\ssh.exe` を設定する
（プリインストールの ssh を使っていた場合は `C:\Windows\System32\OpenSSH\ssh.exe` を設定しているはず）
