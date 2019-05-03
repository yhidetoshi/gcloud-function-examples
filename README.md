# gcloud-function-examples

Google cloudのcloud-functionにGo1.11ランタイムでデプロイする


## natureRemoディレクトリのREADME
- やること
  - NatureRemoで取得したデータ(気温・湿度・照度)をMackerelにPostさせる。

- 開発環境
  - go: 1.12.4
  - goland
  - Mackerel(Freeプラン)

- 実行環境
  - cloud-function
    - go1.11
    - メモリ: 128MB
    - トリガー: Cloud Pub/Sub
    - 実行する関数: NatureRemo
    - Region: asia-northeast1

- デプロイ方法
  - gcloudコマンド
    - `$ cd ./natureRemo`
    - go.modを最初に生成する場合: `go mod init github.com/yhidetoshi/gcloud-function-examples/natureRemo`
    - `$ gcloud functions deploy natureRemo --entry-point NatureRemo --runtime go111 --trigger-resource <TOPIC> --memory 128 --trigger-event google.pubsub.topic.publish --project <PROJECTID> --region asia-northeast1 --set-env-vars MKRKEY=<MKRKEY>,REMOTOKEN=<REMOTOKEN>`

- 環境変数
  - MKRKEY: mackerel_api_keyをセット
  - REMOTOKEN: natureRemoトークン


## http-helloディレクトリのREADME
- `$ export GO111MODULE=on`

- `$ go mod init github.com/yhidetoshi/gcloud-function-examples/http-hello`

- `$ gcloud functions deploy Hello --entry-point Hello --runtime go111 --trigger-http --project <PROJECTID> --region asia-northeast1`

--> Endpointが出力される

- `$ curl https://asia-northeast1-<GCP_PROJECT_ID>.cloudfunctions.net/Hello`
  > Hello World

