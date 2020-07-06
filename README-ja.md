[circleci-badge]: https://circleci.com/gh/autifyhq/autify-example-integration-with-circleci/tree/master.svg?style=svg
[circleci-link]:  https://circleci.com/gh/autifyhq/autify-example-integration-with-circleci/tree/master

[pr-welcome-badge]: https://img.shields.io/badge/PRs-welcome-brightgreen.svg
[pr-welcome-link]:  http://makeapullrequest.com

[example-badge]: https://img.shields.io/badge/Autify-example-brightgreen
[example-link]:  https://github.com/search?utf8=%E2%9C%93&q=example%2Buser%3Aautifyhq&type=Repositories&ref=searchresults

<br/><p align="center">
  <small>他の言語： [English](README.md)</small>
</p><br/>

# AutifyとCircleCIの連携例 [![CircleCI][circleci-badge]][circleci-link] [![PRs Welcome][pr-welcome-badge]][pr-welcome-link] [![Example Badge][example-badge]][example-link]

> AutifyとCircleCIを使って自身を持ってリリースするためのベストプラクティスについて説明します

## ベストプラクティス

リリースの前にリグレッションテストを回すことで、より安全に、自信を持って新しい機能をリリースすることが出来ます。そのプロセスを自動化するために、CircleCIでmaster/developブランチに機能がマージされたタイミングで自動的にAutifyのリグレッションテストを実行することができます。

## 設定方法

1. CircleCIで以下の環境変数を設定
     |環境変数|説明|
     |---|---|
     | AUTIFY_PERSONAL_ACCESS_TOKEN |Autifyのユーザー設定ページで生成されるパーソナルアクセストークン|
     | AUTIFY_PROJECT_ID |AutifyでのプロジェクトID|
     | AUTIFY_TEST_PLAN_ID |Autifyで実行したいテストプランのID|

1. [`.circleci/config.yml`](.circleci/config.yml)の必要な部分をコピーして適宜変更

      ```yml
      # 注意：このファイルではmasterブランチにマージしたときにリグレッションが実行されるようになっています
      workflows:
        version: 2
        commit-workflow:
          jobs:
            - publish-to-production:
                filters:
                  branches:
                    only: master
      ```

## ライセンス

autify-example-integration-with-circleci © [Autify Engineers](https://github.com/autifyhq). [MIT License](LICENSE)の下でリリースされています。<br/>
[コントリビューター](https://github.com/autifyhq/autify-example-integration-with-circleci/graphs/contributors)の助けを借りて[Autify Engineers](https://github.com/autifyhq)が作成し、保守しています。
