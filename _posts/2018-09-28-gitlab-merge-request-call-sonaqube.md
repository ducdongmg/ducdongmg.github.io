---
layout: single
title:  "Gọi sonarQube khi tạo merge request trên Gitlab"
desc: "SonarQube tự động check code khi tạo merge request trên GitLab"
keywords: "SonarQube, gitlab, automatic"
categories: [automatic]
tag: [automatic]
---


SonarQube tự động check code khi tạo merge request trên GitLab
===============================

GitLabのマージリクエストをSonarQube Scannerで静的コード解析し結果をマージリクエストのコメントとして投稿するためのメモ。

マージリクエストの作成から解析結果のコメント投稿までの動作概要は以下。

1.  開発者がGitLab上でマージリクエストを作成
2.  GitLabのWebhookでJenkinsの自動レビュージョブを起動
3.  自動レビュージョブがSonarQubeサーバから必要な情報を取得する
4.  自動レビュージョブが静的コード解析を実施
5.  自動レビュージョブが解析結果をGitLabへ投稿

* * *

設定作業の流れ
=======

*   Jenkinsの設定
    *   GitLab Plugのインストール
    *   自動レビュージョブの作成
*   GitLabの設定
    *   ユーザの作成とグループへの追加
    *   Webhookの追加
*   SonarQubeの設定
    *   GitLab Pluginのイントールと設定

Jenkins プラグインの追加
================

GitLab側からのWebhookをトリガーにジョブを起動できるよう [GitLab](https://github.com/jenkinsci/gitlab-plugin)プラグインをインストールする。

_Jenkinsの管理_ _プラグインの管理_ _利用可能_ から `GitLan Plugin` をインストール。

**インストール後、システム設定 から GitLabのURLや認証情報が設定できるようになるが特に設定は不要。今回作成する自動レビュージョブはSonarQube側のGitLab設定を参照するため。**

Jenkins ジョブの作成
==============

GitLabマージリクエスト作成時のWebhookをトリガーに起動する自動レビュージョブを作成する。

_新規ジョブ作成_ から _フリースタイル・プロジェクトのビルド_ を選んでジョブを作成。

ソースコード管理
--------

ソースコード管理に `git` を選択

_リポジトリ_ に以下を設定。

リポジトリURL

`${gitlabSourceRepoURL}`

Credentials

CIユーザ用のクレデンシャルを指定。

_ビルドするブランチ_ に以下を設定。

ブランチ指定子

`*/${gitlabSourceBranch}`

このジョブを複数のGitLabプロジェクトから使用する場合は、 _追加処理_ に以下を設定。

Check out to a sub-directory

`${gitlabSourceRepoName}`

ビルド・トリガ
-------

_Build when a change is pushed to GitLab_ を選択。

`GitLab CI Service URL:` 以降のURLはWebhookでこのジョブを起動するためのエンドポイント。  
GitLab側の設定で必要になるのでメモしておく。

Push Events

なし

Opened Merge Request Events

✓

Accepted Merge Request Events

なし

Closed Merge Request Events

`Never`

Comments

なし

Comment (regex) for triggering a build

`Jenkins please retry a build`

さらに _高度な設定_ から

Ignore WIP Merge Requests

なし  
WIPなマージリクエストも対象にする。

Secret token

_Generate_ でトークンを生成。  
ジョブをWebhook経由で実行する際に必要となる。GitLab側の設定で必要となるのでメモしておく。

ビルド
---

今回はSonarQube ScannerをJenkinsのプラグインではなくGradleのプラグインとして動かすため、 _ビルド手順の追加_ _シェルの実行_ から gradleコマンド経由でSonarQube Scannerを実行する。

    # Check out to a sub-directoryを指定した場合はcdする
    cd ${gitlabSourceRepoName}
    
    # マージ元、先の差分コミットID一覧をカンマ区切りで取得
    COMMIT_SHA=$(git log --pretty='format:%H' origin/${gitlabTargetBranch}..origin/${gitlabSourceBranch} | tr '\n' ',')
    
    # gradle経由でSonarQube Runnerを実行
    ./gradlew --stacktrace sonarqube \
    -Dsonar.analysis.mode=preview \
    -Dsonar.gitlab.commit_sha=${COMMIT_SHA} \
    -Dsonar.gitlab.ref_name=${gitlabSourceBranch} \
    -Dsonar.gitlab.project_id=${gitlabSourceNamespace}/${gitlabSourceRepoName} \
    -Dunique_issue_per_inline=true \
    -Dsonar.gitlab.disable_global_comment=true \
    -Dsonar.host.url=http://<SonarQubeのホスト>:9000
    

好みの問題であるが`sonar.gitlab.disable_global_comment=true`でglobal commentを無効化、 コミットの変更行対してのみインラインでレポートするようにした。

またGitLabプラグインで利用できる環境変数一覧については以下を参照。 [https://github.com/jenkinsci/gitlab-plugin#parameterized-builds](https://github.com/jenkinsci/gitlab-plugin#parameterized-builds)

GitLabの設定
=========

ユーザの作成
------

自動レビュージョブが解析結果のコメントつける際に利用するレビュー用ユーザを作成。  
既存のCI用ユーザを利用しても良いが今回は `sonar` というユーザを作成する。

作成したユーザでログインし _Settings_ _Access Tokens_ から Sonarが利用するアクセストークンを払い出す。

Name

sonar

Expires at

なし

Scopes (api)

✓

Scope (read\_user)

なし

_Create Personal Access Token_ で作成。

払い出したトークンをメモしておく。

グループのメンバーに追加
------------

作成したレビューユーザ `sonar` を対象グループに `Developer` ロールで追加する。

Webhookの設定
----------

対象プロジェクトの設定から _Integrations_ で新規Webhookを登録。

URL

Jenkins自動レビュージョブのWebhook URL

Secret Token

Jenkins自動レビュージョブのSecret Token

Trigger

`Merge Request Events`

_Add Webhook_ で登録。

SonarQubeの設定
============

SonarQube Scannerの解析結果をGitLabへ投稿できるよう[sonar-gitlab-plugin](https://gitlab.talanlabs.com/gabriel-allaigre/sonar-gitlab-plugin)をインストール、設定する。

インストール
------

adminユーザでログインし、

_Administration_ _System_ _Available_ から `GitLab` で検索。

`GitLab` を _Install_

設定
--

_Administration_ _Configuration_ _GitLab_ から設定。

GitLab url

GitLabのURL

GitLab User Token

GitLab側で作成したレビュー用ユーザのパーソナルアクセストークン

_Save Repoting Settigs_ で保存。

* * *

以上で設定は完了。  
マージリクエストを作成すると自動レビュージョブが動き、指摘箇所はマージリクエストのコメントに投稿されるようになる。

<div style="text-align: right">Theo <a href="https://blog.nijohando.jp/post/gitlab-merge-request-sonarqube/">nijohando</a></div>