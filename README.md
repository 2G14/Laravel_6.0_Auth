# Laravel 6.0  Auth

Laravel 6.0 時点でのAuth実装方法の調査をまとめる.

## 実装手順

デフォルトのユーザテーブルのemailとpasswordを使用した認証機能をLaravelに付与するまでの実装手順

```bash
$ laravel new [app_name]
$ cd [app_name]
$ composer require laravel/ui
$ php artisan ui vue --auth
$ php artisan migrate
$ npm install
$ npm run dev
```

## 各種変更方法

### email以外での認証

`app/Http/Controllers/Auth/LoginController.php` に使用するカラム名のfuncitonを追加  
`resources/views/auth/login.blade.php` のemailの箇所を追加したカラム名に変更  

### Usersテーブル以外での認証

デフォルトのUserモデルを元に使用するテーブルに対応するモデルファイルを作成  
`config/auth.php` の `App\User::class` を作成したモデルファイルに置き換える  

### パスワードのハッシュ化

LaravelはBcryptとArgon2ハッシュを提供している.  
設定方法は[Laravel 6.0 ハッシュ](https://readouble.com/laravel/6.0/ja/hashing.html)に記載されている.
