# Todo App Backend API

Backend REST API for the MERN Stack Todo Application built with Node.js, Express, and MongoDB.

## Features

- ✅ RESTful API endpoints
- ✅ MongoDB database integration
- ✅ CORS enabled for frontend communication
- ✅ Error handling and validation
- ✅ Environment variable configuration

## Tech Stack

- **Node.js** - JavaScript runtime
- **Express** - Web framework
- **MongoDB** - NoSQL database
- **Mongoose** - MongoDB ODM

## Prerequisites

Before running this project, make sure you have:

- Node.js (v14 or higher)
- MongoDB (local installation or MongoDB Atlas account)
- npm or yarn package manager

## Installation

1. **Clone the repository**
```bash
   git clone <your-repo-url>
   cd backend
```

2. **Install dependencies**
```bash
   npm install
```

3. **Create environment file**
   
   Create a `.env` file in the root directory:
```env
   MONGODB_URI=mongodb://localhost:27017/todoapp
   PORT=5000
   NODE_ENV=development
   FRONTEND_URL=http://localhost:3000
```

4. **Start MongoDB**
   
   If using local MongoDB:
```bash
   # On macOS (with Homebrew)
   brew services start mongodb-community
   
   # On Windows
   # Start MongoDB service from Services panel
   
   # On Linux
   sudo systemctl start mongod
```

5. **Run the server**
   
   Development mode (with auto-reload):
```bash
   npm run dev
```
   
   Production mode:
```bash
   npm start
```

6. **Test the API**
   
   Open browser or Postman and visit:
```
   http://localhost:5000/
```
   
   You should see:
```json
   {
     "message": "Todo API is running",
     "status": "OK",
     "timestamp": "2024-..."
   }
```

## API Endpoints

### Base URL
```
http://localhost:5000/api
```

### Endpoints

| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/todos` | Get all todos |
| GET | `/todos/:id` | Get single todo by ID |
| POST | `/todos` | Create new todo |
| PUT | `/todos/:id` | Update todo by ID |
| DELETE | `/todos/:id` | Delete todo by ID |

### Request/Response Examples

#### Create Todo (POST `/api/todos`)

**Request Body:**
```json
{
  "title": "Buy groceries",
  "description": "Milk, eggs, bread",
  "priority": "high",
  "dueDate": "2024-12-30"
}
```

**Response:**
```json
{
  "_id": "676f1234567890abcdef",
  "title": "Buy groceries",
  "description": "Milk, eggs, bread",
  "priority": "high",
  "dueDate": "2024-12-30T00:00:00.000Z",
  "completed": false,
  "createdAt": "2024-12-28T10:30:00.000Z"
}
```

#### Get All Todos (GET `/api/todos`)

**Response:**
```json
[
  {
    "_id": "676f1234567890abcdef",
    "title": "Buy groceries",
    "description": "Milk, eggs, bread",
    "priority": "high",
    "dueDate": "2024-12-30T00:00:00.000Z",
    "completed": false,
    "createdAt": "2024-12-28T10:30:00.000Z"
  }
]
```

#### Update Todo (PUT `/api/todos/:id`)

**Request Body:**
```json
{
  "completed": true
}
```

#### Delete Todo (DELETE `/api/todos/:id`)

**Response:**
```json
{
  "message": "Todo deleted successfully"
}
```

## Project Structure
```
backend/
├── controllers/
│   └── todoController.js    # Business logic for todos
├── models/
│   └── Todo.js              # Todo schema/model
├── routes/
│   └── todos.js             # API routes
├── .env                     # Environment variables (not in git)
├── .gitignore              # Git ignore rules
├── package.json            # Dependencies and scripts
├── server.js               # Main application file
└── README.md               # This file
```

## Environment Variables

| Variable | Description | Example |
|----------|-------------|---------|
| `MONGODB_URI` | MongoDB connection string | `mongodb://localhost:27017/todoapp` |
| `PORT` | Server port | `5000` |
| `NODE_ENV` | Environment mode | `development` or `production` |
| `FRONTEND_URL` | Frontend URL for CORS | `http://localhost:3000` |

## Deployment

### Deploy to Render

1. Push code to GitHub
2. Create new Web Service on [Render](https://render.com)
3. Connect your repository
4. Configure:
   - **Build Command:** `npm install`
   - **Start Command:** `node server.js`
5. Add environment variables in Render dashboard
6. Deploy!

### Deploy to Railway

1. Push code to GitHub
2. Create new project on [Railway](https://railway.app)
3. Connect repository
4. Add environment variables
5. Deploy!

### MongoDB Atlas Setup

1. Create account at [MongoDB Atlas](https://www.mongodb.com/cloud/atlas)
2. Create a free cluster
3. Add database user
4. Whitelist IP (use `0.0.0.0/0` for development)
5. Get connection string and update `MONGODB_URI`

## Troubleshooting

### MongoDB Connection Error
```
Error: connect ECONNREFUSED 127.0.0.1:27017
```
**Solution:** Make sure MongoDB is running locally or check your MongoDB Atlas connection string.

### CORS Error
```
Access to fetch has been blocked by CORS policy
```
**Solution:** Check that `FRONTEND_URL` in `.env` matches your frontend URL.

### Port Already in Use
```
Error: listen EADDRINUSE: address already in use :::5000
```
**Solution:** Change `PORT` in `.env` or kill the process using port 5000:
```bash
# Find process
lsof -i :5000

# Kill process
kill -9 <PID>
```

## Scripts

- `npm start` - Start production server
- `npm run dev` - Start development server with nodemon

## Contributing

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add some amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## License

This project is licensed under the ISC License.

## Author

Your Name

## Acknowledgments

- Express.js documentation
- MongoDB documentation
- Mongoose documentation