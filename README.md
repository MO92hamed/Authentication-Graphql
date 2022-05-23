
# Graphql server-api

this repositorie is an authentication ,comment and post using MongoDB, expressjs ,NodeJs and Graphql


## Dependencies
- express

- express-graphql

- graphql

- mongoose

- dotenv

- jsonwebtoken

## Roadmap

- Install dependencies.

- Create Server.

- Connect to database.

```bash

const connectDB = async () => {
  const connect = await mongoose.connect(process.env.MONGO_URI, {
    useNewUrlParser: true,
    useUnifiedTopology: true,
  })
  console.log(`MongoDB connected`)
}

module.exports = { connectDB }
```

- Create  models
   
   - User

   - Comment

   - Post

   - index

- Create and assign a JWT

```bash

const jwt = require("jsonwebtoken")

const authenticate = async (req, res, next) => {
  const token = req.headers.authorization?.split(" ")[1] || ""

  try {
    const verified = jwt.verify(token, process.env.JWT_SECRET)
    req.verifiedUser = verified.user
    console.log("Verification success!", verified)
    next()
  } catch (err) {
    console.log("Verification failed!", err)
    next()
  }
}

module.exports = { authenticate }

```

- Create a graphql-server with get(/graphql)

```bash

app.get("/", (req, res) => {
  res.json({ msg: "Welcome! Go to /graphql" })
})
```

- Create a  graphql using express

     - mutations 
        - register
        - login
        - Post(add,update,delete)
        - Comment(add, update,delete)
     - queries
        - user
        - users
        - comment
        - comments
        - post
        - posts
     - schema
     
     - types    
    
     -Graphql-server

```bash
app.use(
  "/graphql",
  graphqlHTTP({
    schema,
    graphiql: true,
  })
)

```


     
## Deployment

To deploy this project run

```bash
  npm install
```

```bash
  npm start
```

## Authors

- [@MO92hamed](https://github.com/MO92hamed)


