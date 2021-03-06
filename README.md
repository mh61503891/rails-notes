# App Notes

## anyenv

### Rubyのアップデート

```bash
$ anyenv update
$ rbenv install --list
$ rbenv install 2.4.3
$ rbenv rehash
$ rbenv global 2.4.3
```

## Git

### ベアリポジトリの作成

リモートサーバにベアリポジトリを作成する。

```bash
$ ssh server
$ git init --bare /home/git/example.git
$ echo 'Example' > /home/git/example.git/description
$ ln -s /usr/share/git-core/contrib/hooks/post-receive-email /home/git/example.git/hooks/post-receive
$ cd /home/git/example.git
$ git config hooks.envelopesender "user@example.net"
$ git config hooks.mailinglist "user@example.net"
$ git config hooks.announcelist "user@example.net"
```

ローカルサーバにクローンする。

```bash
$ git clone server:example.git
$ cd example
$ git config user.name "User Name"
$ git config user.email "user@example.net"
```
## パッケージマネージャ

|            | yarn              | anyenv        |
| ---------- | ----------------- | ------------- |
| 本体のアップグレード | brew upgrade yarn | anyenv update |

## アップデート

### Node.js

```bash
$ anyanv update
$ ndenv install --list
$ ndenv install v8.9.1
$ ndenv rehash
$ ndenv global v8.9.1
```

## LTS

### Node.js

- [Node.js Foundation Release Working Group Release schedule](https://github.com/nodejs/Release)

# Ruby on Rails

## Path

### Pathの取得

```ruby
Rails.root.join('db/data.csv')
```

## Tasks

### 独自タスクの定義

```ruby
namespace :foo do
  namespace :bar do
    desc 'Bazz'
    task :bazz => :environment do |task, args|
    # bazz
    end
  end
end
```

## Tips

### クラスが自動で読み込まれるパスの追加

```ruby
# config/application.rb
config.autoload_paths << Rails.root.join('app', 'services')
```

```
# showing autoload_paths
$ bin/rails r 'puts ActiveSupport::Dependencies.autoload_paths'
```

* Link: http://qiita.com/necojackarc/items/fb76352dbea5bdd83366
* Link: http://qiita.com/joooee0000/items/369fd4676cd9dfb1f6eb
* Link: http://qiita.com/kbaba1001/items/a1c7db5d97bdff581d7b

### Exceptions

* Link: [rails save! create! update!のバリデーション例外を捕捉する](http://qiita.com/metheglin/items/db595d972df99b3849c2)

## RubyGems

### i18n-js

* GitHub: https://github.com/fnando/i18n-js
* Railsのi18nの訳文ファイルをJavaScriptで使用する場合に便利なgemです。
* Railsの `locales/*.yml` から `translations.js` 書き出すrakeタスクが追加される。
* `translations.js` をJavaScriptから `I18n.t('js.hello');` とかで使用する。
* Rails 5.1でWebpackerが導入されたが訳文ファイルをRailsファーストにするかJavaScriptファーストにするか悩む。
    * ポイント: JavaScriptファーストにする場合はRailsをAPIモードにしてユーザ向けのメッセージを排除できるか？
* Link: http://d.hatena.ne.jp/a_kimura/20120221/1329825267

commands:

```bash
$ rails i18n:js:setup
$ rails i18n:js:export
```

config/i18n-js.yml:

```yml
translations:
  - file: 'app/assets/javascripts/i18n/translations.js'
    only: '*'
```

## JavaScript

### bootstrap-validator

* Demo: http://1000hz.github.io/bootstrap-validator/
* GitHub: https://github.com/1000hz/bootstrap-validator
* Bootstrap 3のフォームのバリデータをHTMLのタグ属性で記述できる。
* JavaScriptのAPIはjQueryベース。Vueとかで使うのはきついだろうか？
