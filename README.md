# 利用方法
1. 本リポジトリをクローン
  ```
  $ cd /path/to/
  $ git clone https://github.com/koreander2001/django-on-docker.git
  ```
2. Djangoのプロジェクト名、アクセスポート番号などを設定
  ```
  $ cp .env.sample .env
  $ vim .env
  ```
3. Dockerイメージのビルド
  ```
  $ docker-compose build
  ```
4. Djangoプロジェクトの生成
  ```
  $ docker-compose run python django-admin startproject {2で設定したDjangoプロジェクト名} .
  ```
5. settins.pyの編集
  ```
  $ vim .src/{2で設定したDjangoプロジェクト名}/settings.py
  ```
  以下を更新・追加する
  ```
  # インポートを追加
  import os

  # DB認証情報を更新
  DATABASES = {
      'default': {
          'ENGINE': 'django.db.backends.mysql',
          'NAME': os.getenv('MYSQL_DATABASE'),
          'USER': os.getenv('MYSQL_USER'),
          'PASSWORD': os.getenv('MYSQL_PASSWORD'),
          'PORT': 3306,
          'HOST': 'db',
      }
  }

  # タイムゾーンを更新
  TIME_ZONE = os.getenv('TZ')

  # 追加
  STATIC_ROOT = '/static/'
  ```
6. Djangoの初期設定
  ```
  $ docker-compose run python ./manage.py migrate
  $ docker-compose run python ./manage.py createsuperuser
  $ docker-compose run python ./manage.py collectstatic
  ```
7. 起動
  ```
  $ docker-compose up -d
  ```
8. 停止
  ```
  $ docker-compose down
  ```

