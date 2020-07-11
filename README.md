#  DB Design

## users
|Column|Type|Options|
|------|----|-------|
|name|string|null: false, index: true, unique: true|
|email|string|null: false, index: true, unique: true|
|password|string|null: false, index: true, unique: true|

### Association
- has_many :groups, through: :group_users
- has_many :group_users
- has_many :messages

## groups
|Column|Type|Options|
|------|----|-------|
|name|string|null: false, index: true, unique: true|

- has_many :users, through: :group_users
- has_many :group_users
- has_many :messages


## group_users

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
|body|text||
|image|string||
|user_id|references|null: false, foreign_key: true|
|group_id|references|null: false, foreign_key: true|

### Association
- belongs_to :user
- belongs_to :group
