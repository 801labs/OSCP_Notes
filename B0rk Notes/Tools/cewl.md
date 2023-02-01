cewl

Creating Custom Wordlists from a Website

~~~bash
cewl -w customwordlist.txt -d 5 -m 7 www.sans.org
~~~

• -w customwordlist.ext: the -w means write to the file name that follows.  

• -d 5: the depth (in this case, 5) that CeWL will crawl to website.  

• -m 7: the minimum word length; in this case it will grab words of 7 characters minimum.  

• www.sans.org: the website we are crawling. 
