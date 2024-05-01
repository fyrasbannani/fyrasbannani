// app.js file
const express = require('express');
const bodyParser = require('body-parser');
const cors = require('cors');
const http = require('http');

const app = express();

app.use(bodyParser.json());
app.use(cors());

const userRoutes = require('./routes/users');
const medicalRoutes = require('./routes/medicals');
const commandRoutes = require('./routes/command');

app.use('/api/user', userRoutes);
app.use('/api/medical', medicalRoutes);
app.use('/api/command', commandRoutes);

const server = http.createServer(app);

const PORT = process.env.PORT || 8800;

server.listen(PORT, () => {
    console.log(`Server is running on port ${PORT}`);
});

module.exports = { app, server };



//command.js <routes folder>
const express = require('express');
const router = express.Router();

router.get('/getCommandById/:id',(req,res)=>{});
module.exports = router;


//medicals.js <routes folder>
const express = require('express');
const router = express.Router();

router.get('/getMedicalById/:id',(req,res)=>{});
module.exports = router;


//users.js <routes folder>
const express = require('express');
const router = express.Router();

router.get('/getUserById/:id',(req,res)=>{});

module.exports = router;


//command.js <models folder>
const mongoose = require("mongoose");
const commandSchema = new mongoose.Schema({
    referance: String ,
    date: { type: Date, default: Date.now },
    cardNumber : String ,
    cardHolder : String ,
    expDate : Date,
    CVV : int, 
});

const user = mongoose.model("user", commandSchema);
module.exports = user;

//medicals.js <models folder>
const mongoose = require("mongoose");
const medicalSchema = new mongoose.Schema({
    name: String,
    price: double,
});

const medical = mongoose.model("medical", medicalSchema);
module.exports = medical;


//users.js <models folder>
const mongoose = require("mongoose");
const userSchema = new mongoose.Schema({
    username: String,
    email: String,
    password: String,
});

const user = mongoose.model("user", userSchema);
module.exports = user;



