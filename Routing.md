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

Top.jsのページ遷移  
```
<Switch></Switch>の中に  
<Route exact  
    path="/"　　　　　         ルーティングのパス指定  
    render={() => <Top />}>　　Top.jsをレンダリング  
</Route>  
```  

About.jsとContact.jsのページ遷移  
```
<Route exact  
    path="/"　　　　　          
    render={() => <Top />}>　　  
</Route> 
---ここから↓
<Route exact  
    path="/about"　　　　　         ルーティングのパス指定  
    render={() => <About />}>　　Top.jsをレンダリング  
</Route>  
<Route exact  
    path="/contact"　　　　　          
    render={() => <Contact />}>　　  
</Route> 
```  
 
App.jsにimportを追加する  
```  
import Contact from './pages/Contact';  
import About from './pages/About';  
import Top from './pages/Top';  
```  

npm startする  
ブラウザのurlパスをlocalhost:3000/  
windowsは文字化けたまにあり  
localhost:3000/about  
localhost:3000/contactを試し、Top About Contactと変化するのを確認  
