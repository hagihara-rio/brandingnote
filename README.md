# README


## アプリケーション名

Blanding note (ブランディングノート)

## アプリケーション概要

ブランディングを必要とする方々
それぞれにあった、提案やサポートをするアプリケーション

## URL

（デプロイ次第 記載致します）

## 目指した課題解決

Blanding note の機能は、大きく分けて2方向です。

  1.ユーザー視点 / ヒアリングをはじめとする機能から
    ブランディングの手順や理解を深め、サポート、及びマッチングをする。

  2.ブランディング企業視点 / ブランディング業界の顧客リクエストの把握
    また、最適なタイミング・マッチングを実現する。

## 洗い出した要件

・ヒアリング機能
・ユーザー登録機能
・マイページ（進捗管理）
・マッチング機能
・情報コラムページ
・ホームページ

## 実装した機能についてのGIFと説明

（実装後 記載致します）

## データベース設計

【 users テーブル 】

| Column             | Type    | Options     |
| ------------------ | ------- | ----------- |
| brand_name         | string  | null: false |
| name               | string  | null: false |
| name_kana          | string  | null: false |
| birthdate          | date    | null: false |
| gender_id          | integer | null: false |
| email              | string  | null: false |
| phone_number       | string  | null: false |
| postal_code        | integer | null: false |
| prefecture_id      | integer | null: false |
| city               | string  | null: false |
| address            | string  | null: false |
| building_name      | string  |             |
| encrypted_password | string  | null: false |

< Association >
- has_many :designers
- has_one :user_hearing
- has_many :matchings


【 user_hearings テーブル 】

| Column             | Type    | Options     |
| ------------------ | ------- | ----------- |
| understand_id      | integer | null: false |
| type_id            | integer | null: false |
| term_id            | integer | null: false |
| budget_id          | integer | null: false |

< Association >
- belongs_to :user
- has_one :column


【 designers テーブル 】

| Column             | Type       | Options                        |
| ------------------ | ---------- | ------------------------------ |
| name               | string     | null: false                    |
| name_kana          | string     | null: false                    |
| email              | string     | null: false                    |
| phone_number       | integer    | null: false                    |
| postal_code        | integer    | null: false                    |
| prefectures        | string     | null: false                    |
| city               | string     | null: false                    |
| address            | string     | null: false                    |
| building_name      | string     |                                |
| encrypted_password | string     | null: false                    |

< Association >
- has_many :users
- has_one :designer_hearing
- has_many :matchings


【 designer_hearings テーブル 】

| Column             | Type    | Options     |
| ------------------ | ------- | ----------- |
| type_id            | integer | null: false |
| term_id            | integer | null: false |
| cost_id            | integer | null: false |

< Association >
- belongs_to :designer


【 columns テーブル 】
| Column             | Type    | Options     |
| ------------------ | ------- | ----------- |

< Association >
- belongs_to :user_hearing


【 matchings テーブル 】
| Column             | Type    | Options     |
| ------------------ | ------- | ----------- |

< Association >
- belongs_to :users
- belongs_to :designer