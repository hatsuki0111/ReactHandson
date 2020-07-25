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

App.jsにrouterをいれる  npm install react-router-dom(react-routerは古い)  

import { BrowserRouter, Switch, Route } from 'react-router-dom';を追加するfunction App(){}は古いのでconst App =()=>{}にする  


```
<BrouserRouter>  
   <Switch>  
   </Switch>  
</BrouseRouter>  
```  
<Navbar />を<BrouserRouter>の下にに(Navbarとは)  
<Footer />を</BrouserRouter>の上にに(Footerとは)  

```
<BrouserRouter>  
  <Navbar />  
   <Switch>  
   </Switch>  
   <Footer />  
</BrouseRouter>  
```  

importを追加  
import Navbar from './components/Navbar';  
import Footer from './components/Footer';  

```
<Switch>の中に  
<Route exact  
    path="/"　　　　　ルーティングのパス指定  
    render={() => <Top />}>　　Top.jsをレンダリング  
</Route>  
```  

  
```
以下About Contactも同じ  
importを追加する  
import Contact from './pages/Contact';  
import About from './pages/About';  
import Top from './pages/Top';  
```  



npm startする  
ブラウザのurlパスをlocalhost:3000/  
windowsは文字化けたまにあり  
localhost:3000/about  
localhost:3000/contactを試し、Top About Contactと変化するのを確認  
