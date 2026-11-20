# Lab L1 · Answers

## Q1 · เครื่องมือ
**ปัญหาที่พบใน `flutter doctor`:**
ตอนแรก `Android toolchain` ไม่ผ่าน โดยแจ้งว่า `Unable to locate Android SDK` และต่อมาแจ้งว่า `cmdline-tools component is missing` รวมถึง `Android license status unknown`

**เครื่องมือและวิธีแก้:**
- ใช้ **Android Studio → SDK Manager → SDK Tools** เพื่อติดตั้ง **Android SDK Command-line Tools (latest)**
- รันคำสั่ง `flutter doctor --android-licenses` เพื่อจัดการเรื่อง license
- รัน `flutter doctor` อีกครั้งจนทั้ง `Flutter` และ `Android toolchain` ขึ้น `[✓]` ครบ

---

## Q2 · Reload
เมื่อ `Likes` เป็น 3 อยู่:
- **กด `r` (Hot Reload):** ค่า `Likes` **ยังคงเป็น 3 เท่าเดิม** เพราะ Hot Reload จะฉีดโค้ดที่แก้ไขเข้าไปและสร้าง Widget tree ใหม่โดย **คงค่า State เดิม** ในหน่วยความจำไว้
- **กด `R` (Hot Restart):** ค่า `Likes` **ถูกรีเซ็ตกลับเป็น 0** เพราะ Hot Restart จะเริ่มรันแอปใหม่ตั้งแต่ฟังก์ชัน `main()` ทำให้ State ทั้งหมดถูกสร้างขึ้นใหม่

---

## Q3 · โค้ด และ Git
**ทำไม `_likes++` ต้องใช้ `setState`:**
เพราะการเพิ่มค่าตัวแปร `_likes` เพียงอย่างเดียวจะเปลี่ยนแค่ค่าในหน่วยความจำ แต่ Flutter จะไม่รู้ว่าต้องวาดหน้าจอใหม่ การครอบด้วย `setState(() { _likes++; })` เป็นการแจ้ง Framework ว่า State เปลี่ยนแล้ว ให้เรียก `build()` ใหม่เพื่ออัปเดตตัวเลขบนหน้าจอ

**ตัวอย่าง Commit (`25d7cc1` - `feat: add About me page with Like button`):**
- แก้ไขไฟล์ `lib/main.dart` เพิ่มหน้าโปรไฟล์ที่มี AppBar แสดงรหัสนักศึกษา `Lab L1 · 67121913🧑`
- แสดงไอคอน `Icons.person`, ชื่อ `Nattasit Tinawong - 67121913`, ข้อความ `Likes: $_likes` และปุ่ม `Like` (`FilledButton`) ที่เรียก `_like()` เพื่อเพิ่มค่าด้วย `setState`

---
*หมายเหตุ: ใช้ Gemini ช่วยหาวิธีการแก้ไขปัญหา (เช่น `flutter doctor` และ `cmdline-tools`) รวมถึงช่วยเรียบเรียงคำตอบในไฟล์นี้ โดยได้ลงมือทำ ตรวจสอบ และเข้าใจการทำงานของโค้ดและผลลัพธ์ด้วยตัวเองแล้ว*