# DevOps a Rails Application

## Rails アプリケーションを DevOps

## 使用ツール

- Ansible
- CircleCI
- ServerSpec
- Terraform

## 概要

リポジトリに Push を契機に CircleCI が動作します。

1. Terraform によるインフラ環境構築
2. Ansible による構成管理
3. ServerSpec による自動テスト

## 事前設定

## AWS

- IAM からプログラムによるアクセスできるユーザーの作成
- Elastic IP アドレス を用意
- RDS のエンドポイントを事前に確認しておくこと<br>
  Amazon RDS のエンドポイントの命名規則は以下
  ```
  識別子は、RDS によってインスタンスに割り当てられた DNS ホスト名の一部として使用されます。たとえば、db1 を DB インスタンス識別子として指定した場合、RDS は、db1.123456789012.us-east-1.rds.amazonaws.com などのインスタンスの DNS エンドポイントを自動的に割り当て、ここでの 123456789012 はアカウントの特定の地域の固定識別子です。
  ここでの 123456789012 はアカウントの特定の地域の固定識別子です。
  ```
  つまり、
  - RDS のインスタンス識別子
  - AWS アカウント ID
  - RDS インスタンスを配置するリージョン が変わらなければ、たとえば RDS インスタンスを作り直してもエンドポイントは変わらないようです。

## CircleCI の設定

- Project Settings > Environment Variables から設定

  <br><br>

- Project Settings > Additional SSH Keys から設定  
  <br><br>
  SSH キーを登録すると Fingerprint が作成されます。
