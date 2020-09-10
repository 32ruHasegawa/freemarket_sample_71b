
[![Image from Gyazo](https://i.gyazo.com/9a76d80069822856079c27a90a578ac2.gif)](https://gyazo.com/9a76d80069822856079c27a90a578ac2)    

[![Image from Gyazo](https://i.gyazo.com/9a76d80069822856079c27a90a578ac2.gif)](https://gyazo.com/9a76d80069822856079c27a90a578ac2)

  # usersテーブル


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

# addressesテーブル

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



# favoritesテーブル


|Column|Type|Options|
|------|----|-------|
|user_id|reference|null:false,foregin_key:true|
|product|reference|null:false,foregin_key:true|

Association

- belongs_to:user
- belongs_to:product


# commentsテーブル


|Column|Type|Options|
|------|----|-------|
|user_id|reference|null:false,foregin_key:true|
|product_id|reference|null:false,foregin_key:true|
|comment|text|null:false|

Association

- belongs_to:user
- belongs_to:product


# order_statusesテーブル


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


# transaction_recordesテーブル

|Column|Type|Options|
|------|----|-------|
|user_id|reference|null:false,foregin_key:true|
|order_status|reference|null:false,foregin_key:true|

Association

- belongs_to:order_status



# productsテーブル


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



# categoriesテーブル


|Column|Type|Options|
|------|----|-------|
|name|string|null:false|
|ancestry|string|null:false|


Asscsiation

- has_many:products
- has_ancestry

# imagesテーブル

|Column|Type|Options|
|------|----|-------|
|image|string|null:false|
|product_id|reference|null:false,foregin_key:true|

Association

- belongs_to:product

# cradsテーブル
|Column|Type|Options|
|------|----|-------|
|user_id|Integer|null: false,foreign_key: true|
|cusomer_id|String|null: false|
|card_id|String|null: false|

Association

- belongs_to:user



