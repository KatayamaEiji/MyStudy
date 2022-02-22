# linux コマンド

- ファイルの中身を確認  
`les`  
`cat`

# Docker

## Docker image
- イメージの一覧
  ~~~
  docker image ls
  ~~~

- イメージ作成
  ~~~
  docker image build -t sample/sinatra:latest .
  ~~~

- イメージ削除


## Docker Container
- コンテナー作成

- コンテナー削除

- コンテナー起動
  ~~~
  docker container run -it -p 4567:4567 --name sinatra -v ${PWD}/src:/var/www sample/sinatra:latest
  ~~~

  > -it : インタラクティブモードで起動（双方向）

  > -v : ローカルのsrcフォルダ内のファイルと、コンテナ内の/var/wwwのファイルを同期させる。

  ~~~
  docker container run -d -p 8000:8000 --name webrick sample/webrick:latest
  ~~~

  > -d : バックグランドで稼働

- コンテナー停止
  ~~~
  docker container stop webrick
  ~~~

- 稼働しているコンテナ上でコマンドを実行
  ~~~
  docker container exec webrick ruby -v
  ~~~

- 稼働していないコンテナを削除
  ~~~
  docker system prune -a
  ~~~

## bash 
~~~
bundle config --local set path 'vendor/bundle'
~~~

~~~
bundle install
~~~


# docker compose
- composeとは
  > Docker compose とは、複数のコンテナから成るサービスを構築・実行する手順を自動的にし、管理を容易にする機能です。

- サービスのビルド
  ~~~ 
  docker-compose build
  ~~~

  > ※サービスとは、docker-compose.yml　に記載されている "services"に定義したサービスをビルドする。（存在しない場合はプルしてからビルドする）

- サービス作成と起動
  ~~~
  docker-compose up -d
  ~~~

  >docker-compose.ymlに書かれているサービスを参考にコンテナを作成し、起動します。

  > -d : バックグラウンド稼働

- サービスをコンテナを停止・削除
  ~~~
  docker-compose down
  ~~~

  >docker-compose.ymlに書かれているサービスを参考にコンテナを停止し、そのコンテナとネットワークを削除します。  
オプションで--rmi allをつけることでイメージも削除してくれます。

- コンテナの一覧
  ~~~
  docker-compose ps
  ~~~

- ログを表示
  ~~~
  docker-compose logs
  ~~~

- コンテナを作成してコマンドを実行
  ~~~
  docker-compose run <サービス><コマンド>
  ~~~

- 起動中のコンテナにコマンド実行
  ~~~
  docker-compose exec <サービス><コマンド>'`
  ~~~

  - Bashを起動)
    ~~~
    docker-compose exec web /bin/bash
    ~~~

- doceker compose で作成したすべてのイメージ、コンテナを削除する
  ~~~
  docker-compose down --rmi all --volumes --remove-orphans`
  ~~~



---
# Ruby関連
## Gemとは
> GemはRubyでのライブラリーの意味。

## bundlerとは
> Gemを管理するGem(ライブラリー)の名称。

## gemfile,gemfile.lock
> "gemfile"はbundlerがインストールするgemとそのバージョン情報を設定します。
>
> "gemfile.lock"は"gemfile"で設定したgemと依存関係のあるgemの情報について設定します。

## rails 環境の作成
~~~docker
docker-compose run web rails new . --force --database=mysql
docker-compose run web bundle install
docker-compose run web rails db:create
~~~

