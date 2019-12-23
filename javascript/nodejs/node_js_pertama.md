# node pertama

`npm install express`

`npm install mysqljs/mysql`

`npm install cors`

`npm install body-parser`


###f implementation
```javascript
const express = require('express')
const path = require('path')
const http = require('http');
const PORT = process.env.PORT || 8080
const mysql = require('mysql')
const parser = require('body-parser')
var cors = require('cors')

const db = mysql.createConnection({
    host:"localhost",
    user:"makuro",
    password:"Makuro_123",
    database:"malik_data"
  })
  

  db.connect((err)=>{
    if(err) throw err
  })
  process.on('uncaughtException',(err)=>{
    if(err){
      console.log(err)
    }
  })
  
  const app = express();
  app.use(parser.json())
  app.use(parser.urlencoded({extended:true}))
  app.use(cors({credentials: true, origin: true}))
  
  
 app.get("/",(a,b)=>{
    b.send(`[{"status":"ok"}]`)
  })

app.get('*',(a,b)=>{
    b.send("kesalahan url")
  })

  app.listen(PORT,()=>{
    console.log(`app run on port : ${PORT}`)
  })


```