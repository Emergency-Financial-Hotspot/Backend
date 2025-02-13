# DeCo Backend - Step-by-Step Setup Guide

## Introduction
This documentation provides a step-by-step guide to setting up the **DeCo Backend** using **Node.js (Express) or FastAPI** with WebSockets. Follow these steps to configure, install dependencies, and run the backend server locally.

---

## **🛠️ Step 1: Install Prerequisites**
Before proceeding, ensure you have the following installed:
- ✅ **Node.js** (for Express backend) → [Download](https://nodejs.org/)
- ✅ **Python 3.8+** (for FastAPI backend) → [Download](https://www.python.org/downloads/)
- ✅ **Docker** (optional, for containerization) → [Download](https://www.docker.com/)

---

## **📝 Step 2: Clone the Backend Repository**
Run the following command to clone the backend repository:
```bash
git clone https://github.com/deco-org/backend.git
cd backend
```

---

## **📦 Step 3: Install Dependencies**

### For **Node.js (Express) Backend**
Run:
```bash
npm install
```

### For **FastAPI Backend**
Create a virtual environment and install dependencies:
```bash
python -m venv venv
source venv/bin/activate  # (Mac/Linux)
venv\Scripts\activate  # (Windows)

pip install -r requirements.txt
```

---

## **🔑 Step 4: Set Up Environment Variables**
Create a `.env` file inside the backend folder and configure the required variables:
```
PORT=5000
DATABASE_URL=mongodb://localhost:27017/deco
JWT_SECRET=your-secret-key
```
For FastAPI, create a `.env` file and update settings accordingly.

---

## **🚀 Step 5: Start the Backend Server**

### **For Node.js (Express) Backend**
```bash
npm start
```
Or, for development mode (with hot reload):
```bash
npm run dev
```

### **For FastAPI Backend**
```bash
uvicorn main:app --host 0.0.0.0 --port 8000 --reload
```

---

## **🔗 Step 6: Test API Endpoints**
Use **Postman** or `curl` to check if the server is running:
```bash
curl http://localhost:5000/api/health
```
For FastAPI:
```bash
curl http://localhost:8000/docs
```
FastAPI provides an interactive API at `http://localhost:8000/docs` 🎯

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

### **FastAPI WebSockets Example**
Install `fastapi-sockets`:
```bash
pip install websockets
```
Modify `main.py`:
```python
from fastapi import FastAPI, WebSocket

app = FastAPI()

@app.websocket("/ws")
async def websocket_endpoint(websocket: WebSocket):
    await websocket.accept()
    while True:
        data = await websocket.receive_text()
        await websocket.send_text(f"Message received: {data}")
```

---

## **✅ Step 8: Deploy (Optional)**
Deploy using **Docker**:
```bash
docker build -t deco-backend .
docker run -p 5000:5000 deco-backend
```
Or use **Heroku, Vercel, or AWS** for hosting.

---

## 🎉 Conclusion
Now your **DeCo Backend** is up and running! 🚀 Let us know if you need any help setting it up. Happy coding! 👨‍💻👩‍💻

