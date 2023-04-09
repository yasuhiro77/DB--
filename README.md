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
| birth_day          | date                | null: false               |

### Association
* has_many :items
* has_many :orders

## items table
| Column                              | Type       | Options                        |
|-------------------------------------|------------|--------------------------------|
| items_name                          | string     | null: false                    |
| Description                         | string     | null: false                    |
| category_id                         | reference  | null: false, foreign_key: true |
| condition_id                        | reference  | null: false, foreign_key: true |
| delivery_charge_id                  | reference  | null: false, foreign_key: true |
| shipping_area_id                    | reference  | null: false, foreign_key: true |
| shipping_day_id                     | reference  | null: false, foreign_key: true |
| price                               | float　　   | null: false                    |
| user                                | references | null: false, foreign_key: true |

### Association
* belongs_to :users
* belongs_to :orders

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
* belongs_to :users

## orders table
| Column      | Type       | Options                        |
|-------------|------------|--------------------------------|
| items_name  | references | null: false, foreign_key: true |
| user        | references | null: false, foreign_key: true |
| address     | references | null: false, foreign_key: true |

### Association

* belongs_to :items
* belongs_to :users
* belongs_to :addresses