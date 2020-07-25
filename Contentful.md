# Contentful  
Contentfulの説明(headlessCMS 無料枠)  
使いかた  
https://app.contentful.com/  


![Contentful1](https://user-images.githubusercontent.com/44164993/88462542-0e3f0600-cee7-11ea-85f0-c7c587000170.png)  

Googleアカウントでログイン gitでもなんでもいい  


![Contentful2](https://user-images.githubusercontent.com/44164993/88462551-26af2080-cee7-11ea-882b-e3608f6a98db.png)

Add Spaceを押す  

![Contentful3](https://user-images.githubusercontent.com/44164993/88462571-5827ec00-cee7-11ea-89c3-77660c83b5f6.png)  

community 0/1 free spaceを押す  

![Contentful5](https://user-images.githubusercontent.com/44164993/88462621-b48b0b80-cee7-11ea-8406-e3c59ea17723.png)  

Space nameに名前を入れる。create an empty spaceを選択。procced to confirmationを押す  

![Contentful6](https://user-images.githubusercontent.com/44164993/88462631-d8e6e800-cee7-11ea-9eae-884a239e906d.png)

confirm and create spaceを押す  

![Contentful7](https://user-images.githubusercontent.com/44164993/88462663-1ea3b080-cee8-11ea-92ee-3fdef4e23464.png)  

上のメニューバーのcontent modelを押す

![Contentful8](https://user-images.githubusercontent.com/44164993/88462697-46931400-cee8-11ea-86b1-3523db789974.png)  

Nameに名前を入力。今回はblogとする。createを押す  


![Contentful9](https://user-images.githubusercontent.com/44164993/88462724-6d514a80-cee8-11ea-86fd-c59ab93f847b.png)  

add fieldを押す  

![Contentful10](https://user-images.githubusercontent.com/44164993/88462752-9e317f80-cee8-11ea-9da2-7717a7223ed3.png)  

Textを選択する  

![Contentful11](https://user-images.githubusercontent.com/44164993/88462780-e51f7500-cee8-11ea-8da7-8bd38f105399.png)  

Nameにtitleと入力(ブログのタイトルとなる)。short textを選択する。 createする。  

![Contentful12](https://user-images.githubusercontent.com/44164993/88462797-008a8000-cee9-11ea-9bd3-885a6711593d.png)  

同様にadd fieldでTextを選択し、titleのようにbodyも作成する(ブログの本文となる)。  


Date and Timeを選択する。  

![Contentful13](https://user-images.githubusercontent.com/44164993/88462832-40516780-cee9-11ea-80ed-a3caf157e75a.png)

NameにpublishDateと入力(ブログの投稿日時となる)。

![Contentful14](https://user-images.githubusercontent.com/44164993/88462840-552dfb00-cee9-11ea-8c51-7d2c497c99cb.png)  


medhiaを選択する。  

![Contentful15](https://user-images.githubusercontent.com/44164993/88462878-b3f37480-cee9-11ea-8849-3567686a1ecc.png)  


Nameにimageと入力する(ブログの画像となる)。createを押す  

![Contentful16](https://user-images.githubusercontent.com/44164993/88462898-db4a4180-cee9-11ea-84ae-c52405a08110.png)


右上のsaveを押す。上のメニューバーのcontentを押す   

![Contentful17](https://user-images.githubusercontent.com/44164993/88462924-0896ef80-ceea-11ea-8a6b-0f2699851ad4.png)  

記念すべき1記事目を書こう! Titleにブログ記事のタイトル。bodyに本文(マークダウン形式)。publishDateに時間を設定する(00:00でよい)。imageを押す  
 

![Contentful18](https://user-images.githubusercontent.com/44164993/88462942-2bc19f00-ceea-11ea-9d96-8e38a976e152.png)  


imageのTitleを入力する。open file selectorを押す  

![Contentful19](https://user-images.githubusercontent.com/44164993/88462972-6b888680-ceea-11ea-814c-7ee5cff8d8e6.png)  

WebSearchをクリックし、適当な名前で検索し、画像を選ぶ  

![Contentful20](https://user-images.githubusercontent.com/44164993/88463051-fd908f00-ceea-11ea-8929-19b90e5b2e69.png)  


右上のDRAFTを押し、Publishを選択する。画像の右上がDRAFTと黄色くなっていたら、画像の右上の...をクリックし、Publishに変える  

![Contentful21](https://user-images.githubusercontent.com/44164993/88463085-20bb3e80-ceeb-11ea-9eb2-56e85dd93a54.png)  


上のメニューバーのSettingを押し、API Keyを選択  

![Contentful23](https://user-images.githubusercontent.com/44164993/88463145-92938800-ceeb-11ea-9f97-944d77ec959c.png)  

 右上のAdd API Keyを選択  

![Contentful24](https://user-images.githubusercontent.com/44164993/88463157-b48d0a80-ceeb-11ea-9647-46a927a90212.png)  

API Keyをメモするかなどで覚えておく(後で使う)  

![Contentful25_LI](https://user-images.githubusercontent.com/44164993/88463186-f5851f00-ceeb-11ea-8ce5-afec9b2a3fbc.jpg)  


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
classNameはStyleで必要 通常のcssのclassだとjsとの関係でコンピューターが勘違いするため、classNameを使用  

```
<div onClick={()=>console.log(props.data)}>clg</div>
```  
はクロームのデベロッパーツールのコンソールでjsonの確認
props.data.???.???とか探す
Contentfulでブログ作ったときのtitle body image publishDateがjsonになっている
clgはEmmet  

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

<></>はreturn()の中は複数のタグ？を返せないので全体を<></>と囲んで一つとみなす  


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
mapでjson配列のtitle bodyなどを全部出力でBlogCard.jsを呼び出しその中でレンダリングする  
<Now Loading>はデータとっている待ち時間にhtmlに表示  
 
 exportしたやつは他のファイルでimportできる  
 
