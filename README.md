# ポートフォリオの技術スタック等の説明

## [teloppy.com](https://teloppy.com)

#### ・どのようなサービスか

テキストを入力すると、mp4・gif形式のオリジナル動画を生成できるサービス。アニメーションはhtml,css,jsにて作っているのでブラウザでの表示も可能。

#### ・技術スタック

・フロント-　Vue.js(Nuxt.js,Typescript)

・バックエンド - AWS Amplify(API Gateway,Lambda), AWS SAM(API Gateway,Lambda),Dynamodb

・インフラ - AWS(S3,Cloudfront,Route53)

・テスト - Jest

・CI/CD - Github Actions

#### ・その他補足

できるだけ、安価な構築が必要だったのでNuxtのSSGモード(Static Site Generation)にて静的フォルダを生成しS3に出力、Cloundfrontにて配信しています。バックエンドで必要な処理はLambda,API GatewayにてAPIサーバーを設置して対応しています。
Route53(DNS)が月200円程度かかっている程度で他はほとんど料金はかかっておりません。

また、動画生成のロジックとしてはフロント側で録画はできませんので、サーバー側でブラウザ(ヘッドレス)を立ち上げて録画しています。録画にはPlaywright(ブラウザ操作用ライブラリ)を使用しております。


## commenthub(現在、インフラを調整中)

#### ・どのようなサービスか

ユーザーが記事にコメントを行い、そのコメントがメインのコンテンツとなるサービス。ゲストユーザーでもコメント可能。Yahoo Newsをイメージして作成。

#### ・技術スタック

・フロント-　Vue.js(Nuxt.js,Typescript)

・バックエンド - AWS Amplify(API Gateway,Lambda,Dynamodb(Graphql),Cognito),Node.js(Express.js)

・インフラ - AWS(Fargate,ECS,ELB,Route53,Cloudfront),Docker

・テスト - なし

・CI/CD - なし

#### ・その他補足

１年ほど前に作ったものをポートフォリオとして調整したものです。OAuthによるログイン機能をつけていますが、現在では使用できません。本番環境で運用することは想定しない構築となっております。
実際に会員登録によるログインもできますが、ゲストユーザー用のアカウントも用意していますので、仕様を確認するのにご利用できます。

ゲストユーザー

メールアドレス - commenthub.testuser@gmail.com

パスワード - CommentHub2022


また、一度ログインしたらローカルストレージにてtokenを保存し、ブラウザを閉じても自動でログインされるようになっています。





## [skeizai.com](https://skeizai.com)

#### ・どのようなサイトか

経済学関連の記事を載せているブログサイト。

#### ・技術スタック

・フロント-　Vue.js(Nuxt.js,Typescript)

・バックエンド - Node.js(Express.js),MongoDB

・インフラ - AWS(S3,Cloudfront)

・テスト - なし

・CI/CD - なし

#### ・その他補足

元々、さくらのVPSにてDockerで環境を構築しNode.jsでSSRモードによる配信を行っていましたが、記事の更新をしなくなったことや、さくらのVPSを解約したことにより、SSGにて静的ファイルに出力して配信しています。
