---
title: "AWSの認証情報はshared credential fileで管理する"
date: 2018-01-08T10:00:00+09:00
tags: [ "aws"]
---

様々なAWSサービスを使っていると複数のcredential情報を使い分けることが多くなる。

プログラムに直接credentialを書きたくない、かつサービスによって認証情報を使い分けるには、~/.aws/credentialsを使って複数のcredentialを管理するようにするのがよい。

## boto3で読み込まれるcredentialの優先順位

awsでよく使われるライブラリ、boto3では以下の[優先順位](http://boto3.readthedocs.io/en/latest/guide/configuration.html#shared-credentials-file)で認証情報がセットされる

1. boto.client() メソッドのパラメータでセットされたとき
2. Session objectのパラメータでセットされたとき
3. 環境変数でセットされた値
4. Shared credential file (~/.aws/credentials)
5. AWS config file (~/.aws/config)
6. Assume Role provider
7. Boto2 config file (/etc/boto.cfg and ~/.boto)
8. Instance metadata service on an Amazon EC2 instance that has an IAM role configured.

## 何を使うのがよいか

1,2だと直接プログラムに認証情報を書いてしまうことになるので
３以降を使いたい。

３だとAWS_ACCESS_KEY_ID、AWS_SECRET_ACCESS_KEY、AWS_SESSION_TOKENが読み込まれるので
サービスごとに認証情報を使い分けられない。

よって、４によってShared credential fileに複数の認証情報を記載して使い分ける

## Shared credential fileの書き方

以下のように~/.aws/credentialsにcredential情報を書く

```
[default]
aws_access_key_id=foo
aws_secret_access_key=bar

[dev]
aws_access_key_id=foo2
aws_secret_access_key=bar2

[prod]
aws_access_key_id=foo3
aws_secret_access_key=bar3
```

defaultは[]で囲まれたprofileが指定されないときに使われる。

## boto3をprofileを指定して使う

botoからは以下のようにprofileを指定して使う。

```
session = boto3.Session(profile_name='dev')
# Any clients created from this session will use credentials
# from the [dev] section of ~/.aws/credentials.
dev_s3_client = session.client('s3')
```

## 参考)1. boto.client() メソッドのパラメータでセットして使うとき

```
import boto3
client = boto3.client(
    's3',
    aws_access_key_id=ACCESS_KEY,
    aws_secret_access_key=SECRET_KEY,
    aws_session_token=SESSION_TOKEN,
)
```


## 参考)2. Session objectのパラメータでセットして使うとき

```
session = boto3.Session(
    aws_access_key_id=ACCESS_KEY,
    aws_secret_access_key=SECRET_KEY,
    aws_session_token=SESSION_TOKEN,
)
dev_s3_client = session.client('s3')
```
