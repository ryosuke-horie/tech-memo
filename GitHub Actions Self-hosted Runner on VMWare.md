
## 概要
- ITS社内に設置されている、デスクトップPC上に構築されている、VMWareにSelf-hosted Runnerを構築できるか検証
- 実装・作業ログを記載

## 作業ログ
1. VMの34環境で作業を行う。
2. `192.168.80.30`で34環境を起動
3. 34環境にSSH接続する（VSCode経由）
4. ターミナルで操作 ダウンロード
```
# GitHub OrganizationのSettings＞Acitons＞RunnersにLinux用のセルフホストランナーの設定方法の記載がある
# https://github.com/organizations/mamiya-its/settings/actions/runners/new?arch=x64&os=linux
# Create a folder  
$ mkdir actions-runner && cd actions-runner

# Download the latest runner package  
$ curl -o actions-runner-linux-x64-2.319.1.tar.gz -L https://github.com/actions/runner/releases/download/v2.319.1/actions-runner-linux-x64-2.319.1.tar.gz

# Optional: Validate the hash  
$ echo "3f6efb7488a183e291fc2c62876e14c9ee732864173734facc85a1bfb1744464 actions-runner-linux-x64-2.319.1.tar.gz" | shasum -a 256 -c

# Extract the installer  
$ tar xzf ./actions-runner-linux-x64-2.319.1.tar.gz
```
5. ターミナルで操作 設定
```
# 下のコマンドを実行するために依存関係のダウンロードのため以下が必要だった。
sudo ./bin/installdependencies.sh

# Create the runner and start the configuration experience  
$ ./config.sh --url https://github.com/mamiya-its --token APHWAFVBAD6A7PR2BANOJKLGY7S5Y

# Last step, run it!  
$ ./run.sh
```
6. GitHubのRunnersとして登録されていることを確認
