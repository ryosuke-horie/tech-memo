
## 目的

Chuumoにおいて、外部からのアクセスに対する一意なキーをヘッダーとして追加するため、CloudFront Server-timingヘッダーの検証を行う。

[Server-Timing ヘッダー](https://docs.aws.amazon.com/ja_jp/AmazonCloudFront/latest/DeveloperGuide/understanding-response-headers-policies.html#server-timing-header)
- Cloudfrontおよびオリジンの動作とパフォーマンスに関するインサイトを得るのに役立つメトリクスの表示を可能にする。
	- 例えばキャッシュヒットを処理したキャッシュレイヤを確認するなど
- レスポンスヘッダぽりし