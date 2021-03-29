# docker-rails6-mysql8
## start rails setup
### run rails new
```
$ docker-compose run web rails new . --force --no-deps --database=mysql --skip-test --webpacker
```
### docker image build
```
$ docker-compose build
```
### edit database.yml
config/database.yml
```
default: &default
  adapter: mysql2
  encoding: utf8mb4
  pool: <%= ENV.fetch("RAILS_MAX_THREADS") { 5 } %>
  username: <%= ENV.fetch("MYSQL_USERNAME", "root") %>
  password: <%= ENV.fetch("MYSQL_PASSWORD", "password") %>
  host: <%= ENV.fetch("MYSQL_HOST", "db") %>

development:
  <<: *default
  database: app_development
  
staging:
  <<: *default
  database: app_staging
  
production:
  <<: *default
  database: app_production
  username: app
  password: <%= ENV['APP_DATABASE_PASSWORD'] %>
```
### db create
```
$ docker-compose run web rails db:create
```
### container start-up
```
$ docker-compose up -d
```
### Hello Rails!
access at http://localhost:3000/
### finish
```
$ docker-compose down
```
