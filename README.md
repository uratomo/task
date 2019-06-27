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

DB設計

## usersテーブル

|Column|Type|Options|
|----------|-------|------|
|id        |integer|null: false,foreign_key: true|
|name      |string |null: false,unique: true     |
|mail      |string |null: false,unique: true     |
|password  |string |null: false                  |
## Asociation
- has_many  :boards,through teams
- has_many  :teams
- has_many  :lists
- has_many  :cards

## boardsテーブル
|Column|Type   |Options                      |
|------|-------|-----------------------------|
|id    |integer|null: false,foreign_key: true|
|name  |string |null: false                  |
## Asociation
- has_many :users,through teams
- has_many :teams
- has_many :lists
- has_many :cards

## teams 中間テーブル
|Column  |Type   |Options                      |
|--------|-------|-----------------------------|
|id      |integer|null: false,foreign_key: true|
|user_id |integer|null: false                  |
|board_id|integer|null: false                  |
## Asociation
- belongs_to :board
- belongs_to :user

## listsテーブル
|Column  |Type   |Options                      |
|--------|-------|-----------------------------|
|id      |integer|null: false                  |
|name    |string |null: false                  |
|board_id|integer|null: false                  |
|user_id |integer|null: false                  |
## Asociation
- has_many :cards
- belongs_to :board
- belongs_to :user

## cardsテーブル
|Column  |Type   |Options                      |
|--------|-------|-----------------------------|
|id      |integer|null: false                  |
|title   |string |null: false                  |
|text    |string |null: false                  | 
|board_id|integer|null: false                  |
|user_id |integer|null: false                  |
|list_id |integer|null: false                  |
## Asociation
- belongs_to :user
- belongs_to :board
- belongs_to :list



