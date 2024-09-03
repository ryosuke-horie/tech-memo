
## 概要
terraform-aws-github-runnerを利用してGitHubセルフホストランナーを構築すると、RunnerはAmazon LinuxのEC2で作成される。
立ち上がりに時間がかかるのと、プロジェクトで必要な依存関係のインストールの時間を省き、CIのパフォーマンス改善とコスト削減を行う。

## 