
## 概要
- ITS社内に設置されている、デスクトップPC上に構築されている、VMWareにSelf-hosted Runnerを構築できるか検証
- 実装・作業ログを記載

## 作業ログ
1. VMの34環境で作業を行う。
2. `192.168.80.30`で34環境を起動
3. 34環境にSSH接続する（VSCode経由）
4. ターミナルで操作
```
# GitHub OrganizationのSettings＞Acitons＞RunnersにLinux用のセルフホストランナーの設定方法の記載がある
# https://github.com/organizations/mamiya-its/settings/actions/runners/new?arch=x64&os=linux

```