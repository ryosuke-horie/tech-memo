
## 概要
terraform-aws-github-runnerを利用してGitHubセルフホストランナーを構築すると、RunnerはAmazon LinuxのEC2で作成される。
立ち上がりに時間がかかるのと、プロジェクトで必要な依存関係のインストールの時間を省き、CIのパフォーマンス改善とコスト削減を行う。

## カスタムAMIの作成
### 事前準備：packerのインストール
WSL2 Ubuntuでダウンロード
https://developer.hashicorp.com/packer/install
```
echo "deb [signed-by=/usr/share/keyrings/hashicorp-archive-keyring.gpg] https://apt.releases.hashicorp.com $(lsb_release -cs) main" | sudo tee /etc/apt/sources.list.d/hashicorp.list

# 確認
packer --version
# >Packer v1.11.2
```
### packerの構文でUbuntuでGitHub セルフホストランナーのセットアップ
1. terraform-aws-github-runnerのubuntuのサンプルをベースにプロジェクトに合わせてプロジェクトに必要なphp, composer, nodejsのセットアップを追加する。
2. packerをプロジェクト用に初期化
```
# packerの設定ファイルを置いたディレクトリでinitする
packer init github_agent.ubuntu.pkr.hcl
```
3. バリデーション
```
packer validate github_agent.ubuntu.pkr.hcl 
```
4. イメージ作成
```
packer build github_agent.ubuntu.pkr.hcl
```

### カスタムAMIを利用できるようにvariables.tfを修正
- `ami_filter`のnameを指定するように追加し自作したamiの名前を指定
- `runner_run_as`がデフォルトでは`ec2-user`になっている。Ubuntuの場合は`ubuntu`