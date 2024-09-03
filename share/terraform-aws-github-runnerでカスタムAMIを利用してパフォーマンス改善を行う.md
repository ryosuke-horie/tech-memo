
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
