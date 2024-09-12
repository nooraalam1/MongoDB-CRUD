# MongoDB-CRUD
POST Method:
Client Site:

    fetch('http://localhost:3000/users',
      {
        method: 'POST',
        headers: { 'Content-Type': 'application/json' },
        body: JSON.stringify(Info)
      })
      .then(res => res.json())
      .then(data => {
        console.log(data)
      })

Server Site:

    async function run() {
      try {
      await client.connect();
    const database = client.db("insertDB");
    const haiku = database.collection("haiku");
    app.post('/users',async(req,res)=>{
              const user = req.body
          const result = await haiku.insertOne(user);
          res.send(result)
    })

