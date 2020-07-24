# Contentful  
Contentfulの説明(headlessCMS 無料枠)  
使いかた  
https://app.contentful.com/  
Googleアカウントでログイン gitでもなんでもいい  

画像で説明  

sdkを入れる  
npm install contentful  
npm install react-contentfulのどっちか  

constantsの中にcontentful.jsを作る  
```
-constans
 -contentful.js
 export default{
 space: 'kokoniireru',
 accessToken: 'kokoniirerunndayo'
 }
 ```  
 apikey書く
 git push時はignoreで指定だけどま別に大丈夫
App.js  
import * as contentful from "contentful";
contentfulを使うと自動import  
import ApiKey from './constants/contentful';  
後述するconst client = contentful.createClietnt(ApiKey)  
のApiKeyはimport Apikey from 'パス'のApiKeyと同じ名前  

React Hookを使う  
```
const App =()=>{
  const client = contentful.createClient(ApiKey)
  const [blog, setBlog] = useState([])
  useEffect(() => {
    client
      .getEntries({
        order: '-sys.createdAt',
        'sys.contentType.sys.id': 'blog'
      })
      .then((res) => setBlog(res.items))
  },[])
  return(
    <BrowserRouter> 
      <Navbar/>
 ```  

import React ,{useState, useEffect} from 'react';


-components  
  -BlogCard.jsをいじる  
  
-pages  
 -Top.js　
 
 
 ToDo
  map hook
