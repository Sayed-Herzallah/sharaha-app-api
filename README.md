# 🔒 Sharaha - Secure Anonymous Messaging API Backend

<div align="center">
  <img src="https://capsule-render.vercel.app/api?type=waving&color=0:0d1117,100:e91e63&height=180&section=header&text=Sharaha%20Messaging&fontSize=40&fontColor=ffffff&fontFamily=Outfit" width="100%" />
</div>

A production-grade, highly secure, and encrypted anonymous feedback and messaging API backend. Built using Node.js, Express 5.x, and MongoDB, this application prioritizes absolute data privacy and integrity. It leverages advanced cryptographic algorithms to ensure that messages are encrypted end-to-end, making them unreadable by anyone—including database administrators.

---

## 🚀 Key Features

* **🛡️ End-to-End Cryptography**: Advanced database-level message encryption using `Crypto-JS` (AES-256). All incoming anonymous feedback is encrypted before writing to MongoDB and decrypted only when requested by the authenticated owner.
* **🔑 Secure Identity Protocol**: State-of-the-art password hashing using `Bcrypt` and stateless user authorization using industry-standard `JSON Web Tokens (JWT)`.
* **📧 Verification Mailer**: Automatic email dispatch powered by `Nodemailer` for user activation, email confirmation, and secure password reset tokens.
* **⚡ Strict Schema Validation**: Bulletproof input sanitization using `Joi` validation schemas at the routing gate to intercept malicious payloads.
* **📂 Modular Architecture**: Structured MVC architecture separating business logic into clean folders (`Auth`, `User`, and `Messages`).

---

## 🧬 Architecture & Cryptographic Flow

Here is how anonymous messages are sent, encrypted at rest, and securely retrieved by the target user:

```mermaid
graph TD
    Sender[Anonymous Sender] -->|Post Message to User Link| Router[Express Routing Gate]
    Router -->|Input Validation| JoiMW[Joi Middleware Validator]
    JoiMW -->|Valid Text| CryptoService[CryptoJS Encryptor]
    CryptoService -->|AES-256 Encrypted Ciphertext| DB[(MongoDB database)]
    
    Receiver[Authenticated Receiver] -->|Request My Inbox + JWT| AuthMW[Auth JWT Verification Middleware]
    AuthMW -->|Valid User| DBQuery[Query Encrypted Messages]
    DB -->|Encrypted Ciphertext| DBQuery
    DBQuery -->|Decrypt Ciphertext| DecryptService[CryptoJS Decryptor]
    DecryptService -->|Plaintext Messages| ExpressResponse[JSON Response Package]
    ExpressResponse -->|Render Inbox| Receiver
```

---

## 🛠️ Technology Stack & Badges

### Core Frameworks
[![Node.js](https://img.shields.io/badge/Node.js-v20.x-green?logo=nodedotjs&style=flat-square)](https://nodejs.org/)
[![Express.js](https://img.shields.io/badge/Express.js-v5.x_Beta-lightgrey?logo=express&style=flat-square)](https://expressjs.com/)
[![MongoDB](https://img.shields.io/badge/MongoDB-v7.x-green?logo=mongodb&style=flat-square)](https://www.mongodb.com/)
[![Mongoose](https://img.shields.io/badge/Mongoose-v9.x-red?logo=mongoose&style=flat-square)](https://mongoosejs.com/)

### Security & Mail
[![CryptoJS](https://img.shields.io/badge/Crypto_JS-AES_Encryption-orange?style=flat-square)](https://cryptojs.gitbook.io/)
[![Bcrypt](https://img.shields.io/badge/Bcrypt-Password_Hashing-gold?style=flat-square)](https://www.npmjs.com/package/bcrypt)
[![JWT](https://img.shields.io/badge/JWT-Authentication-blue?logo=jsonwebtokens&style=flat-square)](https://jwt.io/)
[![Nodemailer](https://img.shields.io/badge/Nodemailer-SMTP_Mailer-lightblue?style=flat-square)](https://nodemailer.com/)

---

## 📂 Folder Structure

```text
Sharaha Application/
├── index.js               # Web Server Entrypoint & HTTP Bootstrap
├── app.controller.js      # Global Middlewares (CORS, body parser), Database Connections
├── jsconfig.json          # Path mapping & JS IntelliSense configuration
├── src/
│   ├── DataBase/          # Connection handler & mongoose models
│   │   ├── connection.js
│   │   └── Models/
│   │       ├── Message.model.js
│   │       └── User.model.js
│   ├── middelware/        # Request handling and security filters
│   │   ├── auth.middleware.js
│   │   └── validation.middleware.js
│   ├── utils/             # Helper utilities & cryptographic wrappers
│   │   ├── sendEmail.js
│   │   └── crypto.js
│   └── Modules/           # Main business feature groups
│       ├── Auth/          # Signup, activation links, token signing, reset passwords
│       ├── Messages/      # Anonymous message dispatch, fetch inbox, delete entries
│       └── User/          # Profile retrieval, visibility toggles, account termination
```

---

## 🚀 Getting Started

### Prerequisites
- Node.js (v20.x or above)
- MongoDB running locally or a MongoDB Atlas URI
- SMTP configuration details (e.g., Gmail App Password or Mailtrap)

### Installation
1. Clone the codebase:
   ```bash
   git clone https://github.com/Sayed-Herzallah/Sharaha-Application.git
   cd Sharaha-Application
   ```
2. Install dependencies:
   ```bash
   npm install
   ```
3. Configure the environment variables in a `.env` file in the root folder:
   ```env
   PORT=3000
   MONGO_URI=mongodb://127.0.0.1:27017/sharaha
   JWT_SECRET=your_jwt_signature_key
   CRYPTO_SECRET=your_aes_encryption_key
   
   SMTP_HOST=smtp.gmail.com
   SMTP_PORT=465
   SMTP_SECURE=true
   SMTP_USER=your_email@gmail.com
   SMTP_PASS=your_gmail_app_password
   ```
4. Run locally:
   ```bash
   npm start
   ```

---

## 📜 Verified Certificates & Achievements
To review verified technical accomplishments, backend training, and professional project portfolios, click below:

[![Portfolio Achievements](https://img.shields.io/badge/Verified_Certifications-Click_to_View-gold?style=for-the-badge&logo=credentials)](https://herzallah.me#certifications)

---

## 👨‍💻 Developed By
**Sayed Herzallah**  
*Backend-Focused Full-Stack Developer*  
- [LinkedIn Profile](https://www.linkedin.com/in/sayed-herzallah)  
- [Portfolio Website](https://herzallah.me)  
- [GitHub Profile](https://github.com/Sayed-Herzallah)  
