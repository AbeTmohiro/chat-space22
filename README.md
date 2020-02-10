# README

This README would normally document whatever steps are necessary to get the
application up and running.

Things you may want to cover:

* Ruby version

* System dependencies

* Configuration

* Database creation

* Database initialization

* How to run the test suite

* Services (job queues, cache servers, search engines, etc.)

* Deployment instructions

* ...
# DATABASE
## usersテーブル
|Column|Type|Options|
|------|----|-------|
|name|varchar(255)|null: false,add_index: true|
|email|varchar(255)|null: false,unique: true|
|password|varchar|null: false|

### Association
- has many :messages
- has_many :groups_users
- has_many :groups,through: :groups_users

## groupsテーブル
|Column|Type|Options|
|------|----|-------|
|group_name|varchar(256)|null: false,unique: true|

### Association
- has_many :groups_users
- has_many :users,through: :groups_users
- has_many :messages

## groups_usersテーブル

|Column|Type|Options|
|------|----|-------|
|user_id|integer|null: false, foreign_key: true|
|group_id|integer|null: false, foreign_key: true|

### Association
- belongs_to :group
- belongs_to :user

## messagesテーブル
|Column|Type|Options|
|------|----|-------|
|body|text|
|image|string|
|user_id|integer|null: false, foreign_key: true|
|group_id|integer|null: false, foreign_key: true|

### Association
- belongs_to :group
- belongs_to :user