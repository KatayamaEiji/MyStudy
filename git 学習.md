# Git学習
## コマンド
- 初期化　リポジトリ作成
~~~
git init
~~~

- ファイル追加・更新
  ~~~~
  git add .
  ~~~~

- Commit
  ~~~
  git commit -m "メッセージ"
  ~~~

- 変更ファイルを確認
  ~~~
  git status
  ~~~

- リポジトリとワークツリーの差分をチェック
  ~~~~
  git diff
  ~~~~
  > git add 前に変更点を見る

- リポジトリとステージの差分をチェック
  ~~~~
  git diff --cached
  ~~~
  > git 

- ログの確認
  ~~~
  git log
  ~~~

- 元に戻す
  ~~~
  git restore <ファイル名>

  git restore --staged <ファイル名>
  ~~~

- ブランチ作成
  ~~~
  git branch <ブランチ名>
  ~~~

- ブランチ一覧
  ~~~
  git branch

  git branch - a
  ~~~

  > -a : git hubも含めたブランチ

- ブランチ切り替え
  ~~~
  git switch <ブランチ名>

  git switch -c <新規ブランチ名>
  ~~~

  > -c : ブランチを新規作成して切り替える

  - ブランチ
  ~~~~
  git marge <ブランチ名>

  git marge <リモート名>/<ブランチ名>
  ~~~~

## GitHub
- Gitの初期設定
~~~
git config --global user.name "KatayamaEiji"

git config --global user.email katayama.eiji@gmail.com
~~~
- リモートURLの設定
~~~
git remote add origin https://github.com/KatayamaEiji/MyStudy.git
~~~

- PUSH
~~~
git push origin master
~~~

- PULL
~~~
git pull origin master
~~~
