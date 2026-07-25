# 🔥 Calorie Deficit Tracker

เว็บแอป (PWA) ติดตามแคลอรี่ขาดดุลเพื่อลดน้ำหนัก — ทำงานออฟไลน์ ติดตั้งลงมือถือได้ ข้อมูลเก็บในเครื่อง 100%

## ฟีเจอร์
- **คำนวณ TDEE & เป้าหมาย** — สูตร Mifflin–St Jeor + macro targets (โปรตีน 2g/กก., ไขมัน 25%, ที่เหลือคาร์บ)
- **บันทึกอาหาร** — ค้นจากฐานข้อมูลอาหารไทย ~100 เมนู 9 หมวด (อาหารเช้า/ข้าว-เส้น/โปรตีน/กับข้าว/ฟาสต์ฟู้ด/ผลไม้/เครื่องดื่ม/ขนม) หรือเพิ่มเอง ระบุจำนวนหน่วยได้
- **Macros** — โปรตีน/คาร์บ/ไขมัน พร้อมแถบเทียบเป้าหมายรายวัน
- **ออกกำลังกาย** — จดกิจกรรม (มี preset) แคลที่เผาบวกเข้า deficit ของวัน
- **ดื่มน้ำ** — แตะแก้วนับ 8 แก้ว/วัน (250ml/แก้ว)
- **Streak** — นับวันติดต่อกันที่ทำ deficit สำเร็จ (🔥 x วันติด)
- **น้ำหนัก + กราฟเส้น** — สรุปเริ่มต้น/ล่าสุด/ต่ำสุด/เปลี่ยนแปลง
- **สรุป deficit สะสม** — ประเมินไขมันที่ลดได้ (7,700 kcal ≈ 1 กก.) + กราฟแท่ง 14 วัน
- **Backup/Import** ข้อมูลเป็นไฟล์ JSON

## ไฟล์
```
index.html      แอปทั้งหมด (HTML + CSS + JS ในไฟล์เดียว)
manifest.json   ข้อมูล PWA
sw.js           service worker (ออฟไลน์)
icon-*.png      ไอคอนแอป
```

## รันในเครื่อง (ต้องผ่าน http เพื่อให้ PWA/ออฟไลน์ทำงาน)
```bash
cd calorie-deficit-tracker
python3 -m http.server 8848
# เปิด http://localhost:8848
```
เปิดจากมือถือในวง Wi-Fi เดียวกัน: `http://<IP-เครื่อง>:8848`

## Deploy ขึ้นเว็บจริง (ฟรี — เลือกอย่างใดอย่างหนึ่ง)

**1) Netlify Drop (ง่ายสุด ไม่ต้องมี account เริ่มต้น)**
- ไปที่ https://app.netlify.com/drop → ลากโฟลเดอร์ `calorie-deficit-tracker` ทั้งโฟลเดอร์เข้าไป
- ได้ URL สาธารณะทันที เปิดจากมือถือแล้ว "เพิ่มไปยังหน้าจอโฮม" ได้เลย

**2) GitHub Pages**
```bash
cd calorie-deficit-tracker
git init && git add . && git commit -m "calorie deficit tracker"
gh repo create calorie-tracker --public --source=. --push
# เปิด Settings → Pages → Branch: main / root → Save
# ได้ URL: https://<user>.github.io/calorie-tracker/
```

**3) Vercel** — `npx vercel` ในโฟลเดอร์นี้

## ติดตั้งลงมือถือ (หลัง deploy หรือรันผ่าน http)
- **Android/Chrome:** จะมีปุ่ม "📲 ติดตั้งแอป" ในแท็บ 🧮 หรือเมนู ⋮ → "ติดตั้งแอป"
- **iPhone/Safari:** ปุ่มแชร์ ▵ → "เพิ่มไปยังหน้าจอโฮม"
