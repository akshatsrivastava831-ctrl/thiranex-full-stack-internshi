# Personal Portfolio Website (Full-Stack)

A full-stack portfolio website — frontend (HTML/CSS/JS), backend
(Node.js + Express), and database (MongoDB).

## Folder Structure
```
portfolio-project/
├── frontend/       → index.html, style.css, script.js
└── backend/        → server.js, routes/, models/
```

## 1. Backend Setup (Node.js + Express + MongoDB)

1. Open a terminal in the `backend` folder.
2. Install dependencies:
   ```
   npm install
   ```
3. Get a free MongoDB connection string:
   - Go to https://www.mongodb.com/cloud/atlas → create a free cluster
   - Copy your connection string
4. Rename `.env.example` to `.env` and paste your MongoDB URI:
   ```
   MONGO_URI=mongodb+srv://<username>:<password>@cluster0.mongodb.net/portfolio
   PORT=5000
   ```
5. Start the server:
   ```
   npm start
   ```
   You should see: `MongoDB connected` and `Server running on port 5000`

### API Endpoints
| Method | Endpoint          | Description             |
|--------|-------------------|--------------------------|
| GET    | /api/projects     | Get all projects         |
| POST   | /api/projects     | Add a new project        |
| DELETE | /api/projects/:id | Delete a project         |
| POST   | /api/contact      | Submit contact form      |
| GET    | /api/contact      | View all messages (admin)|

### Add a sample project (using curl or Postman)
```
curl -X POST http://localhost:5000/api/projects \
  -H "Content-Type: application/json" \
  -d '{"title":"To-Do App","description":"A simple to-do list app","link":"https://github.com/you/todo-app"}'
```

## 2. Frontend Setup

Just open `frontend/index.html` in a browser (or use the VS Code "Live Server"
extension). Make sure the backend is running first, since the page fetches
project data from `http://localhost:5000/api/projects`.

Edit your name, about section, etc. directly inside `index.html`.

## 3. Deployment

**Backend** (choose one, all have free tiers):
- Render: https://render.com — connect your GitHub repo, set the `MONGO_URI` env variable, deploy.
- Railway: https://railway.app
- Heroku: https://www.heroku.com

**Frontend**:
- Netlify: https://netlify.com — drag & drop the `frontend` folder
- Vercel: https://vercel.com

After deploying the backend, update `API_BASE` in `frontend/script.js` to your
live backend URL, e.g.:
```js
const API_BASE = "https://your-backend-name.onrender.com/api";
```

## 4. Next Steps / Customization Ideas
- Add an admin panel to add/delete projects without using curl/Postman
- Add authentication (JWT) if you want a private admin dashboard
- Add project images (store on Cloudinary and save the URL in MongoDB)
- Style the site further using the `frontend/style.css` file
