# Google Analyticsの導入方法  

GoogleAnalyticsにログインしてトラッキング情報を発行のとこまでは以下サイト参照
https://web-kanji.com/posts/google-analytics-setting  

react-gaをインストールする
```
npm install react-ga --save
```  

App.jsに以下のコードを書く  
```
import React from 'react';
import { Router, Route, Switch } from 'react-router-dom';
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
       <BrowseRouter history={history}> ///historyを渡す  
         <Switch>
           <Route .../>
           <Route .../>
         </Switch>
       </BrowseRouter>,
       document.getElementById('root')
)
```  
