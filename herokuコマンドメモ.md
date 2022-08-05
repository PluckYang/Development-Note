### 教程：https://trailhead.salesforce.com/ja/content/learn/trails/heroku_enterprise その内:
#### [Heroku Enterprise](https://trailhead.salesforce.com/ja/content/learn/modules/heroku_enterprise_baiscs?locale=ja&trail_id=heroku_enterprise)はheroku基礎
#### [Heroku Flow](https://trailhead.salesforce.com/ja/content/learn/modules/heroku-flow?locale=ja&trail_id=heroku_enterprise)はgithubブランチを利用し、herokuアプリを開発用、テスト用、本番環境とのリリースフローを説明
#### [Salesforce に統合する Heroku アプリケーションの開発](https://trailhead.salesforce.com/ja/content/learn/projects/develop-heroku-applications?locale=ja&trail_id=heroku_enterprise)はsalesforceとherokuの実践の例

- 今パソコンのheroku　versionを表示 `heroku --version`
- リモートheroku環境に接続 `heroku login`
- ローカル環境のユーザを表示 `heroku auth:whoami`
- リモート環境でアクセスできるAPPリストを表示 `heroku apps`
- ロモートAPPの情報を確認 `heroku apps:info APP名`
- すべてのdyno(コンテナ)で実行されないよう `heroku ps:scale web=0 -a your_app’s_name`
- Web でアプリケーションを開く `heroku open -a your_app’s_name`（ブラウザ画面に飛ぶ、dyno=0の時アプリは作動しない）
- dynoの数を１にする`heroku ps:scale web=1 -a your_app’s_name`
- ロモートのappをローカルにプルダウン、そしてローカル環境をリモート環境に接続
  `git clone https://github.com/heroku/node-js-getting-started your_app’s_name`
  `cd your_app’s_name`
  `heroku git:remote -a your_app’s_name`
- ローカル環境でAPP中身修正した後、修正された資材に対してcommitし、リモート環境へ反映する 
  `git commit -am "my first heroku push"`
  `git push heroku main`

- herokuに繋がったGitHubに一つのappコードを保存のしたrepositoryの内容を、appとしてherokuで作成したい場合、ブラウザで以下のリンクを訪問↓：
  `https://heroku.com/deploy?template=https://github.com/『YOUR_GitHub_USERNAME』/intro-to-heroku`
  そしてAPP名前を入れ、github倉庫と繋がったapp作成される。ただし、作成されたappは倉庫に繋がってい無いので、app詳細の「Deployment method」で「github」を選んで、倉庫に繋ぐ必要がある
  
- 倉庫のreadmeファイルに、herokuへ資材をdeployするボタンを追加には、readmeに以下のコードを入れる：
  `<a href="https://heroku.com/deploy"><img src="https://www.herokucdn.com/deploy/button.svg" alt="Deploy"></a>`
  
- heroku上、新しappを作成の時、app名に`dhprod-UNIQUE_ID`を入れると、自動的にアプリケーション名の UNIQUE_ID を一意の ID に置き換えます
