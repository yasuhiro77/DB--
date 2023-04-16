
# DB 設計
## users table
| Column             | Type                | Options                   |
|--------------------|---------------------|---------------------------|
| email              | string              | null: false,unique: true  |
| encrypted_password | string              | null: false               |
| nickname           | string              | null: false               |
| first_name         | string              | null: false               |
| last_name          | string              | null: false               |
| first_name_kana    | string              | null: false               |
| last_name_kana     | string              | null: false               |
| birth_date         | date                | null: false               |
integer
### Association
* has_many :items
* has_many :order

## items table
| Column                              | Type       | Options                        |
|-------------------------------------|------------|--------------------------------|
| items_name                          | string     | null: false                    |
| description                         | string     | null: false                    |
| category_id                         | integer　  | null: false, foreign_key: true |
| condition_id                        | integer    | null: false, foreign_key: true |
| delivery_charge_id                  | integer    | null: false, foreign_key: true |
| prefecture_id                       | integer    | null: false, foreign_key: true |
| shipping_day_id                     | integer    | null: false, foreign_key: true |
| price                               | integer    | null: false                    |
| user                                | references | null: false, foreign_key: true |

### Association
* belongs_to :item
* belongs_to :order

## addresses table　　　　　　
| Column                              | Type       | Options                        |
|-------------------------------------|------------|--------------------------------|
| post_code                           | string     | null: false                    |
| prefecture_id                       | integer 　 | null: false　                   |
| city                                | string     | null: false                    |
| address                             | string     | null: false                    |
| building                            | string     |
| tel_no                              | string     | null: false                    |

### Association
* belongs_to :order


## orders table
| Column      | Type       | Options                        |
|-------------|------------|--------------------------------|
| user        | references | null: false, foreign_key: true |
| item        | references | null: false, foreign_key: true |

### Association

* belongs_to :item
* belongs_to :user
* has_one :address
