
# Pictweet DB設計

## usersテーブル
|Column|Type|Options|
|------|----|-------|
|email|string|null: false,/[^\s]@[^\s]/|
|password|string|null: false|
|username|string|null: false|
### Association
- has_many :comments
- has_many :groups, through: :groups_users

## commentsテーブル
|Column|Type|Options|
|------|----|-------|
|text|text|null: false|
|user_id|integer|null: false, foreign_key: true|
|tweet_id|integer|null: false, foreign_key: true|
### Association
- belongs_to :user
- belongs_to :group

## groupsテーブル
|Column|Type|Options|
|------|----|-------|
|groupname|string|null: false|
|users_id|integer|null: false, foreign_key: true|
### Association
- has_many :massages
- has_many  :users,  through: :groups_users

## groups_usersテーブル
|Column|Type|Options|
|------|----|-------|
|user_id|integer|null: false, foreign_key: true|
|group_id|integer|null: false, foreign_key: true|

### Association
- belongs_to :group
- belongs_to :user
