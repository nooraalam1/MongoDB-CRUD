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
------------------------------------------------------------------------
GET Method:

     const database = client.db("insertDB");
    const haiku = database.collection("haiku");
    app.post('/users',async(req,res)=>{
              const user = req.body
          const result = await haiku.insertOne(user);
          res.send(result)
    })

--------------------------------------------------------------------
DELETE Method:
Server:

     app.delete('/Allusers/:id',async(req,res)=>{
      const a= req.params.id;
      const query = { _id: new ObjectId (a) };
    const result = await haiku.deleteOne(query);
    res.send(result)
    })

Client:

     const handleDelete = (_id) => {
        console.log("Clicked", _id)
        fetch(`http://localhost:3000/Allusers/${_id}`,
            { method: 'DELETE' }
        )
            .then(res => res.json())
            .then(data => console.log(_id))
    }
-------------------------------------------------------------------------
