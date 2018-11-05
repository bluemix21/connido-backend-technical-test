## Article Backend Rest API

This git hub repository has *Article CRUD REST API* implementation using Typescript, ES6, MongoDB and Node JS.

This Atricle API conatins functions like create, read, update, delete Articles and Search articles based on Author and/Or Title.

  

#### Article Model :
```javascript
article {
  keywords :
  title: {
    type: String
  },
  content: {
    type: String
  },
  author: {
    type: String
  },
  created_date : {
    type: Date
  },
  updated_date : {
    type: Date    
  }
}
```

## Development environment setup

### Prerequisites :

 Make sure Mongo DB is up and running.
 Make sure Node JS and NPM is installed.
 
Run the following commnads in a terminal :
```sh
git clone https://github.com/bluemix21/connido-backend-technical-test.git

npm install

```

### Update config.js file

 Please alter the config.js file based on mongo db url, mongo db test url and node server port.
```javascript
{    
    "port": 3001,
    "mongo_url": "mongodb://localhost/articledb",
	"mongo_url_test": "mongodb://localhost/articledb_10"
}

```

### Start the Node server
```sh

npm run dev

```

API will be hosted on localhost:3001/api/article


## API documentation


### Create article

	POST /api/article

#### Parameters

| Name    | Type      | Description                          |
|---------|-----------|--------------------------------------|
| title			| 			|  <p>Article's title.</p>							|
| content			| 			|  <p>Article's content.</p>							|
| author			| 			|  <p>Article's author.</p>							|

created_date and created_date properties will be automatically updated by REST API

```sh

Request Type : post
URL: http://localhost:3001/api/article
body:{"title": "Article Title","content": "Article Content","author": "Article_Author"}

```



### Delete article

	DELETE /api/article/:id
```sh

Request Type : delete
URL: http://localhost:3001/api/article/5bdd6189b080427a5070d0b5

```



### Retrieve article by Id

	GET /api/article/:id

```sh

Request Type : get
http://localhost:3001/api/article/56c787ccc67fc11a5e92
  
```


### Retrieve articles using pagination 
	GET /api/article

#### Parameters

	GET /api/article?limit=3&skip=2

    limit - if limit is set to 3 then limit parameter will return only 3 articles.
	skip - if skip is set to 2 then application will not select first 2 item from the list.

```sh

Request Type : get
URL: http://localhost:3001/api/article?limit=3&skip=2

```

### Update article
	PUT api/article/:id


#### Parameters

| Name    | Type      | Description                          |
|---------|-----------|--------------------------------------|
| title			| 			|  <p>Article's title.</p>							|
| content			| 			|  <p>Article's content.</p>							|
| author			| 			|  <p>Article's author.</p>							|

```sh

Request Type : PUT
URL: http://localhost:3001/api/article/5bdd859045aa8c06a82b0b89
body:{"title": "Article Title","content": "Article Content","author": "Article_Author"}

```

### Retrieve articles By Author 
	GET /api/articleByAuthor?author=tomcruise

#### Parameters

	GET /api/articleByAuthor?author=tomcruise

    author - Provide Author name to find list of atricles under an Author.

```sh

Request Type : get
URL: http://localhost:3001/api/articleByAuthor?author=tomcruise

```

### Retrieve articles By Article Title 

	GET /api/articleByTitle?title=sampleTitle

#### Parameters

	GET /api/articleByTitle?title=sampleTitle

    title - Provide Title to find list of atricles under the title.

```sh

Request Type : get
URL: http://localhost:3001/api/articleByTitle?title=sampleTitle

```

### Retrieve articles By Article Title And/Or Title

	GET /api/articleByAuthorAndOrTitle?title=orkut 1212&author=cook tom&condition=and

#### Parameters

	GET /api/articleByAuthorAndOrTitle?title=orkut 1212&author=cook tom&condition=and

    title - Provide Title to find list of atricles under the title.
	author - Provide Author name to find list of atricles under an Author.
	condition- valid values are 1) AND 2) OR
	

```sh

Request Type : get
URL: http://localhost:3001/api/articleByAuthorAndOrTitle?title=orkut 1212&author=cook tom&condition=and
URL: http://localhost:3001/api/articleByAuthorAndOrTitle?title=orkut 1212&author=cook tom&condition=or

```

## UnitTesting

mocha and Chai has been used to do testing. 

Please configure different database for testing so that it will affect dev database.

To configure testing database please complete below stesps.

1)set below environment variable in the test console/terminal, if not set then application will insert data in development database.

For Windows
```sh
set NODE_ENV=test
```

2)Alter config.js file with valid test database, this file located in the root folder.


#### Running the test suites
```sh
npm run test
```



