#  DB Design

## users
|Column|Type|Options|
|------|----|-------|
|name|string|null: false, index: true|
|email|string|null: false, unique|
|password|string|null: false|

### Association
- has_many :groups, through: :groups_users
- has_many :groups_users
- has_many :messages

## groups
|Column|Type|Options|
|------|----|-------|
|name|string|null: false|

- has_many :users, through: :groups_users
- has_many :groups_users
- has_many :messages


## groups_users

|Column|Type|Options|
|------|----|-------|
|user_id|references|null: false, foreign_key: true|
|group_id|references|null: false, foreign_key: true|

### Association
- belongs_to :user
- belongs_to :group

## messages

|Column|Type|Options|
|------|----|-------|
|body|text|null: false|
|image|string||
|user_id|references|null: false, foreign_key: true|
|group_id|references|null: false, foreign_key: true|

### Association
- belongs_to :user
- belongs_to :group
