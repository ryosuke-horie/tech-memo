
## 概要
- Github selfhost-runnerを利用するためにOSSのterrafrom-aws-github-runnerを利用する
- Terraformの実行環境をローカルに立ち上げる

## 1. OSSリポジトリのClone
https://github.com/philips-labs/terraform-aws-github-runner

- forkだとプライベートリポジトリに変更できなかったためClone

## 2. Terraformのインストール
- WSL2の中にインストールする
- [公式ダウンロードページ](https://developer.hashicorp.com/terraform/install?product_intent=terraform)
	- LinuxのUbuntuのコマンドを実行

## 3. セットアップガイドに従う
https://philips-labs.github.io/terraform-aws-github-runner/getting-started/
1. 組織用のGithub Appを作成
2. terraform モジュールのセットアップ
	1. https://github.com/philips-labs/terraform-aws-github-runner/releases
			上記からLambdaのZipファイルをダウンロード
			`modules/download-lambda`に保存する
	2. 変数を調整する
		1. lambda用のZipのパスとGithub Appsの部分