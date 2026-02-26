# 🏨 ระบบจองห้องพักออนไลน์ — Hotel Booking System

> **ใบงานปฏิบัติการ** วิชาการออกแบบและพัฒนาซอฟต์แวร์ (Software Design and Development)

[![Node.js](https://img.shields.io/badge/Node.js-22.x-339933?logo=node.js&logoColor=white)](https://nodejs.org)
[![React](https://img.shields.io/badge/React-18-61DAFB?logo=react&logoColor=white)](https://react.dev)
[![Express](https://img.shields.io/badge/Express-4.x-000000?logo=express&logoColor=white)](https://expressjs.com)
[![SQLite](https://img.shields.io/badge/SQLite-3-003B57?logo=sqlite&logoColor=white)](https://sqlite.org)
[![JWT](https://img.shields.io/badge/JWT-Auth-FB015B?logo=jsonwebtokens&logoColor=white)](https://jwt.io)
[![Tailwind CSS](https://img.shields.io/badge/Tailwind_CSS-3-06B6D4?logo=tailwindcss&logoColor=white)](https://tailwindcss.com)

---

## 📋 สารบัญ

- [ภาพรวมของโปรเจค](#-ภาพรวมของโปรเจค)
- [เทคโนโลยีที่ใช้](#-เทคโนโลยีที่ใช้)
- [โครงสร้างโปรเจค](#-โครงสร้างโปรเจค)
- [การติดตั้งและรันโปรแกรม](#-การติดตั้งและรันโปรแกรม)
- [API Endpoints](#-api-endpoints)
- [ใบงานปฏิบัติการ](#-ใบงานปฏิบัติการ)

---

## 🎯 ภาพรวมของโปรเจค

ระบบจองห้องพักออนไลน์แบบ Full-Stack ที่พัฒนาด้วย Node.js และ React ประกอบด้วย 2 ส่วนหลัก

| ส่วน | รายละเอียด |
|------|-----------|
| **Frontend** | React + Tailwind CSS — หน้าจองห้องพักสำหรับลูกค้า และ Admin Dashboard |
| **Backend** | Node.js + Express — REST API พร้อมระบบ Authentication ด้วย JWT |
| **Database** | SQLite — เก็บข้อมูลผู้ใช้ (`users`) และการจอง (`bookings`) |
| **Auth** | JWT + bcryptjs — Login/Logout พร้อม Protected Routes |

### ฟีเจอร์หลัก

- ✅ จองห้องพักออนไลน์ (ไม่ต้อง Login)
- ✅ ระบบ Login/Logout สำหรับ Admin ด้วย JWT
- ✅ Protected Routes — ป้องกันหน้า Admin โดยอัตโนมัติ
- ✅ Admin Dashboard — ดู แก้ไข และลบข้อมูลการจอง
- ✅ Token persistence — ไม่ต้อง Login ใหม่เมื่อ refresh หน้าเว็บ
- ✅ Auto logout — เมื่อ token หมดอายุ

---

## 🛠 เทคโนโลยีที่ใช้

### Backend

| Package | เวอร์ชัน | การใช้งาน |
|---------|---------|-----------|
| `express` | ^4.x | Web framework สำหรับสร้าง REST API |
| `sqlite3` | ^5.x | ฐานข้อมูล SQLite |
| `jsonwebtoken` | ^9.x | ออกและตรวจสอบ JWT token |
| `bcryptjs` | ^2.x | Hash รหัสผ่านก่อนบันทึก |
| `cors` | ^2.x | อนุญาต Cross-Origin requests |
| `body-parser` | ^1.x | แปลง JSON request body |
| `nodemon` | ^3.x | Auto-restart server (dev) |

### Frontend

| Package | เวอร์ชัน | การใช้งาน |
|---------|---------|-----------|
| `react` | ^18.x | UI Library |
| `react-router-dom` | ^6.x | Client-side routing |
| `axios` | ^1.x | HTTP client สำหรับเรียก API |
| `tailwindcss` | ^3.x | Utility-first CSS framework |
| `vite` | ^5.x | Build tool และ Dev server |

---

## 📁 โครงสร้างโปรเจค

```
hotel-booking-system/
├── backend/
│   ├── database.js          # สร้าง SQLite tables + admin account เริ่มต้น
│   ├── server.js            # REST API + JWT middleware + endpoints ทั้งหมด
│   ├── bookings.db          # ไฟล์ฐานข้อมูล (สร้างอัตโนมัติเมื่อรันครั้งแรก)
│   └── package.json
│
└── frontend/
    ├── .env                         # กำหนด VITE_API_URL (ไม่ push ขึ้น GitHub)
    ├── .env.example                 # ตัวอย่าง .env สำหรับทีม
    ├── src/
    │   ├── config.js                # อ่านค่า API_URL จาก .env — แก้ port ที่นี่ที่เดียว
    │   ├── contexts/
    │   │   └── AuthContext.jsx      # จัดการ user/token ด้วย React Context
    │   ├── components/
    │   │   ├── Login.jsx            # หน้า Login
    │   │   ├── ProtectedRoute.jsx   # Guard สำหรับ Admin pages
    │   │   ├── BookingForm.jsx      # ฟอร์มจองห้องพัก (ไม่ต้อง Login)
    │   │   ├── BookingList.jsx      # รายการจองทั้งหมด (Admin)
    │   │   ├── BookingEdit.jsx      # แก้ไขข้อมูลการจอง (Admin)
    │   │   └── AdminDashboard.jsx   # หน้าหลัก Admin
    │   ├── App.jsx                  # Route configuration
    │   └── main.jsx
    ├── tailwind.config.js
    └── package.json
```

---

## 🚀 การติดตั้งและรันโปรแกรม

### ข้อกำหนดเบื้องต้น

- [Node.js](https://nodejs.org) v18 ขึ้นไป
- npm v9 ขึ้นไป

### 1. Clone Repository

```bash
git clone https://github.com/surachai-p/Software-Design-and-Development-Booking-App-Demo.git
cd Software-Design-and-Development-Booking-App-Demo
```

### 2. ติดตั้งและรัน Backend

```bash
cd backend
npm install
npm run dev
```

Server จะรันที่ `http://localhost:3001`

ผลลัพธ์ที่ควรเห็น:
```
[nodemon] starting `node server.js`
เชื่อมต่อฐานข้อมูลสำเร็จ
Server running on port 3001
```

> **Admin account เริ่มต้น:** username: `admin` / password: `admin123`  
> (สร้างอัตโนมัติเมื่อรันครั้งแรก)

### 3. ติดตั้งและตั้งค่า Frontend

เปิด Terminal ใหม่ (ไม่ปิด Terminal ที่รัน Backend)

```bash
cd frontend
npm install
```

สร้างไฟล์ `.env` ในโฟลเดอร์ `frontend/`

```bash
# frontend/.env
VITE_API_URL=http://localhost:3001
```

> 💡 ถ้า Backend รันที่ port อื่น เช่น 3002 แก้แค่ไฟล์ `.env` บรรทัดนี้บรรทัดเดียว แล้ว restart `npm run dev`

```bash
npm run dev
```

Frontend จะรันที่ `http://localhost:5173`

---

## 📡 API Endpoints

Base URL: `http://localhost:3001`

### Authentication

| Method | Endpoint | Auth | คำอธิบาย |
|--------|----------|:----:|----------|
| `POST` | `/api/login` | ❌ | เข้าสู่ระบบ รับ JWT token |

**Request body:**
```json
{
  "username": "admin",
  "password": "admin123"
}
```

**Response:**
```json
{
  "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9...",
  "user": { "id": 1, "username": "admin", "role": "admin" }
}
```

---

### Bookings

| Method | Endpoint | Auth | คำอธิบาย |
|--------|----------|:----:|----------|
| `POST` | `/api/bookings` | ❌ | สร้างการจองใหม่ |
| `GET` | `/api/bookings` | ✅ | ดึงข้อมูลการจองทั้งหมด |
| `GET` | `/api/bookings/:id` | ✅ | ดึงข้อมูลการจองตาม ID |
| `PUT` | `/api/bookings/:id` | ✅ | แก้ไขข้อมูลการจอง |
| `DELETE` | `/api/bookings/:id` | ✅ | ลบข้อมูลการจอง |

> ✅ = ต้องส่ง Header `Authorization: Bearer <token>`

**ตัวอย่าง Request body (POST/PUT):**
```json
{
  "fullname": "สมชาย ใจดี",
  "email": "somchai@example.com",
  "phone": "0812345678",
  "checkin": "2025-03-01",
  "checkout": "2025-03-03",
  "roomtype": "standard",
  "guests": 2,
  "comment": "ต้องการห้องชั้นล่าง"
}
```

---

## 🗄 โครงสร้างฐานข้อมูล

### ตาราง `users`

| Column | Type | ข้อมูล |
|--------|------|-------|
| `id` | INTEGER PK | รหัสผู้ใช้ |
| `username` | TEXT UNIQUE | ชื่อผู้ใช้ |
| `password` | TEXT | รหัสผ่าน (bcrypt hash) |
| `role` | TEXT | `admin` หรือ `user` |
| `created_at` | TIMESTAMP | วันที่สร้าง |

### ตาราง `bookings`

| Column | Type | ข้อมูล |
|--------|------|-------|
| `id` | INTEGER PK | รหัสการจอง |
| `fullname` | TEXT | ชื่อผู้จอง |
| `email` | TEXT | อีเมล |
| `phone` | TEXT | เบอร์โทรศัพท์ |
| `checkin` | DATE | วันเช็คอิน |
| `checkout` | DATE | วันเช็คเอาท์ |
| `roomtype` | TEXT | `standard` / `deluxe` / `suite` |
| `guests` | INTEGER | จำนวนผู้เข้าพัก |
| `status` | TEXT | สถานะ (default: `pending`) |
| `comment` | TEXT | หมายเหตุ |
| `created_at` | TIMESTAMP | วันที่สร้าง |

---

## 📄 ใบงานปฏิบัติการ

| ไฟล์ | เนื้อหา |
|------|---------|
| [hotel-booking-lab.md](./hotel-booking-lab.md) | ใบงานหลัก — Full-Stack พร้อม Authentication (ใช้ร่วมกับ repo นี้) |
| [rest-api-lab.md](./rest-api-lab.md) | ใบงานพื้นฐาน — REST API ด้วย Node.js และ Python |

### หัวข้อที่ครอบคลุมใน `hotel-booking-lab.md`

**Backend**
- REST API และ HTTP Methods
- การออกแบบฐานข้อมูล (ตาราง `users` + `bookings`)
- JWT Authentication และ bcrypt password hashing
- Express Middleware (`authenticateToken`)
- ทดสอบ API ทุก endpoint ด้วย Postman

**Frontend**
- React Hooks (`useState`, `useEffect`, `useContext`, `useNavigate`)
- React Context API สำหรับ Authentication state
- Protected Routes
- Axios สำหรับเรียก REST API
- Tailwind CSS utility classes

---

## 🔒 ระบบ Authentication — ภาพรวม

```
ผู้ใช้ Login
     │
     ▼
POST /api/login ──► ตรวจสอบ username/password
                         │
              ┌──────────┴──────────┐
           ถูกต้อง              ไม่ถูกต้อง
              │                     │
              ▼                     ▼
        ออก JWT Token         401 Unauthorized
              │
              ▼
     Frontend เก็บ token
     ใน localStorage + Context
              │
              ▼
     เรียก Protected API
     ด้วย Authorization: Bearer <token>
              │
              ▼
     authenticateToken middleware
     ตรวจสอบ token ก่อนเข้าถึงข้อมูล
```

---

## 📝 License

This project is for educational purposes.
