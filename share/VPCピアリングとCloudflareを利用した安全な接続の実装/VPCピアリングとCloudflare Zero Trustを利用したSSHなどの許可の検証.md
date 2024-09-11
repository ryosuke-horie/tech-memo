
## 検証内容
- AWSアカウント間のVPCピアリングを行う
- リクエスタのVPC内にCloudflaredのインスタンスを起動
- Cloudflare Tunnelを利用して、Cloudflare WARPでZeroTrustにログインしたPCからVPCピアリングのアクセプタのEC2にSSH接続を成功させる

## 検証時に行った操作
1. 適当なAWSアカウントに対してVPCを新規作成する。
	- 