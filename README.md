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
    app.get('/users',async(req,res)=>{
        const cursor = haiku.find();
        const result = await cursor.toArray();
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

Update:
Server:

      app.get('/users/:id',async(req,res)=>{
      const id = req.params.id;
      const query = { _id: new ObjectId (id) };
      const result = await haiku.findOne(query)
      res.send(result)

    })

Client:

    <Link to={`/update/${a._id}`}><button>Update</button></Link>

    {
    path: '/update/:id',
    element: <Update></Update>,
    loader: ({ params }) => fetch(`http://localhost:3000/users/${params.id}`)
    }

    

  
