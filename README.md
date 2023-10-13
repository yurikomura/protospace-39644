# テーブル設計

## users テーブル

| Column             | Type   | Options     | Key  |
| ------------------ | ------ | ----------- | ---- |
| email              | string | null: false | UNI  |
| encrypted_password | string | null: false |      |
| name               | string | null: false |      |
| profile            | text   | null: false |      |
| occupation         | text   | null: false |      |
| position           | text   | null: false |      |

### Association

- has_many :prototype_users
- has_many :prototypes, through: :prototype_users
- has_many :comments

## prototypes テーブル

| Column     | Type       | Options                        |
| ---------- | ---------- | ------------------------------ |
| title      | string     | null: false                    |
| catch_copy | text       | null: false                    |
| concept    | text       | null: false                    |
| user       | references | null: false, foreign_key: true |

### Association

- has_many :prototype_users
- has_many :users, through: :prototype_users
- has_many :comments

## prototype_users テーブル

| Column      | Type       | Options                        |
| ----------- | ---------- | ------------------------------ |
| user        | references | null: false, foreign_key: true |
| prototype   | references | null: false, foreign_key: true |

### Association

- belongs_to :prototype
- belongs_to :user

## comments テーブル

| Column    | Type       | Options                        |
| --------- | ---------- | ------------------------------ |
| content   | text       | null: false                    |
| prototype | references | null: false, foreign_key: true |
| user      | references | null: false, foreign_key: true |

### Association

- belongs_to :prototype
- belongs_to :user
