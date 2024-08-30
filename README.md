# README
# テーブル設計

## users_table

| Column             | Type   | Options     |
| ------------------ | ------ | ----------- |
| email              | string | null: false, unique: true |
| password           | string | null: false |
| name_first         | string | null: false |
| name_last          | string | null: false |
| birthday           | text   | null: false |
| nickname         | text   | null: false |
| user_id           | text   | null: false |


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


### Association

- belongs_to :user
- has_many :shippings
- has_many :purchases

## shippings_table

| Column           | Type       | Options                        |
| ---------------- | ---------- | ------------------------------ |
| post_code        | text       | null: false |
| prefectures      | text       | null: false |
| municipalities   | text       | null: false |
| street_address   | text       | null: false |
| building_name    | text       | null: false |
| telephone_number | text       | null: false |


### Association

- belongs_to :user
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

- belongs_to :user
- belongs_to :items
- belongs_to :shippings