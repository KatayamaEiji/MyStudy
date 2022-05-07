
# プロジェクト作成

docker-compose exec web 
docker-compose exec web /bin/bash

mkdir action_trigger
django-admin startproject config .

python3 manage.py startapp accounts

## 初期設定
python manage.py runserver 0.0.0.0:8000

CREATE DATABASE action_trigger_db

## テスト実行
docker-compose exec web bash

cd action_trigger/
python manage.py test

