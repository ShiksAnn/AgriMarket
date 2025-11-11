# 🌾 AgriMarket – Smart Agricultural Marketplace (SDG 2: Zero Hunger)

**AgriMarket** is a full-stack **MERN** application that bridges the gap between **farmers** and **buyers**, enabling direct trade of agricultural produce.  
By eliminating middlemen, AgriMarket empowers farmers to earn fair prices and helps buyers access fresh, affordable food — contributing to the **United Nations Sustainable Development Goal (SDG) 2: Zero Hunger.**

---

## 🌍 Project Overview

Farmers often struggle to find fair and reliable markets for their produce.  
**AgriMarket** solves this by creating a **digital marketplace** that connects **farmers, consumers, and wholesalers** directly — promoting sustainable agriculture, food accessibility, and income equity.

---

## 🎯 Objectives

- Empower farmers with **market access** and **transparent pricing**.  
- Enable buyers to **find, order, and pay** for fresh produce online.  
- Facilitate **real-time communication** between farmers and buyers.  
- Provide **data insights** on agricultural trade and food distribution.  

---

## 🧩 Key Features

### 👨‍🌾 Farmer Portal
- Register, log in, and verify profile.  
- Upload produce listings with images, prices, and quantity.  
- Manage inventory and mark products as available or sold.  
- Dashboard showing sales, top crops, and earnings analytics.

### 🛒 Buyer Portal
- Browse produce by type, price, or location.  
- Add products to cart, place orders, and make payments.  
- Track order status (ordered → shipped → delivered).  
- Rate and review farmers after transactions.

### 💬 Real-Time Chat (Socket.io)
- Buyers and farmers can chat instantly.  
- Notifications for new messages and order updates.

### 🗺️ Location & Maps
- Farmers can **pin farm locations** on **Google Maps**.  
- Buyers can discover **nearby farms** and pickup points.

### 📦 Order & Payment System
- Secure payment integration (IntaSend / Stripe).  
- Automated email or SMS order confirmations.  
- Admin-managed order verification.

### 📊 Analytics Dashboard
- Farmers: revenue tracking, order trends, crop performance.  
- Admins: platform usage, active users, and trade volumes.

### 🧭 Admin Panel
- Approve or verify farmers.  
- Manage users, products, and transactions.  
- Export reports in CSV or PDF.

---

## ⚙️ Tech Stack

| Layer | Technology | Description |
|-------|-------------|-------------|
| Frontend | React (Vite) + TailwindCSS | Modern responsive UI |
| Backend | Node.js + Express.js | RESTful API and server logic |
| Database | MongoDB + Mongoose | NoSQL data storage |
| Real-time | Socket.io | Chat and notifications |
| Auth | JWT + bcrypt | Secure authentication |
| File Upload | Cloudinary | Image hosting |
| Payment | IntaSend / Stripe | Online transactions |
| Maps | Google Maps API | Farm and location mapping |
| Charts | Recharts | Data visualization |
| Deployment | Vercel / Render / MongoDB Atlas | Cloud hosting |

---

AgriMarket/
├── client/ # Frontend (React + Vite)
│ ├── src/
│ │ ├── components/
│ │ │ ├── Navbar.jsx
│ │ │ ├── ProductCard.jsx
│ │ │ ├── FarmerForm.jsx
│ │ │ ├── ChatBox.jsx
│ │ │ ├── DashboardCharts.jsx
│ │ │ └── Footer.jsx
│ │ ├── pages/
│ │ │ ├── Home.jsx
│ │ │ ├── Products.jsx
│ │ │ ├── FarmerDashboard.jsx
│ │ │ ├── BuyerDashboard.jsx
│ │ │ ├── Chat.jsx
│ │ │ └── AdminPanel.jsx
│ │ ├── context/
│ │ │ └── AuthContext.jsx
│ │ ├── services/
│ │ │ └── api.js
│ │ ├── App.jsx
│ │ └── main.jsx
│ └── package.json
│
├── server/ # Backend (Node + Express)
│ ├── config/
│ │ └── db.js
│ ├── models/
│ │ ├── User.js
│ │ ├── Product.js
│ │ ├── Order.js
│ │ └── Chat.js
│ ├── routes/
│ │ ├── userRoutes.js
│ │ ├── productRoutes.js
│ │ ├── orderRoutes.js
│ │ └── chatRoutes.js
│ ├── controllers/
│ │ ├── userController.js
│ │ ├── productController.js
│ │ ├── orderController.js
│ │ └── chatController.js
│ ├── middleware/
│ │ └── authMiddleware.js
│ ├── server.js
│ └── package.json
│
└── README.md


---

## 🗄️ Database Models (MongoDB)

### 👤 User Model
```js
{
  name: String,
  email: String,
  password: String,
  role: { type: String, enum: ["farmer", "buyer", "admin"], default: "buyer" },
  phone: String,
  location: {
    type: { type: String, default: "Point" },
    coordinates: [Number]
  },
  createdAt: { type: Date, default: Date.now }
}

🌾 Product Model
{
  farmerId: { type: ObjectId, ref: "User" },
  productName: String,
  category: String,
  description: String,
  pricePerKg: Number,
  quantityAvailable: Number,
  imageUrl: String,
  status: { type: String, enum: ["available", "sold"], default: "available" },
  createdAt: { type: Date, default: Date.now }
}

🧾 Order Model
{
  buyerId: { type: ObjectId, ref: "User" },
  farmerId: { type: ObjectId, ref: "User" },
  productId: { type: ObjectId, ref: "Product" },
  quantity: Number,
  totalPrice: Number,
  paymentStatus: { type: String, enum: ["pending", "paid"], default: "pending" },
  orderStatus: { type: String, enum: ["ordered", "shipped", "delivered"], default: "ordered" },
  createdAt: { type: Date, default: Date.now }
}

💬 Chat Model
{
  senderId: { type: ObjectId, ref: "User" },
  receiverId: { type: ObjectId, ref: "User" },
  message: String,
  timestamp: { type: Date, default: Date.now }
}

🚀 Installation & Setup
1️⃣ Clone Repository
git clone https://github.com/yourusername/AgriMarket.git
cd AgriMarket

2️⃣ Setup Backend
cd server
npm install


Create .env in the server folder:

PORT=5000
MONGO_URI=your_mongodb_uri
JWT_SECRET=your_jwt_secret
CLOUDINARY_URL=your_cloudinary_url
INTASEND_API_KEY=your_payment_key
GOOGLE_MAPS_API_KEY=your_maps_key


Run server:

npm run dev

3️⃣ Setup Frontend
cd ../client
npm install
npm run dev


Access the app at:
👉 http://localhost:5173

🌐 Deployment
Service	Purpose	Example
Frontend	Vercel / Netlify	Host React app
Backend	Render / Railway	Deploy Node.js API
Database	MongoDB Atlas	Cloud database
Media	Cloudinary	Image uploads
Domain	Freenom / Namecheap	Custom domain
📈 Future Enhancements

🌦️ Weather integration using OpenWeather API.

🤖 AI crop price prediction model (TensorFlow.js).

🛰️ IoT sensor data integration (soil & temperature).

📱 Mobile PWA for offline access in rural areas.

📩 SMS alerts for low-connectivity users.

👩‍💻 Author

Your Name
Full-Stack Developer | SDG Innovator 🌍
📧 your.email@example.com

🔗 LinkedIn
 | GitHub

🌱 Impact

“AgriMarket empowers farmers, connects communities, and nourishes nations —
one digital harvest at a time.” 🌾


## 🗂️ Project Structure

