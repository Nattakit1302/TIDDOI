# TIDDOI — พอร์ตหุ้นสหรัฐฯ ของคุณ

แอพติดตามพอร์ตหุ้นสหรัฐฯ แบบหลายพอร์ตย่อย พร้อมราคาเรียลไทม์จาก Finnhub, จำลองซื้อ/ขาย,
คำนวณกำไรขาดทุนล่วงหน้า, และแปลงสกุลเงิน USD/THB

ข้อมูลทั้งหมดเก็บไว้ใน **localStorage ของเบราว์เซอร์เท่านั้น** — ไม่มีเซิร์ฟเวอร์ ไม่มีฐานข้อมูล
ไม่มีการส่งข้อมูลพอร์ตของคุณไปที่ไหนเลย (ยกเว้นการเรียก API ราคาหุ้น/อัตราแลกเปลี่ยนตามสัญลักษณ์ที่คุณเพิ่มเอง)

## รันบนเครื่องตัวเอง

ต้องมี [Node.js](https://nodejs.org) (เวอร์ชัน 18 ขึ้นไป) ติดตั้งไว้ก่อน

```bash
npm install
npm run dev
```

จะเปิดที่ `http://localhost:5173` — เปิดด้วยเบราว์เซอร์จริง (ไม่ใช่ sandbox) จึงดึงราคาหุ้นและอัตราแลกเปลี่ยนได้ตามปกติ

## Build สำหรับ production

```bash
npm run build
```

ไฟล์ที่ build แล้วจะอยู่ในโฟลเดอร์ `dist/`

ตรวจสอบ build ก่อนปล่อยจริงได้ด้วย:

```bash
npm run preview
```

## Deploy ขึ้น Vercel (แนะนำ)

1. สมัครบัญชีฟรีที่ [vercel.com](https://vercel.com)
2. กด "Add New… → Project" แล้วอัปโหลดโฟลเดอร์นี้ (หรือเชื่อมกับ GitHub repo)
3. Vercel จะตรวจพบว่าเป็นโปรเจกต์ Vite อัตโนมัติ — ใช้ค่าเริ่มต้นได้เลย (Build command: `npm run build`, Output directory: `dist`)
4. กด Deploy จะได้ลิงก์ เช่น `your-app.vercel.app`

## ใช้งานบน iPhone

เปิดลิงก์ที่ deploy แล้วด้วย Safari บน iPhone จากนั้นกดปุ่มแชร์ → **"เพิ่มลงหน้าจอโฮม"**
(Add to Home Screen) จะได้ไอคอนแอพเต็มจอ ใช้งานเหมือนแอพจริงโดยไม่ต้องผ่าน App Store

## การตั้งค่า API Key

แอพนี้ต้องใช้ **Finnhub API key** (ฟรี) เพื่อดึงราคาหุ้นจริง:

1. สมัครฟรีที่ [finnhub.io/register](https://finnhub.io/register)
2. คัดลอก API key มาใส่ในหน้า "ตั้งค่า" ของแอพ
3. แผนฟรีจำกัดประมาณ 60 คำขอ/นาที — เพียงพอสำหรับใช้งานส่วนตัว

API key จะถูกเก็บไว้ใน localStorage ของเบราว์เซอร์คุณเท่านั้น ไม่ถูกส่งไปที่อื่น

## อัตราแลกเปลี่ยน USD/THB

ดึงจากแหล่งข้อมูลฟรีหลายแหล่ง (Frankfurter, ExchangeRate-API และอื่นๆ) แบบสำรองกันอัตโนมัติ
ไม่ต้องตั้งค่าอะไรเพิ่ม

## โครงสร้างไฟล์

```
.
├── index.html          จุดเริ่มต้นของหน้าเว็บ
├── src/
│   ├── main.tsx         จุดเริ่ม render React
│   ├── App.tsx          โค้ดแอพทั้งหมด (component, logic, storage)
│   └── index.css        สไตล์พื้นฐาน
├── public/
│   └── favicon.svg
├── package.json
├── vite.config.ts
├── tsconfig.json
└── vercel.json
```
