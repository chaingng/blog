---
title: "特定のs3バケットにのみアクセス権限を与えるiamポリシー"
date: 2018-04-02T10:00:00+09:00
tags: [ "aws"]
---

[公式](https://docs.aws.amazon.com/ja_jp/IAM/latest/UserGuide/reference_policies_examples_s3_rw-bucket.html)を参考に、以下のように設定すればよい。


## プログラムアクセスにより、特定のバケットに対するRead/Write権限を付与するiamポリシー

```
{
   "Version": "2012-10-17",
   "Statement": [
     {
       "Effect": "Allow",
       "Action": ["s3:ListBucket", "s3:GetBucketLocation"],
       "Resource": ["arn:aws:s3:::<BUCKET-NAME>"]
     },
     {
       "Effect": "Allow",
       "Action": [
         "s3:PutObject",
         "s3:GetObject",
         "s3:DeleteObject"
       ],
       "Resource": ["arn:aws:s3:::<BUCKET-NAME>/*"]
     }
   ]
 }
```



## マネジメントコンソールにて、特定のバケットに対するRead/Writeを権限を付与するiamポリシー

マネジメントコンソールで閲覧する際は　`s3:ListAllMyBuckets`も必要なので、
プログラムによるアクセスを許可する場合には以下のように設定する


```
{
   "Version": "2012-10-17",
   "Statement": [
     {
       "Effect": "Allow",
       "Action": [
         "s3:GetBucketLocation",
         "s3:ListAllMyBuckets"
       ],
       "Resource": "*"
     },
     {
       "Effect": "Allow",
       "Action": ["s3:ListBucket"],
       "Resource": ["arn:aws:s3:::<BUCKET-NAME>"]
     },
     {
       "Effect": "Allow",
       "Action": [
         "s3:PutObject",
         "s3:GetObject",
         "s3:DeleteObject"
       ],
       "Resource": ["arn:aws:s3:::<BUCKET-NAME>/*"]
     }
   ]
 }

```



