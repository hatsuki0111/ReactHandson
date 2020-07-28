# ルーティング
ルーティングとは？

srcフォルダの中に
```
-conponents
-pages
-static/css
```  
のフォルダをつくる  

componentの説明  

-conponentsにNavbar.js Footer.jsを作成  

-pagesにTop.js About.js Contact.jsを作成(Class extendsとかrender()とかは古い)  

App.jsの中身を消して以下のコードをApp.jsに書く  
```
import React from 'react'

const App =()=>{
return(
  <div>hello world</div>
);
}
export default App
```  
ブラウザでhello worldを確認  


App.jsにrouterをいれる(react-routerは古い)  
```
npm install react-router-dom  
```  
App.jsにimportを追加する  
```
import { BrowserRouter, Switch, Route } from 'react-router-dom'
```
App.jsの中にRoutingを書くfunction App(){}は古いのでconst App =()=>{}にする    

```
import React from 'react'

const App =()=>{
return(
<BrowserRouter>  
  <Navbar />  
   <Switch>  
   </Switch>  
   <Footer />  
</BrowseRouter>
);
}
export default App
```  

importを追加  
import Navbar from './components/Navbar'  
import Footer from './components/Footer'  

Top.jsのページ遷移をする  
Top.jsを作る  
```
import React from 'react'

const Top =()=>{
return(
  <div>Topだお</div>
);
}
export default Top

```  


App.jsの中にTop.jsのルーティング処理を書く  
```
<Switch></Switch>の中に  
<Route exact  
    path="/"　　　　　         ルーティングのパス指定  
    render={() => <Top />}>　　Top.jsをレンダリング  
</Route>  
```  

blogs.jsのページ遷移をする  
Top.js同様にpagesフォルダの中にBlogs.jsファイルを作る  
App.js  
```
<Route exact  
    path="/"　　　　　          
    render={() => <Top />}>　　  
</Route> 
---ここから↓
<Route exact  
    path="/blogs"　　　　　         ルーティングのパス指定  
    render={() => <Blogs />}>　　Blogs.jsをレンダリング  
</Route>  
```  
 
App.jsにimportを追加する  
```    
import Blogs from './pages/Blogs';  
import Top from './pages/Top';  
```  

npm startする  
ブラウザのurlパスをlocalhost:3000/にする  
Top.jsが見れることを確認  

windowsは文字化けたまにあり  
localhost:3000/blogs  
Blogs.jsが見れることを確認する  
