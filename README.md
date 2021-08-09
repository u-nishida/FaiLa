# Faila

![recording (2)](https://user-images.githubusercontent.com/62362974/128688691-84f733a3-c76e-4771-a35a-c1312ec1530c.gif)

## :sparkler: Overview

つぶやきや記事の投稿によって失敗を共有するSNS

## :earth_americas: AppURL

https://faila.herokuapp.com/


## :pencil2: Description

- 記事を投稿する
  - Markdown記法が使える
  - リアルタイムに変化するプレビュー付き
- つぶやきを投稿する
  - 画像を4枚まで付加することができる
- 他のユーザをフォローする
- 記事にコメントする
- つぶやき、記事、コメントにいいねする
- つぶやきに返信する
- いいね、フォローなどの通知を受け取る
- ユーザ、投稿を検索する
- タイムラインで最新の投稿をチェックする
- Twitter、Googleアカウントを利用してログイン
- スマートフォン、タブレット端末でもデザインが崩れない


#### ・返信機能

<img width="1000" alt="スクリーンショット 2021-08-09 20 49 59" src="https://user-images.githubusercontent.com/62362974/128701830-80f9045b-1dda-4fe3-aee4-1fcc21a4ced9.png">

---
#### ・レスポンシブデザイン

<img width="300" src="https://user-images.githubusercontent.com/62362974/128711077-e0d9b6cb-f8bd-44c1-a4d3-47176b0dbd55.PNG">

---

#### ・ER
<img width="1000" src="https://user-images.githubusercontent.com/62362974/128689107-9a7cff26-a10f-42c8-a3f6-bfb623f57b62.png">

---

## 使用技術・仕様の説明

※該当コードへのURLを載せているので是非ご覧ください。

### 使用技術
| 名称 | 説明 |
| ---- | ---- |
| Ruby on Rails | フルスタックフレームワーク |
| JQuery | JavaScriptライブラリ |
| Vue.js | フロントエンドフレームワーク(プレビュー機能に使用) |
| Heroku | ホスティング |
| AWS S3 | オンラインストレージ(画像保存用に使用) |
| Twitter API, Google API | OAuth認証に利用 |
| Rspec | テスティングフレームワーク |

- 基本的にRailsを使用して開発、部分的にJQuery、Vue.jsを導入
- ViewはHamlを使用して記述
- S3にはアイコン画像、つぶやきに添付された画像を保存

### 仕様・工夫した点

※細かい仕様は[アプリのフッターのヘルプ](https://faila.herokuapp.com/help)に記載しています。  

- 返信は再帰的にViewをレンダリングすることによって、正しい順番で表示
  - [該当コード](https://github.com/nizi24/FaiLa/blob/master/app/views/replies/_replies.html.haml#L3-L8)
- 返信するときに自動的に付加される(ユーザーが自分でつけることもできる)ユーザーIDはリンクになる
  - @user1 みたいなのがつぶやきに含まれていた場合、そのユーザーのプロフィールへのリンクに自動的に変化するようにしている
  - [該当コード(helper、リンクに使用するためのIDを探すためのメソッド)](https://github.com/nizi24/FaiLa/blob/master/app/helpers/microposts_helper.rb#L7-L18)
  - [該当コード(View、呼び出す側)](https://github.com/nizi24/FaiLa/blob/master/app/views/microposts/_micropost_detail.html.haml#L28-L32)
- 投稿に@から始まるユーザIDが含まれているか、返信ボタンから他の投稿へ返信したときには、返信として扱われる
  - [該当コード(@userみたいなのが含まれるか判定し、メソッドを呼び出す)](https://github.com/nizi24/FaiLa/blob/master/app/controllers/microposts_controller.rb#L17-L25)
  - [該当コード(リプライを作成するメソッド)](https://github.com/nizi24/FaiLa/blob/master/app/controllers/microposts_controller.rb#L59-L92)
- いいね、フォローなどはAjaxを使って実装
  - [該当コード例(いいね)](https://github.com/nizi24/FaiLa/blob/master/app/views/likes/create.js.haml#L1)





## 👀 Author

- [Twitter](https://twitter.com/nizi_24a)
- [Qiita](https://qiita.com/nizi24)

