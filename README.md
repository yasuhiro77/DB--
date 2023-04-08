# DB 設計
## users table
| Column             | Type                | Options                   |
|--------------------|---------------------|---------------------------|
| email              | string              | null: false,unique: true |
| encrypted_password | string              | null: false               |
| nickname           | string              | null: false               |
| first_name         | string              | null: false               |
| last_name          | string              | null: false               |
| first_name_kana    | string              | null: false               |
| last_name_kana     | string              | null: false               |
| birth_day          | date                | null: false               |

### Association
* has_many :items
* has_many :records

## items table
| Column                              | Type       | Options                        |
|-------------------------------------|------------|--------------------------------|
| items_name                          | string     | null: false |
| category                            | references | null: false, foreign_key: true |
| condition                           | references | null: false, foreign_key: true |
| delivery_charge                     | references | null: false, foreign_key: true |
| shipping_area                       | references | null: false, foreign_key: true |
| shipping_days                       | references | null: false, foreign_key: true |
| price                               | references | null: false, foreign_key: true |

### Association
* belongs_to :user

## addresses table　　　　　　
| Column                              | Type       | Options                        |
|-------------------------------------|------------|--------------------------------|
| post_code                           | string     | null: false                    |
| prefecture_id                       | integer 　 | null: false, foreign_key: true |
| city                                | string     | null: false |
| address                             | string     | null: false |
| building                            | string     |
| tel_no                              | string     | null: false |
### Association
* belongs_to :user

## records table
| Column      | Type       | Options                        |
|-------------|------------|--------------------------------|
| nickname    | references | null: false                    |
| user        | references | null: false, foreign_key: true |

### Association

* belongs_to :items
* belongs_to :user

## managements table
| Column      | Type       | Options                        |
|-------------|------------|--------------------------------|
| nickname    | references | null: false                    |
| user        | references | null: false, foreign_key: true |

### Association

* belongs_to :items
* belongs_to :user