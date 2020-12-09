#SSH 接続公開キー認証方式設定のメモ

last-update 2020-12-09
WT

```
# 以下 wt の部分をユーザー名に書き換えて

# サーバーへ接続(biolab, biolab5のwifiから)
ssh wt@cacao.bioinfo.ttck.keio.ac.jp

# 鍵の生成、パスワードとしてににの
ssh-keygen -t rsa -b 4096

# Enter passphraseとでたら、好きなパスワードを入力
*******

# 公開鍵展開
cd .ssh
cat ./id_rsa.pub >> ./authorized_keys
chmod 600 ./authorized_keys

# サーバーはログアウト
logout

# 秘密鍵をMacにダウンロード
scp wt@cacao.bioinfo.ttck.keio.ac.jp:~/.ssh/id_rsa ~/.ssh/

# biolab, biolab5のwifiから接続を確認
ssh wt@cacao.bioinfo.ttck.keio.ac.jp

# パスワードを求められるので、入力
*******

# パスフレーズを省略する方法

# configファイルに書き込む
echo -e "Host *\nUseKeychain yes" >> ~/.ssh/config

# evalの起動
eval `ssh-agent`
ssh-add -K ~/.ssh/id_rsa

# パスフレーズを入力
******* 

# .bashrcに書き込む
echo 'eval `ssh-agent`' >> ~/.bashrc
```
