

## 前提
- Node.jsを知らなくていいというわけではない
	- 最速でCDKを扱うAWSインフラ構築に携わるために必須の知識に絞っただけです
	- 各自Node.jsについても学習しておいてください。

## npmの基礎
Node.jsのパッケージマネージャです。
CDK自体がパッケージですので知らないとインストールできません。

Pythonでいうpipに相当するものです。

Node.jsをインストールしたときにnpmもインストールされます。
git bashなどで以下のコマンドを実行してください
```bash
# version確認
npm -v
```

### パッケージ管理について
2パターン存在します。
- ローカルインストール
	- プロジェクトのディレクトリ内に`node_modules`ディレクトリを作成し、そこにパッケージをインストールします。
	- 他のプロジェクトを汚染しないため、基本的にはこちらを利用します。
- グローバルインストール
	- OSにパッケージをインストールします
	- どのプロジェクトでも利用可能になりますが、移行時に同一の環境になる保証がなくなります。
```bash
# ローカルインストール
npm install <パッケージ名>
# グローバルインストール
npm install -g <パッケージ名>
```

## package.json
パッケージ情報を管理しているJSONファイルです。
中に使われているパッケージ名が記載されています。

```json
{
  "name": "infra",
  "version": "0.1.0",
  "bin": {
    "cdk": "bin/cdk.js"
  },
  "scripts": {
    "build": "tsc",
    "cdk": "cdk",
    "lint": "npx @biomejs/biome check",
    "format": "npx @biomejs/biome check --fix",
    "snapshot": "npx vitest ./test/cdk-cheerpay-dev-snapshot.test.ts --run",
    "snapshot:update": "npx vitest ./test/cdk-cheerpay-dev-snapshot.test.ts --u"
  },
  "devDependencies": {
    "@biomejs/biome": "1.8.3",
    "@types/aws-lambda": "^8.10.145",
    "@types/node": "22.5.4",
    "aws-cdk": "2.155.0",
    "ts-node": "^10.9.2",
    "typescript": "~5.5.3",
    "vitest": "^2.0.5"
  },
  "dependencies": {
    "aws-cdk-lib": "2.155.0",
    "constructs": "^10.0.0",
    "source-map-support": "^0.5.21"
  }
}
```

### scriptsについて
package.jsonのscriptのオブジェクトに
`コマンド名: 実行コマンド`のように記載することで頻繁に利用するコマンドをエイリアスのように扱うことが可能です。
コードのフォーマットや自動テストなどを定義し、
```
npm run <コマンド名>
```
で実行できます。

### devDependenciesについて
プロジェクトにインストールしているパッケージが記載されます。
こちらは開発用の依存関係です。つまり本番環境では利用しないが開発時には必要になるパッケージです。
直接編集することもできますが、基本的にはライブラリのインストール時に自動的に更新されます。
例えば
```bash
npm install --save-dev aws-cdk
```
とコマンドを打てばaws-cdkのパッケージを見つけてインストールし、追記されます。
### dependenciesについて
本番環境でも利用するパッケージが記載されます。
それ以外はdevDependenciesと同じです。

## package-lock.jsonについて
パッケージの詳細なバージョンを管理するために利用されます。
package.jsonでは`"aws-cdk": "2.155.0"`の記載がありますが、