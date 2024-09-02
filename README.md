# README
# テーブル設計

## users_table

| Column             | Type   | Options     |
| ------------------ | ------ | ----------- |
| email              | string | null: false, unique: true |
| encrypted_password | string | null: false |
| name_first         | string | null: false |
| name_first(kana)   | string | null: false |
| name_last          | string | null: false |
| name_last(kana)    | string | null: false |
| birthday           | date   | null: false |
| nickname           | string | null: false |

### Association

- has_many :items
- has_many :shippings
- has_many :purchases

## items_table

| Column                      | Type       | Options     |
| -----------------------     | ---------- | ----------- |
| name                        | string     | null: false |
| image_url                   | text       | null: false |
| explanation                 | text       | null: false |
| category                    | text       | null: false |
| condition                   | text       | null: false |
| shipping_fee                | text       | null: false |
| shipping_preparation_days   | text       | null: false |
| price                       | text       | null: false |
| sales_commission            | text       | null: false |
| sales_profit                | text       | null: false |
| user                        | references | null: false, foreign_key: true|

### Association

- belongs_to :users
- has_many :shippings
- has_many :purchases

## shippings_table

| Column           | Type       | Options                        |
| ---------------- | ---------- | ------------------------------ |
| post_code        | text       | null: false |
| prefectures      | text       | null: false |
| municipalities   | text       | null: false |
| street_address   | text       | null: false |
| building_name    | text       |             |
| purchases        | references | null: false, foreign_key: true|


### Association

- belongs_to :users
- belongs_to :items
- belongs_to :purchases


## purchases_table

| Column          | Type       | Options                        |
| --------------- | ---------- | ------------------------------ |
| users_id        | text       | null: false |
| items_id        | text       | null: false |
| shippings_id    | text       | null: false |
| purchase_date   | text       | null: false |

### Association

- belongs_to :users
- belongs_to :items
- has_one    :shippings