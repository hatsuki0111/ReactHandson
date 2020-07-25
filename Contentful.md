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
-constans
 -contentful.js  
 
```
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

import React ,{useState, useEffect} from 'react';する  

コードはおまじない
コード説明は今後追記します2020/7/25  

-components  
  -BlogCard.jsをいじる  
  
  ```
  import React from 'react'
import ReactMarkdown from 'react-markdown';

const BlogCard =(props)=>{
  return(
    <>
    <div className='blogCard'>
    <div onClick={()=>console.log(props.data)}>clg</div>
      <img src={props.data.fields.image.fields.file.url}/>
      <h3>{props.data.fields.title}</h3>
      <p className='publishDate'>{props.data.fields.publishDate}</p>
      <ReactMarkdown className='body'>{props.data.fields.body}</ReactMarkdown>
            
    </div>
    </>
  )
}

export default BlogCard
```  

引数propsでブログのデータ  

Contentfulのマークダウンをhtmlにする
```
npm i react-markdown
```  
classNameはStyleかな？

```
<div onClick={()=>console.log(props.data)}>clg</div>
```  
はクロームのデベロッパーツールのコンソールでjsonの確認
props.data.???.???とか探す
Contentfulでブログ作ったときのtitle body image publishDateがjsonになっている

```
<img src={props.data.fields.image.fields.file.url}/>
```  
は画像srcにjsonデータのurlを入れる
Contentfulの画像がDRAFTになっていることがあるのでPublishかどうかを確認する  
```
<h3>{props.data.fields.title}</h3>
```  
タイトルのjsonをh3タグに入れる
```
<p className='publishDate'>{props.data.fields.publishDate}</p>
```  
pタグにjsonのpublishDateを入れる
```
<ReactMarkdown className='body'>{props.data.fields.body}</ReactMarkdown>
```  
jsonのbodyをReactMarkdwonに入れることでマークダウンをhtmlに直す  

<></>はなに？  


-pages  
 -Top.js　
 ```
 import React from 'react'
import BlogCard from '../components/BlogCard';

const Top =(props)=>{
  return(
    <>
      
      <div className='top'>Top</div>
      <div onClick={()=>console.log(props.data)}>clg</div>
        
        <p>{props.data.length ? props.data.map((item,i)=>(
          <BlogCard data={item} key={i}/>
        )): 
          (<p>Now Loading...</p>)}
        </p>
    </>
  )
}

export default Top
```  

importBlogcardする
引数props
mapでjson配列のtitle bodyなどを全部出力でBlogCard.jsを呼び出しその中でレンダリングかな？  
<Now Loading>はデータとっている待ち時間にhtmlに表示  
 
 
 ToDo
  map hook
  exportしたやつは他のファイルでimportできる
