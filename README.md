# 🍽️ Cafe Management API

A robust, real-time backend orchestration engine for modern hospitality operations. Designed to streamline order management, team coordination, and kitchen workflows with enterprise-grade reliability.

![Node.js](https://img.shields.io/badge/Node.js-339933?style=flat&logo=nodedotjs&logoColor=white)
![Express](https://img.shields.io/badge/Express-000000?style=flat&logo=express&logoColor=white)
![MongoDB](https://img.shields.io/badge/MongoDB-47A248?style=flat&logo=mongodb&logoColor=white)
![Pusher](https://img.shields.io/badge/Pusher-251E4E?style=flat&logo=pusher&logoColor=white)
![Socket.io](https://img.shields.io/badge/Socket.io-010101?style=flat&logo=socketdotio&logoColor=white)

---

## 🚀 System Overview

The **Cafe Management API** serves as the central intelligence for dining establishments. It handles the critical path of an order from creation (waiter app) to preparation (kitchen display) and final delivery. 

### 🌟 Core Capabilities
- **Real-Time Orchestration**: Instant order synchronization between waitstaff and kitchen via Pusher and WebSockets.
- **Dynamic CRM**: Specialized management for users, roles (Admin/Waiter/Chef), and customer interactions.
- **Durable Order Lifecycle**: Robust handling of order states (`pending`, `ready`, `delivered`) backed by MongoDB.
- **Scalable Architecture**: Event-driven design capable of handling peak restaurant hours with high throughput.

---

## 🛠 Tech Stack

- **Runtime**: Node.js
- **Server Framework**: Express.js
- **Database**: MongoDB (via Mongoose)
- **Real-Time Engine**: Pusher Channels & Socket.io for fallback
- **Tooling**: Dotenv (Config), Nodemon (DX), CORS (Security)

---

## 📂 Architecture

```bash
/
├── models/         # Data persistence schemas (Mongoose)
│   ├── OrderModul.js  # Order lifecycle & line-item logic
│   └── UserModel.js   # Staff & Role definitions
├── routers/        # API route handlers
│   ├── OrderRoute.js  # Order processing & real-time triggers
│   └── UserRouter.js  # Staff management & authentication
├── Pusher.js       # Real-time event bus configuration
└── index.js        # Entry point & systems integration
```

---

## 🌐 API Reference

### Order Management
| Method | Endpoint | Description | Real-time? |
| :--- | :--- | :--- | :--- |
| `POST` | `/order/create` | Submit a new order to the kitchen | ✅ Yes |
| `PUT` | `/order/made/:id` | Mark an order as prepared/ready | ✅ Yes |
| `GET` | `/order/get` | Retrieve the active order queue | - |
| `DELETE` | `/order/delete/:id` | Cancel/Remove an order record | ✅ No |

### Staff/User Management
| Method | Endpoint | Description |
| :--- | :--- | :--- |
| `GET` | `/user/get` | List all registered staff members |
| `POST` | `/user/create` | Register new staff (Admin/Waiter/Chef) |
| `PUT` | `/user/update/:id` | Modify staff profiles or permissions |
| `DELETE` | `/user/delete/:id` | Remove staff access |

---

## ⚙️ Setup & Deployment

### Environment Variables
Create a `.env` file in the root:
```env
PORT=5001
MONGO_URL=your_mongodb_connection_string
PUSHER_APP_ID=your_id
PUSHER_KEY=your_key
PUSHER_SECRET=your_secret
PUSHER_CLUSTER=your_cluster
```

### Installation
```bash
npm install
npm start
```

---

## 🤝 Contribution

This project is part of a high-performance hospitality suite. Contributions that improve concurrency handling or reporting metrics are particularly welcome.

1. Fork the Project
2. Create your Feature Branch (`git checkout -b feature/Optimization`)
3. Commit your Changes (`git commit -m 'Add Performance Tuning'`)
4. Push to the Branch
5. Open a Pull Request

---

## 📄 License

Distributed under the MIT License.

Developed by [Kodirov Dev](https://github.com/kodirov8788)
