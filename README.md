Node.js rapid deployment on Heroku
=================================  
1.下載及安裝 heroku-toolbelt.exe    
    https://devcenter.heroku.com/articles/getting-started-with-nodejs#set-up  
    
2.安裝git  
    https://git-scm.com/downloads  
    
3.打開cmd輸入  
    $heroku login  
    Enter your Heroku credentials.  
    Email: zeke@example.com  
    Password:  
    Authentication successful.  
    
4.建立新的或clone既存的git檔  
  $ mkdir node-js-getting-started  
  $ cd node-js-getting-started  
  $ git init  
  或  
  $ git clone https://github.com/heroku/node-js-getting-started.git  
  $ cd node-js-getting-started  
    
5.在git app裡確認package.json  
  若不存在則建立package.json檔  
	{  
	"name": "testnode",  
	"version": "0.0.1",  
	"main": "node_express_test.js",  
	"dependencies": {  
		"express": "4.13.x"  
		},  
	"engines": {  
		"node": "0.12.7",  
		"npm": "2.11.3"  
		}  
	}
  /\*註:node --version及npm --version取得版號\*/  
    
6.在git app裡確認Procfile檔  
  web: node node-js-getting-started  
    
7.安裝nodejs所使用的lib  
  Ex. npm instll express  
    
8.修改.gitignore檔  
  $ echo node_modules  .gitignore  
    
9.在heroku上佈署app  
  $ heorku create --stack cedar  
    
10.建立BuildPacks  
  $ heroku buildpacks:set https://github.com/heroku/heroku-buildpack-nodejs  
    
11.新增或修改git app的內容  
  $ git add .  
  $ git commit -m "update"  
  $ git push heroku master  
    
12.如果上沒問題的則, ensure that at least one instance of the app is running.  
  $ heroku ps:scale web=1  
    
13.直接開啟web,到此完工  
  $ heroku open  
    
14.查看log  
  $ heroku logs  
    
15.注意程式邏輯  
	var server = app.listen(process.env.PORT || 3000, function(){  
		console.log('listening on', server.address().port);  
	}); 

16.修改已上傳的apps  
  $ heroku git:clone -a mason-restful
  $ cd mason-restful  
