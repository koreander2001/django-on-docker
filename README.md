# 利用方法
1. 本リポジトリをクローン
  ~~~
  $ cd /path/to/
  $ git clone https://github.com/koreander2001/django-on-docker.git
  ~~~
2. Djangoのプロジェクト名、アクセスポート番号などを設定
  ~~~
  $ cp .env.sample .env
  $ vim .env
  ~~~
3. 下記コマンドを実行
  ~~~
  $ docker-compose build
  $ docker-compose up -d
  ~~~

# 参考URL
* [DjangoをDocker Composeでupしよう！](https://qiita.com/kyhei_0727/items/e0eb4cfa46d71258f1be)
* [docker-composeのビルド中に環境変数が認識されない](https://qiita.com/katoosky/items/422c183cf5cabb789030)
* [Djangoの設定をHerokuの環境とローカルの環境で分ける方法](https://yoshitaku-jp.hatenablog.com/entry/2018/09/02/004857)

