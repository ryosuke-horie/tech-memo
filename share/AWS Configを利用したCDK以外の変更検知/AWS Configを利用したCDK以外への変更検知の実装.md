
## 出発点
- CDKでAWSインフラを管理する
- 基本的にほぼすべてのリソースをCDKで管理するため、手動やAPIを利用して変更が加えられたときに検知したい。
- AWS Configを利用すれば検出できそう

## AWS Configの基礎知識
[AWS Config の定期的な記録を使用した設定項目の検出](https://aws.amazon.com/jp/blogs/news/how-to-record-resource-configuration-changes-periodically-with-aws-config/)
- AWSアカウント内の設定変更を追跡できる
- 設定レコーダーを利用してリソースの編国を検出し設定項目として追跡する
- 定期的な記録を利用することで、コスト効率高く実装可能
	- 継続的な記録も可能だが、