# MERN Stack

This repository serves as a comprehensive guide to building a full-stack application using the MERN stack: MongoDB, Express.js, React, and Node.js. It provides step-by-step instructions to set up the environment, integrate each technology, and deploy a simple application.

## Prerequisites

- Node.js and npm (Node Package Manager)
- MongoDB
- A text editor or IDE (e.g., Visual Studio Code)

## Installation

### 1. Setting Up the Backend

1. **Node.js & Express.js Setup**:
   - Initialize a new Node.js project:
     ```bash
     mkdir backend
     cd backend
     npm init -y
     npm install express mongoose body-parser cors dotenv
     ```

2. **Create a Simple Server**:
   - Create `server.js`:
     ```javascript
     const express = require('express');
     const bodyParser = require('body-parser');
     const cors = require('cors');
     const mongoose = require('mongoose');

     const app = express();
     const PORT = process.env.PORT || 5000;

     app.use(cors());
     app.use(bodyParser.json());

     mongoose.connect('mongodb://localhost/mernstack', {
       useNewUrlParser: true,
       useUnifiedTopology: true
     });

     app.get('/', (req, res) => {
       res.send('Hello World!');
     });

     app.listen(PORT, () => {
       console.log(`Server running on port ${PORT}`);
     });
     ```

### 2. Setting Up the Frontend

1. **React Setup**:
   - Create a new React application:
     ```bash
     npx create-react-app frontend
     cd frontend
     npm start
     ```

2. **Integrate with Backend**:
   - Modify `src/App.js`:
     ```javascript
     import React, { useEffect, useState } from 'react';
     import axios from 'axios';

     function App() {
       const [data, setData] = useState('');

       useEffect(() => {
         axios.get('http://localhost:5000/')
           .then((response) => setData(response.data))
           .catch((error) => console.log(error));
       }, []);

       return (
         <div>
           <header>
             <h1>Received from backend: {data}</h1>
           </header>
         </div>
       );
     }

     export default App;
     ```

## Deployment

- **Heroku**: Steps to deploy both frontend and backend on Heroku.
- **MongoDB Atlas**: Instructions to set up a cloud-based MongoDB database.

## Contributing

We welcome contributions to enhance this guide, improve examples, and extend functionality. Please fork the repository, make your changes, and submit a pull request.

## License

This project is licensed under the MIT License. See the LICENSE file for details.
