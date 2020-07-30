# Blogs.jsでblogの一覧を表示する  

moreボタンを押すとblog一覧のBlogs.jsに飛ぶ  
![blogs](https://user-images.githubusercontent.com/44164993/88716181-a6dcbc80-d159-11ea-9ef7-28323b7f46f2.png)  

Blogs.jsが表示される  
![blogs jsl](https://user-images.githubusercontent.com/44164993/88719727-b6123900-d15e-11ea-8680-beb6cf40369e.png)  

この一連の流れをやる  
 
 
Blogs.jsで一覧をmapで表示する  
```
import React from 'react'
import BlogCard from '../components/BlogCard'

const Blogs =(props)=>{
  return(
    <>
    <div>Blogs</div> <p className='blogsGrid'>{props.data.length ? props.data.map((item,i)=>(
      <BlogCard data={item} key={i}/>
    )): 
      (<p>Now Loading...</p>)}
    </p>
    </>
  );
}

export default Blogs
```  

Top.jsにmoreボタンをつくる  
```
<Link to='/blogs' className='moreButton'>
          <p><img src={energy} />MORE...</p> 
        </Link>
 ```  
 
 App.jsにdata={blog}を渡す  
 
 ```
 <Route exact
      path="/blogs"
      render={() => <Blogs data={blog}/>}>
    </Route>
    ```  
    
    
    
 
