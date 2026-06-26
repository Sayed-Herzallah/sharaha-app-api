# Sharaha Anonymous Messaging API: Secure Backend & Privacy-Focused Gateway

<div align="center">
  <img src="https://capsule-render.vercel.app/api?type=waving&color=0:0d1117,100:7c3aed&height=160&section=header&text=Sharaha%20Messaging%20API&fontSize=42&fontColor=ffffff&fontFamily=Outfit" width="100%" />
</div>

<div align="center">
  ![Node.js](https://img.shields.io/badge/Node.js-v18-green?logo=nodedotjs&style=for-the-badge) ![Express.js](https://img.shields.io/badge/Express.js-v4-black?logo=express&style=for-the-badge) ![MongoDB](https://img.shields.io/badge/MongoDB-v6-green?logo=mongodb&style=for-the-badge) ![License](https://img.shields.io/badge/License-MIT-green?style=for-the-badge)
</div>

خادم **منصة صراحة للمصارحة** هو خادم برمجيات خلفي مبني باستخدام Express وقاعدة بيانات MongoDB لمعالجة الرسائل المجهولة وإدارتها بشكل يحمي خصوصية البيانات ويمنع تسرب هويات المرسلين.

This repository houses the secure backend RESTful API, authentication handlers, and messaging database tables for the **Sharaha Anonymous Feedback App**.

---

## 🧬 Anonymous Message Flow

The system processes incoming anonymous statements and logs them securely:

```mermaid
graph TD
    Visitor[Anonymous User] -->|Write message & submit| API[REST Routing Endpoint]
    API -->|Strip IP and Sender metadata| Filter[Sanitization Filter]
    Filter -->|Check user link validity| DBQuery[Mongoose DB Check]
    DBQuery -->|Valid| Save[Save Message to MongoDB]
    Save -->|Success| Res[Return JSON message_id]
```

---

## 🧬 Core Services & Layouts

1.  **Anonymizer Filter (`src/controllers/messages.js`)**: Sanitizes incoming message bodies while avoiding tracking sender metadata.
2.  **User Authentication (`src/controllers/auth.js`)**: JWT access tokens and bcrypt hashing protect recipient inbox access.

---

## 🛠️ Technology Stack & Assets

*   **Runtime Backend**: Node.js & Express.js.
*   **Database Engine**: MongoDB NoSQL database using Mongoose ODM.
*   **Security Framework**: JWT token authentication and CORS access restrictions.

---

## 📂 Repository Module Layout

```text
sharaha-app-api/
├── src/
│   ├── controllers/     # Message handling and auth execution logic
│   ├── models/          # MongoDB Schemas (Users, Messages)
│   ├── routes/          # RESTful endpoint paths
│   └── app.js           # Server application startup configurations
├── package.json         # Node metadata
└── README.md            # System documentation
```

---

## ⚡ Local Setup & Run
```bash
git clone https://github.com/Sayed-Herzallah/sharaha-app-api.git
cd sharaha-app-api
npm install
# Configure MONGO_URI inside config/.env
npm start
```

---

## 📄 License
Licensed under the **MIT License**.
