# Top.jsに最新4つのブログが見られるようにする 
# ブログはTitleと更新日だけにする　
# 1つのブログをクリックしたときにブログの詳細が見られるようにする  


※※※Blogを選んでidとひもづけるところが正しく理解できていなためまったくまとめられていません※※※



Top.jsに最新4つのblogが表示されており、titleとpublishDateとimageが表示されている 1つblogをクリックしてみる  
![blogs](https://user-images.githubusercontent.com/44164993/88716181-a6dcbc80-d159-11ea-9ef7-28323b7f46f2.png)


このように詳細が見られる(Article.js)
![blogsDetail](https://user-images.githubusercontent.com/44164993/88716219-b825c900-d159-11ea-8e5e-6edab206b568.png)  

このTop.jsとBlogs.jsを作る  

前回  
![Contentful27](https://user-images.githubusercontent.com/44164993/88716393-f7541a00-d159-11ea-9208-9c73e18d80a2.png)
で終わったため、Top.jsに最新4つのblogを表示させてみる  

contentfulでblogを3つ追加する  
前回の手順を見て  

blogを4つだすためにTop.jsにBlogCardのデータを渡してをforで4回、まわすその時idも引っ張ってくる  
` `に注意{}のなか  

```
const Top =(props)=>{
  let bloglist = ''
  let bloglist2 = []
  if (props.data.length && props.data.length <= 4) {
    bloglist = props.data.map((item,i) => (
      <div key={item.sys.id}>
        <BlogCard data={item} key={i} url={`/blogs/${item.sys.id}`}/>
      </div>
    ))
  } else if (props.data.length) {
    for (let i = 0; i < 4; i++) {
      bloglist2.push(
        <BlogCard data={props.data[i]} key={i} url={`/blogs/${props.data[i].sys.id}`}/>
      )
    }
  } else {
    bloglist = <p>loading...</p>
  }
  return(
  
  
  );
```  

BlogCardを<BlogCard />でよぶ(BlogCard.jsにtitle publishDate imageが記述されている)  
これで最新4つBlogがTop.jsに表示される  
{bloglist}が1~3個までを表示{bloglist2}が4つになるまで足りないblogを表示  


```
 <div id="blogs" className='newBlog'>
        <h2>B<span>L</span>O<span>G</span>S</h2>
        <p className='desc'>サークルのメンバーがブログを更新しています。</p>
        <div className='blogContainer'>
        {bloglist}
        {bloglist2}
        </div>
        <Link to='/blogs' className='moreButton'>
          <p><img src={energy} />MORE...</p> 
        </Link>
      </div> 
```  

次にArticle.jsを作る  
Top.jsのblogから1つクリックすると、そのblogのtitle body image publishDateが表示される  
BlogCardをimportする  
Top.jsのblog idをArticle.jsでblog1つ1つのidをApp.jsからpropsで受け取り、そのblog idと紐づけてmapで1つのblogのtitlse body image publishDateを表示させる  

Top.jsの{bloglist}{bloglist2}をクリックすると<BlogCard data={item} key={i} url={`/blogs/${item.sys.id}`}/>が呼ばれBlogCardそれぞれのidをもったURLでルーティングされ、パスの/blogs/ここ　が作られる     Article.jsはpropsでblogのjsonデータ(idを含む)を渡しており、porpsでblogのidをArticle.jsに渡す. Article.jsは/blog:idがパスになっており、
<Route path="/blogs/:id">と定義したページにアクセスした際に
const { id } = useParams();とすると:idの部分の値を取得できます
App.jsのjson形式のblog　idと　top.jsでblogを押してBlogCardが呼ばれたときのurlのリンクidをArticle.jsでuseParams();と比較する  
blogs.jsはApp.jsからjsonのblogデータをpropsでもってきているそこにURLがある blogs.jsのurl={`/blogs/${item.sys.id}`が必要な理由はArticle.jsのパスが/blogs/:idであるためblogsのurlもidを使うのに必要だから  
BlogCard.jsに<Link>をつける。これでurlが発行される
  ReactMarkdownはもう使わないデータを渡す役割にてっするため  
  
  
```  
 <Route
          exact
          path="/blogs/:id"
          render={() => <Article data={blog}/>}
          />
 ```  
 

Top.jsのArticleのルーティングpathはblog:idにする
data={blog}でデータを渡す  



