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
