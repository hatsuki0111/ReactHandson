# Google Analyticsの導入方法  

Google Analytics  
https://analytics.google.com/  


GoogleAnalyticsにログインしてトラッキング情報を発行のとこまでは以下サイト参照
https://web-kanji.com/posts/google-analytics-setting  

react-gaをインストールする
```
npm install react-ga --save
```  

App.jsに以下のコードを書く  
```
import React from 'react';
import { BrowserRouter, Switch, Route } from "react-router-dom";
import ReactGA from 'react-ga';
import createBrowserHistory from 'history/createBrowserHistory';
 
 //Google Analytics部分
ReactGA.initialize('[トラッキングコード]');
const history = createBrowserHistory();
history.listen(({ pathname }) => {
  ReactGA.set({ page: pathname });
  ReactGA.pageview(pathname);
});
 
render(
       <BrowserRouter history={history}> ///historyを渡す  
         <Switch>
           <Route .../>
           <Route .../>
         </Switch>
       </BrowserRouter>,
       document.getElementById('root')
)
```  


react-gaは最新のgtag.jsではなくanalytics.jsが使われている  
https://qiita.com/mildsummer/items/184315e6f9a6d298113e  

not defind　undefみたいなのでたら  
npm install -S しようぜ  
import {createBrowserHistroy} from 'history'   

