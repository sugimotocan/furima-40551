# README
# テーブル設計

## users_table

| Column             | Type    | Options     |
| ------------------ | ------- | ----------- |
| email              | string  | null: false, unique: true |
| encrypted_password | string  | null: false |
| name_first         | string  | null: false |
| name_first_kana    | string  | null: false |
| name_last          | string  | null: false |
| name_last_kana     | string  | null: false |
| birthday           | date    | null: false |
| nickname           | string  | null: false |

### Association

- has_many  :items
- belong_to :purchase

## items_table

| Column                       | Type       | Options     |
| ------------------------     | ---------- | ----------- |
| name                         | string     | null: false |
| explanation                  | text       | null: false |
| category_id                  | integer    | null: false |
| condition_id                 | integer    | null: false |
| shipping_fee_id              | integer    | null: false |
| shipping_preparation_days_id | integer    | null: false |
| prefecture_id                | integer    | null: false |
| price                        | integer    | null: false |
| user                         | references | null: false, foreign_key: true|

### Association

- belongs_to :user
- has_many :purchases

## shippings_table

| Column             | Type       | Options                        |
| ------------------ | ---------- | ------------------------------ |
| post_code          | string     | null: false |
| prefecture_id      | integer    | null: false |
| municipalitie      | string     | null: false |
| street_addres      | string     | null: false |
| building_name      | string     |             |
| purchase           | references | null: false, foreign_key: true|
| telephone_number   | integer    | null: false |


### Association


- belongs_to :purchase


## purchases_table

| Column          | Type       | Options                        |
| --------------- | ---------- | ------------------------------ |
| user           | references  | null: false, foreign_key: true|
| item           | references  | null: false, foreign_key: true|


### Association

- belongs_to :user
- belongs_to :item
- has_one    :shipping