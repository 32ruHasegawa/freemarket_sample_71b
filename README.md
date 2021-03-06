### アプリ名  
FURIMA

### 概要  
既存のフリマアプリをサンプリングしたアプリです。
※必須機能のみ実装

### 作成背景  
アジャイル開発を学ぶため作成。（プログラミングスクールの同期と開発）  

### 開発環境  
Ruby/Ruby on Rails/MySQL/Github/AWS/Visual Studio Code  

### 開発体制  
人数：5  
アジャイル型開発（スクラム）  
Trelloによるタスク管理  
  
### イメージ    
<img width="1440" alt="スクリーンショット 2020-09-14 7 30 28" src="https://user-images.githubusercontent.com/62422532/93030261-9f676900-f65c-11ea-8db4-528dec6cab6f.png">

### URL  
http://18.182.212.148  
(ユーザー名：admin, パスワード：2222)
  
### 工夫したポイント  
既存のフリマアプリのようなデザインにしたことです。
  
### DB設計  
#### usersテーブル

|Column|Type|Options|
|------|----|-------|
|nickname|string|null:false|
|email|string|null:false|
|password|string|null:false|
|first_name|string|null:false|
|last_name|string|null:false|
|last_name_kana|string|null:false|
|first_name_kana|string|null:false|
|biryh_y|integer|null:false|
|biryh_m|integer|null:false|
|biryh_d|integer|null:false|
Association

- has_many:favorites, dependent: :destroy
- has_many:comments
- has_many:products
- has_many:order_statuses
- has_many:address, dependent: :destroy

#### addressesテーブル

|Column|Type|Options|
|------|----|-------|
|user_id|reference|null:false,foregin_key:true|
|post_number|string|null:false|
|city|string|null:false|
|block|string|null:false|
|address|string|null:false|
|bulding_name|string|null:false|

Asscsiation

- belongs_to:user



#### favoritesテーブル


|Column|Type|Options|
|------|----|-------|
|user_id|reference|null:false,foregin_key:true|
|product|reference|null:false,foregin_key:true|

Association

- belongs_to:user
- belongs_to:product


#### commentsテーブル


|Column|Type|Options|
|------|----|-------|
|user_id|reference|null:false,foregin_key:true|
|product_id|reference|null:false,foregin_key:true|
|comment|text|null:false|

Association

- belongs_to:user
- belongs_to:product


#### order_statusesテーブル


|Column|Type|Options|
|------|----|-------|
|purchaser_id|integer|null:false,add_index/add_foreign|
|seller_id|integer|null:false,add_index/add_foreign|
|status|integer|null:false|
|item_id|reference|null:false,foregin_key:true|

Association

- belongs_to:user
- belongs_to:product
- has_many:transection_records


#### transaction_recordesテーブル

|Column|Type|Options|
|------|----|-------|
|user_id|reference|null:false,foregin_key:true|
|order_status|reference|null:false,foregin_key:true|

Association

- belongs_to:order_status



#### productsテーブル


|Column|Type|Options|
|------|----|-------|
|name|string|null:false|
|category_id|reference|null:false,forgin_key:true|
|condition|string|null:false|
|price|string|null:false|
|shipping_days|string|null:false|
|postage|string|null:false|
|user_id|string|null:false,foregin_key:true|
|explanation|text|null:false|


Association

- belongs_to:user
- has_many:favorites
- has_many:comments
- has_many:order_statuses
- belongs_to:category
- has_many:images



#### categoriesテーブル


|Column|Type|Options|
|------|----|-------|
|name|string|null:false|
|ancestry|string|null:false|


Asscsiation

- has_many:products
- has_ancestry

#### imagesテーブル

|Column|Type|Options|
|------|----|-------|
|image|string|null:false|
|product_id|reference|null:false,foregin_key:true|

Association

- belongs_to:product

#### cradsテーブル
|Column|Type|Options|
|------|----|-------|
|user_id|Integer|null: false,foreign_key: true|
|cusomer_id|String|null: false|
|card_id|String|null: false|

Association

- belongs_to:user

