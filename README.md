- railsのプロジェクトを作成する
```
docker-compose run web bundle exec rails new . --force --database=mysql
```

- Dockerのimageを作成する
```
docker-compose build
```

- railsのdatabase.ymlを修正する
```yaml
default: &default
  adapter: mysql2
  encoding: utf8mb4
  pool: <%= ENV.fetch("RAILS_MAX_THREADS") { 5 } %>
  username: root
  password:
  host: db　⇦　ここをlocalhostからdbに変更（docker-compose.ymlのmysqlのサービス名）
```

- 起動する
```
docker-compose up
```

- データベースを作成する
```
docker-compose exec web bundle exec rails db:prepare
```

ブラウザでhttp://localhost:3000にアクセスするとRailsのwelcome画面が表示される
