# TwitterShareボタンの作成  

```
npm i react-share
```  

Article.js  

import { useParams, useLocation } from 'react-router-dom'  
指定したブログのurlをuseLocationで取得するためにimportする  


import { 
  TwitterShareButton, 
  TwitterIcon
} from 'react-share'

twittershareのimport  

const Article =()=>{
  const location = useLocation();  //urlを取得
}
  
  urlにuseLocationで取得したものを入れる
  TwitterIconでボタン表示
  mydetail()の中に置く  
<TwitterShareButton url={location.pathname} >
                    <TwitterIcon size={32} round />
        </TwitterShareButton>
