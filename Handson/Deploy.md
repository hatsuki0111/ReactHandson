# FireBaseにデプロイ  

firebaseでオーナーを追加
firebase login
変なやつがでたら
firebase init
hosting use existing project
what do you want to use build
あとy y
npm run build
firebase deploy


https://note.com/wtnb_dev/n/nccd313a346bf  

https://qiita.com/hiroki-harada/items/ca22ac177db68e3c3796  

firebase  
https://firebase.google.com/?hl=ja  

Travisは.comと.orgのurlがあるが、2018年までpublicレポジトリは.orgでprivateリポジトリが.comだったが解消され、.comですべて完結するようになった。  
↓を使う  
https://travis-ci.com/

~~https://travis-ci.org/~~  



firebase login: cli  
1から始まるトークンコピー  

travisのホームページに行ってsign upし、gitと連携する  
settingでauthorize押して、allrepositoryかrepositoryでt使うrepositoryを指定する  
メニューバーのダッシュボードにうつる  
build triggerを押す  
上にsuccesufullyとかでる  

Travisの方でfirebaseのトークンを使う。  
Environment VariablesでNAMEにFIREBASE_TOKEといれ、VALUEにトークンを入れる。BRANCHはmasterを選択する。  
projectを環境変数にして$変数で渡すべき、

ルートフォルダに.travis.ymlファイルを作る  
```
language: node_js
node_js:
  - "12.3.0"

cache: npm

branches:
  only:
    - master
install: 
  - npm install
script:
  - npm run build
deploy:
  skip_cleanup: true
  provider: firebase
  token:
    secure: "$FIREBASE_TOKEN"
```  

language:で言語指定  
node_js:でversion指定  
cache:は何度もテストするときにキャッシュからとればbuild早くすすむやつ  
branch:
  only:はgithubのpushブランチを指定、この場合はmaster  
install: npm installでnpmアップデートのはず  
script: buildのスクリプト Travis CI は、トリガー毎に仮想マシンが建てられて、その中でバッチが進行するので、環境変数やシェルスクリプトの実行が可能  
deploy: 
　skip_cleanup:trueはscriptで実行したファイルの残すことができる、deploy前にTravisがstashしたものが消えるのを防ぐ  
  provider: firebase　firebaseを使うよdeploy先を指定  
  token:
    secure:　トークンをセキュアで指定  
    
 
 理想は以下の構成にしたい(LOCAL SAWADAさんの)
 ![Sawada](https://user-images.githubusercontent.com/44164993/89112860-61dfbf80-d4a4-11ea-8211-3cd19563833d.png)

    
 Slackにテスト結果を通知させる  
 https://qiita.com/matsuda/items/01707c74c2423958a273  
 

  
