# DB設計

# usersテーブル

| Column   | Type   | Options     |
| -------- | ------ | ----------- |
| nickname | string | null: false |
| email    | string | null: false |
| password | string | null: false |

### Association

- has_one :profile
- has_many :items
- has_many :credit_cards
- has_many :destinations


# profilesテーブル

| Column         | Type       | Options                        |
| -------------- | ---------- | ------------------------------ |
| last_name      | string     | null: false                    |
| first_name     | string     | null: false                    |
| last_name_kana | string     | null: false                    |
| first_name_kana| string     | null: false                    |
| birth_year     | integer    | null: false                    |
| birth_month    | integer    | null: false                    |
| birth_date     | integer    | null: false                    |
| user_id        | references | null: false, foreign_key: true |

### Association

- belongs_to :user


# itemsテーブル

| Column      | Type       | Options                        |
| ----------- | ---------- | ------------------------------ |
| item_name   | string     | null: false                    |
| description | text       | null: false                    |
| category    | integer    | null: false                    |
| state       | integer    | null: false                    |
| delivery_fee| integer    | null: false                    |
| consignor   | integer    | null: false                    |
| days        | integer    | null: false                    |
| price       | integer    | null: false                    |
| user_id     | references | null: false, foreign_key: true |

### Association

- has_one_attached :image
- belongs_to :user
- has_one :destination


# credit_cardsテーブル

| Column           | Type       | Options                        |
| ---------------- | ---------  | ------------------------------ |
| card_num         | integer    | null: false                    |
| expiration_month | integer    | null: false                    |
| expiration_year  | integer    | null: false                    |
| security_code    | integer    | null: false                    |
| user_id          | references | null: false, foreign_key: true |
| item_id          | references | null: false, foreign_key: true |

### Association

- belongs_to :user
- has_many :items

# destinationsテーブル

| Column           | Type       | Options                        |
| ---------------- | ---------- | ------------------------------ |
| postal_code      | integer    | null: false                    |
| prefectures      | integer    | null: false                    |
| municipality     | string     | null: false                    |
| address          | string     | null: false                    |
| building         | string     | ------------------------------ |
| phone_number     | integer    | null: false                    |
| user_id          | references | null: false, foreign_key: true |
| item_id          | references | null: false, foreign_key: true |

### Association

- belongs_to :user
- has_many :items






