# Top.jsに最新4つのブログが見られるようにする 
# ブログはTitleと更新日だけにする　
# 1つのブログをクリックしたときにブログの詳細が見られるようにする  

Top.jsに最新4つのblogが表示されており、titleとpublishDateとimageが表示されている 1つblogをクリックしてみる  
![blogs](https://user-images.githubusercontent.com/44164993/88716181-a6dcbc80-d159-11ea-9ef7-28323b7f46f2.png)


このように詳細が見られる(Blogs.js)
![blogsDetail](https://user-images.githubusercontent.com/44164993/88716219-b825c900-d159-11ea-8e5e-6edab206b568.png)  

このTop.jsとBlogs.jsを作る  

前回  
![Contentful27](https://user-images.githubusercontent.com/44164993/88716393-f7541a00-d159-11ea-9208-9c73e18d80a2.png)
で終わったため、Top.jsに最新4つのblogを表示させてみる  

contentfulでblogを3つ追加する  
前回の手順を見て  

blogを4つだすためにTop.jsをforで4回  

BlogCardを<BlogCard />でよぶ(BlogCard.jsにtitle publishDate imageが記述されている)  
これで最新4つBlogがTop.jsに表示される  

次にBlogs.jsを作る  
Top.jsのblogから1つクリックすると、そのblogのtitle body image publishDateが表示される  
BlogCardをimportする  
Top.jsのblog idをBlogs.jsでpropsで受け取りそのblog idと紐づけてmapで1つのblogのtitlse body image publishDateを表示させる  



