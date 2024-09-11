
## 検証内容
- AWSアカウント間のVPCピアリングを行う
- リクエスタのVPC内にCloudflaredのインスタンスを起動
- Cloudflare Tunnelを利用して、Cloudflare WARPでZeroTrustにログインしたPCからVPCピアリングのアクセプタのEC2にSSH接続を成功させる

## 検証時に行った操作
1. 適当なAWSアカウントに対してVPCを新規作成する。
	- パブリックサブネット・ルートテーブルも同時に作成する
2. 新規作成したVPCのパブリックサブネットにAmazonLinux2023のEC2インスタンスを作成する
3. Cloudflare Zero trust＞Networks＞Tunnels
	1. cloudflaredを新規作成
	2. RedHat/64bitを指定してCloudflared構築用のコマンドをコピー
	3. EC2のプライベートIPv4アドレスを指定してトンネルを作成
4. EC2にインスタンスコネクトで接続しCloudflared構築用のコマンドを張り付け実行
5. Cloudflare Zero Trust＞Networks＞Tunnelsでトンネルの状態がHealtyになっていることを確認
6. VPCピアリングを構成
	1. 対象のVPCに対してリクエスト
	2. VPCピアリングのリクエストを承諾
7. リクエスタとアクセプタ両方のVPCのルートテーブルで反対側のVPCのCIDRをVPCピアリングを指定して設定を追加
8. 接続したいEC2やRDSのセキュリティグループがリクエスタのCIDRからポートを解放できｔ