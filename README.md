# muslegram

## アプリケーション名
  muslegram

## 制作背景
  写真などを投稿するアプリケーションは存在するが、何かのジャンルに特化した写真投稿アプリケーションが存在すれば、
  共通の趣味を持った人と繋がることや情報共有を効率的にできると感じながら使用していた。
  その中で近年フィットネスブームに影響され、「筋トレ」をやりたいが、やり方がわからない人や食事メニューの組み立て方が
  分からなくて挫折してしまう人が多いのも事実である。
  そういった人たちが「筋トレ」を続けることの楽しさや自分の身体の変化の記録を残し、その記録に対して励ましあえるアプリケーションを
  制作することでより多くの人に「筋トレ」の楽しさを知ってもらいたいと考え、本アプリケーションの制作を行った。
## URL

## テスト用アカウント

## 実装した機能についてのGIFと説明

## 実装予定の機能

## 工夫した点

## DB設計

## 使用技術(開発環境)

## ローカルでの動作方法

# テーブル設計

## users テーブル
| Column          | Type   | Options     |
| --------------- | ------ | ----------- |
| nickname        | string | null: false |
| email           | string | null: false |
| password        | string | null: false |

### association
- has_many :posts
- has_many :comments
- has_one :profile

## posts テーブル
| Column  | Type        | Options                        |
| ------- | ----------- | ------------------------------ |
| text    | string      | null: false                    |
| user    | references  | null: false, foreign_key: true |

### association
- has_many :comments
- belongs_to :user

## comments テーブル
| Column  | Type        | Options                        |
| ------- | ----------- | ------------------------------ |
| text    | string      | null: false                    |
| user    | references  | null: false, foreign_key: true |
| posts   | references  | null: false, foreign_key: true |

### association
- belongs_to :user
- belongs_to :post

## profiles テーブル
| Column             | Type        | Options                        |
| ------------------ | ----------- | ------------------------------ |
| birthday           | date        | null: false                    |
| last_name          | string      | null: false                    |
| first_name         | string      | null: false                    |
| last_name_kana     | string      | null: false                    |
| first_name_kana    | string      | null: false                    |
| favorite_gym       | integer     | null: false                    |
| prefecture         | integer     | null: false                    |
| self_introduction  | string      |                                |
| user               | references  | null: false, foreign_key: true |

### association
- belongs_to :user