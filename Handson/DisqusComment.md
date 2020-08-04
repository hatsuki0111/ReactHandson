# DisqusComment  

disqusで登録してshortnameを控える  
https://coderrocketfuel.com/article/how-to-add-disqus-to-a-react-application  

```
npm install disqus-react --save
```  

```
import Disqus from 'disqus-react'  
```  





```
const Article =(props)=>{

  const disqusShortname = "my-project-8"
  const disqusConfig = {
    url: "http://localhost:3000",
    identifier: "props.data.sys.id",
    title: "props.data.fields.title"
  }
 ```  
 
 mydetailの中  
 
```
  <Disqus.DiscussionEmbed
          shortname={disqusShortname}
          config={disqusConfig}
        />
        ```  
        
