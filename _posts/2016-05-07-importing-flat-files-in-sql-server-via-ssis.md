---
inFeed: true
hasPage: true
inNav: false
inLanguage: null
keywords: []
description: Importing flat files in SQL Server via SSIS
datePublished: '2016-05-07T22:42:52.211Z'
dateModified: '2016-05-07T22:42:48.629Z'
title: ''
author: []
sourcePath: _posts/2016-05-07-importing-flat-files-in-sql-server-via-ssis.md
authors: []
publisher:
  name: null
  domain: null
  url: null
  favicon: null
starred: false
url: importing-flat-files-in-sql-server-via-ssis/index.html
_type: Article

---
![](https://the-grid-user-content.s3-us-west-2.amazonaws.com/208278bc-6e39-48ec-83a3-06df892d2343.png)

Importing flat files in SQL Server via SSIS

First off, I think this process should be a lot more straightforward than it is and make more use of GUI's but this is Microsoft we are talking about here. 

So after you add a Bulk Insert Task to your SSIS package and specify the flat file to import you must specify a format file to use. Personally, I think it would make everyone's life easier if it just popped up a Edit Mappings option similar to using the Import Data feature in SQL Server. Instead you have to generate a format file that controls the mapping. You can pop open Notepad and create it by hand but of course you'll probably get something wrong. Instead take a trip back to the early 90's and start a dos command to run the BCP(Bulk Copy Program) utility. Type the following in DOS

**BCP database.dbo.tablename format nul -f FORMATNAME.FMT -c -SServerName -UUserName -PPassword **

Substituting database, tablename, FORMATNAME.FMT, ServerName, UserName, and Password with your information. 

**\*\*\*Very important\*\*\*** By default the file will use "\\t" to indicate the fields in your source file is tab delimited. If your file is comma delimited change those to ",". 

Once done I must admit you end up with a nicely formatted format (.fmt) file to specify in SSIS. 

Leave it to Microsoft to make something that should take 5 minutes into a 20-30 minute process. enjoy!
![](https://the-grid-user-content.s3-us-west-2.amazonaws.com/9172d476-bbad-4ee1-88f5-5f553c2291e3.png)