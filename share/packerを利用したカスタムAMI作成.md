## WSL2 Ubuntuでダウンロード
https://developer.hashicorp.com/packer/install
```
echo "deb [signed-by=/usr/share/keyrings/hashicorp-archive-keyring.gpg] https://apt.releases.hashicorp.com $(lsb_release -cs) main" | sudo tee /etc/apt/sources.list.d/hashicorp.list

# 確認
packer --version
# >Packer v1.11.2
```

## packerの構文でUbuntuでGitHub セルフホストランナーのセットアップ
1. terraform-aws-github-runnerのubuntuのサンプルをベースにプロジェクトに合わせてphp, composer, nodejsのセットアップを追加する。
2. packerをプロジェクト用に初期化
```
# packerの設定ファイルを置いたディレクトリでinitする
packer init github_agent.ubuntu.pkr.hcl
```
3. バリデーション
```
packer validate github_agent.ubuntu.pkr.hcl 
```
4. 