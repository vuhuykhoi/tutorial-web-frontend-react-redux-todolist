
## INTRO
This is todo-list front-end app. <br/>
This app call an RESTful API.<br/>
Current can GET- ADD- DELETE todotask
- Tech: <br/>
    + ReactJs:
        + Class Component programming<br/>
    + Redux : 
        + component -> actions -> reducer -> store
    + UI component: material-ui
    + build packet: npm<br/>
    + follow MERN stack programing

### DEVELOPMENT
1. Set proxy, must to be a string in package.json file

2. For example
```json
{  
    "proxy": "https://backend.example.com"
}
```
3. Run project
   npm install && npm start || yarn install && yarn start

### DEPLOYMENT
Set Proxy to deloy Heroku:
1. When deploy on heroku, just push only package-lock.json or yarn.lock. Dont push both those files!
    npm install || yarn install

2. Create static.json file
```json
{
    "root": "build/",
    "clean_urls": false,
    "routes": {
        "/**": "index.html"
    },
    "https_only": true,
    "headers": {
        "/**": {
            "Strict-Transport-Security": "max-age=7776000"
        }
    },
    "proxies": {
        "/api/": {
            "origin": "${API_URL}"
        }
    }
}
```
3. Push file to heroku
    git push heroku master

4. Config proxy heroku
All request from react contain "/api/abc" -> "/abc" <br/>
For example:<br/>
From react:    axios.get("/api/search-items")   → ${API_URL}/search-items <br/> 
From react:     axios.get("/api/users/me")   → ${API_URL}/users/me<br/>
(!)Therefore, run this cmd to set proxy var in heroku: <br/>
```js
heroku config:set API_URL="https://backend.example.com/api"
```