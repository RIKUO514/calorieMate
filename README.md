# アプリ名

caloiremate

# 概要

■ユーザーアカウントの登録

■何を食べたのか記録する

■他のユーザーからコメントを反映させる

■週・月のカロリーの目標を設定する

# 制作背景（意図）

自分が増量中にカロリーの目標を設定して、食べた物のカロリーが自動で反映されるアプリケーションが欲しかった。

# 実装内容

■ユーザー管理機能

■コメント投稿機能

■目標設定機能

■投稿機能


# DB設計

## users

| Column             | Type                | Options                 |
|--------------------|---------------------|-------------------------|
| name               | string              | null: false             |
| email              | string              | null: false             |

### Association

* has_many :posts
* has_many :comments
- has_one  :target

## posts

| Column             | Type                | Options                 |
|--------------------|---------------------|-------------------------|
| name               | string              | null: false             |
| text               | string              | null: false             |
| calorie            | string              | null: false             |
| image              | text                | null: false             |
| user               | references          | foreign_key: true       |

### Association

* has_many   :comments
- belongs_to :user


## targets

| Column             | Type                | Options                 |
|--------------------|---------------------|-------------------------|
| weekly             | string              | null: false             |
| one_month          | string              | null: false             |
| user               | references          | foreign_key: true       |

- has_one  :user

## comments

| Column             | Type                | Options                 |
|--------------------|---------------------|-------------------------|
| comment_text       | string              | null: false             |
| user               | references          | foreign_key: true       |
| post               | references          | foreign_key: true       |

### Association

- belongs_to :user