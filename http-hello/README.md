# http-helloディレクトリのREADME
- `$ export GO111MODULE=on`

- `$ go mod init github.com/yhidetoshi/gcloud-function-examples/http-hello`

- `$ gcloud functions deploy Hello --entry-point Hello --runtime go111 --trigger-http --project <PROJECTID> --region asia-northeast1`

--> Endpointが出力される

- `$ curl https://asia-northeast1-<GCP_PROJECT_ID>.cloudfunctions.net/Hello`
  > Hello World

