# DeCo Backend - Step-by-Step Setup Guide

## Introduction
This documentation provides a step-by-step guide to setting up the **DeCo Backend** using **Node.js (Express)** and deploying it for **free** on **Vercel**. Follow these steps to configure, install dependencies, and run the backend server online.

---

## **🛠️ Step 1: Install Prerequisites**
Before proceeding, ensure you have the following installed:
- ✅ **Node.js** (for Express backend) → [Download](https://nodejs.org/)
- ✅ **Vercel CLI** (for deployment) → [Install](https://vercel.com/docs/cli)
- ✅ **MongoDB Atlas (Free Tier)** (for database) → [Sign Up](https://www.mongodb.com/cloud/atlas)

---

## **📝 Step 2: Clone the Backend Repository**
Run the following command to clone the backend repository:
```bash
git clone https://github.com/deco-org/backend.git
cd backend
```

---

## **📦 Step 3: Install Dependencies**
Run:
```bash
npm install
```

---

## **🔑 Step 4: Set Up Environment Variables**
Create a `.env` file inside the backend folder and configure the required variables:
```
PORT=5000
DATABASE_URL=mongodb+srv://your_mongo_connection_string
JWT_SECRET=your-secret-key
```
Use **MongoDB Atlas Free Tier** for a cloud database.

---

## **🚀 Step 5: Deploy to Vercel (Free Hosting)**

1️⃣ **Install Vercel CLI**  
```bash
npm install -g vercel
```

2️⃣ **Login to Vercel**  
```bash
vercel login
```

3️⃣ **Deploy Backend**  
```bash
vercel --prod
```

4️⃣ **Get Deployed URL**  
After deployment, Vercel will provide a **free HTTPS URL** (e.g., `https://deco-backend.vercel.app`).

---

## **🔗 Step 6: Test API Endpoints**
Use **Postman** or `curl` to check if the server is running:
```bash
curl https://deco-backend.vercel.app/api/health
```

---

## **💬 Step 7: Enable WebSockets (Optional)**
Modify the backend code to support WebSockets for real-time communication.

### **Node.js (Express + Socket.io) Example**
Install `socket.io`:
```bash
npm install socket.io
```
Modify `server.js`:
```javascript
const io = require("socket.io")(server, { cors: { origin: "*" } });

io.on("connection", (socket) => {
    console.log("A user connected");
    socket.on("message", (msg) => {
        io.emit("message", msg);
    });
});
```

---

## **✅ Step 8: Code Execution Engine Deployment (Optional)**
The **Code Execution Engine** requires **Docker** and should be deployed separately (Vercel does not support it). Use **Fly.io (Free Tier)**:
```bash
fly launch
fly deploy
```
For a local test, run:
```bash
docker build -t deco-execution .
docker run -p 5000:5000 deco-execution
```

---

## 🎉 Conclusion
Now your **DeCo Backend** is deployed and running on **Vercel for free!** 🚀 Let us know if you need any help setting it up. Happy coding! 👨‍💻👩‍💻

