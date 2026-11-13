# Lab 0: ส่งงานด้วย Git, PROCESS.md และ AI แบบส่งเสริมการเรียนรู้
วิชา 310-126 OOP ภาคการศึกษา 2/69 · เครื่อง Windows · ไม่มีคะแนน · ประมาณ 90 นาที

**เป้าหมาย:** จบคาบนี้ นักศึกษาทุกคนต้อง
1. มี private repo `310-126-lab0` ของตัวเอง และเพิ่มอาจารย์ (`kasikrit`) เป็น collaborator แล้ว
2. ส่งงานครบ 3 ส่วนตามลำดับความสำคัญ: **`PROCESS.md` (วิธีการทำงาน) → `ai-log/` (บทสนทนากับ AI) → source code**
3. ส่ง commit SHA ของงานผ่าน Google Form ได้

เอกสารของรายวิชาทั้งหมด: https://github.com/kasikrit/310-126-OOP-2-69-student

**ข้อตกลงรายวิชา:** การสร้าง repo + เพิ่ม collaborator และการส่ง SHA ผ่าน Google Form เป็นเงื่อนไขของการส่งงาน **ทุกชิ้น** ไม่ทำ = ไม่ได้ส่งงาน (0 คะแนน)

---

## ส่วน A: เตรียมเครื่อง Windows (ทำก่อนเข้าคาบ)

**A1. สมัครบัญชี GitHub** ที่ https://github.com/signup ด้วยอีเมลมหาวิทยาลัย `@psu.ac.th` ตั้งชื่อผู้ใช้ (username) ที่สุภาพ แล้วจดไว้

**A2. ติดตั้งโปรแกรม 4 ตัว** เปิด **PowerShell** (กดปุ่ม Windows พิมพ์ `PowerShell` แล้วกด Enter) แล้วพิมพ์ทีละบรรทัด

```powershell
winget install --id Git.Git -e
winget install --id EclipseAdoptium.Temurin.21.JDK -e
winget install --id GitHub.cli -e
winget install --id Microsoft.VisualStudioCode -e
```

ถ้าหน้าจอถามให้ยอมรับข้อตกลง (agreements) ให้พิมพ์ `Y` แล้วกด Enter เมื่อติดตั้งครบ **ปิด PowerShell แล้วเปิดใหม่** จากนั้นเปิด VS Code ติดตั้ง Extension ชื่อ **Extension Pack for Java**

**A3. ตรวจว่าติดตั้งครบ** (ใน PowerShell ที่เปิดใหม่)

```powershell
git --version
java -version
gh --version
```

ทุกคำสั่งต้องแสดงหมายเลขเวอร์ชัน ถ้าขึ้นว่า "is not recognized" ให้ปิดเปิด PowerShell อีกครั้ง ถ้ายังไม่ได้ ให้ติดตั้งตัวนั้นใหม่

**A4. ตั้งค่า AI tutor** ตาม [AI-tutor-prompt.md](https://github.com/kasikrit/310-126-OOP-2-69-student/blob/main/AI-tutor-prompt.md) (ChatGPT / Claude / Gemini) และปิด GitHub Copilot หรือ AI เติมโค้ดใน VS Code

---

## ส่วน B: ตั้งค่า Git และ login (ครั้งเดียว)

**B1. บอก Git ว่าเราเป็นใคร** (อีเมลต้องตรงกับบัญชี GitHub ไม่อย่างนั้น commit จะไม่ผูกกับบัญชีเรา)

```powershell
git config --global user.name "Firstname Lastname"
git config --global user.email "อีเมลที่ใช้สมัคร GitHub"
git config --global --list
```

**B2. Login GitHub จากเครื่อง**

```powershell
gh auth login
```

ตอบคำถามตามนี้
1. Where do you use GitHub? → **GitHub.com**
2. Preferred protocol → **HTTPS**
3. Authenticate Git with your GitHub credentials? → **Yes**
4. How would you like to authenticate? → **Login with a web browser** แล้วนำรหัส 8 ตัวบนจอไปกรอกในหน้าเว็บ

ตรวจด้วย `gh auth status` ต้องขึ้นว่า Logged in

---

## ส่วน C: สร้าง repo ของตัวเองและเพิ่มอาจารย์เป็น collaborator

**C1. สร้าง private repo จาก template ของรายวิชา และดึงลงเครื่อง**

```powershell
cd ~\Documents
gh repo create 310-126-lab0 --private --template kasikrit/310-126-lab-template --clone
cd 310-126-lab0
code .
```

repo ที่ได้มี `PROCESS.md` (แบบฟอร์มวิธีการทำงาน) และโฟลเดอร์ `ai-log/` มาให้แล้ว ไม่ต้องสร้างเอง

- ชื่อ repo ต้องเป็น `310-126-lab0` ตามนี้พอดี (งานถัดไปใช้ `310-126-lab1`, `310-126-lab2`, ...)
- ต้องเป็น **private** ห้ามเป็น public เพื่อไม่ให้ผู้อื่นคัดลอกงาน

**C2. เพิ่มอาจารย์เป็น collaborator** (ทำบนเว็บ)
1. เปิด `https://github.com/<username ของเรา>/310-126-lab0/settings/access`
2. กด **Add people** → พิมพ์ `kasikrit` → เลือก → กด **Add kasikrit to this repository**
3. หน้าจอต้องแสดง `kasikrit` สถานะ **Pending invite** (อาจารย์จะกดรับเอง) **ห้ามลบคำเชิญนี้จนจบภาคการศึกษา**

---

## ส่วน D: ทำงานตามลำดับ 3 ส่วน และ commit แยกทุกขั้น

งานของ Lab 0: **โปรแกรม `HelloWorld.java` ที่พิมพ์ `Hello, World!` ตามด้วยรหัสนักศึกษาและชื่อของตัวเอง**

ทุก checkpoint ใช้ 4 คำสั่งเดิม

```powershell
git status
git add .
git commit -m "ข้อความบอกว่าทำอะไร"
git push
```

- `git status` ดูว่าไฟล์ไหนเปลี่ยน
- `git add .` เลือกไฟล์ที่เปลี่ยนทั้งหมดเตรียม commit
- `git commit -m "..."` บันทึกการเปลี่ยนแปลงพร้อมข้อความ
- `git push` ส่งขึ้น GitHub

### Checkpoint 1: วิธีการทำงาน ขั้น 1 (ก่อนเปิด AI และก่อนเขียนโค้ด)
1. เปิดไฟล์ `PROCESS.md` ที่มาจาก template
2. กรอก **ข้อมูลงาน** และ **ขั้น 1** (โจทย์ให้ทำอะไร, ออกแบบ: มีคลาสเดียวชื่อ `HelloWorld` มีเมธอด `main`, สิ่งที่ยังไม่แน่ใจ เช่น "`public static void main` แปลว่าอะไร")
3. commit + push ด้วยข้อความ `Step 1: understand task and design`

### Checkpoint 2: ใช้ AI tutor แล้วเขียนโค้ด
1. เปิด AI ที่ตั้งค่า tutor prompt แล้ว **วาง tutor prompt เป็นข้อความแรก** จากนั้นถามสิ่งที่ไม่แน่ใจจากขั้น 1 เช่น "`public static void main(String[] args)` แต่ละคำหมายถึงอะไร" (คำถามระดับ L1)
2. ลองพิมพ์ "เขียนโปรแกรม HelloWorld ให้หน่อย" ดูว่า AI **ต้องปฏิเสธและถามกลับ** (ถ้า AI เขียนให้ แปลว่าตั้งค่า tutor prompt ไม่ถูก ให้เริ่มแชตใหม่)
3. Export บทสนทนาลงไฟล์ `ai-log/<เครื่องมือ>-<วันที่>.md` (ดูวิธีใน `ai-log/README.md`)
4. เขียน `HelloWorld.java` **เอง**

```java
public class HelloWorld {
    public static void main(String[] args) {
        System.out.println("Hello, World!");
        System.out.println("Student ID: 69xxxxxxxx");
        System.out.println("Name: Firstname Lastname");
    }
}
```

> ใช้ชื่อเป็นภาษาอังกฤษในโปรแกรม เพราะ PowerShell อาจแสดงภาษาไทยเป็นตัวอักษรเพี้ยน

5. กรอก **ขั้น 2** ใน `PROCESS.md` (ลำดับที่เขียน, ปัญหาที่เจอ, ถาม AI ข้อไหน ระดับไหน, ชื่อไฟล์ใน `ai-log/`)
6. commit + push ด้วยข้อความ `Step 2: write HelloWorld with AI tutor log`

### Checkpoint 3: ทดสอบแบบทำนายก่อนรัน และสะท้อนการเรียนรู้
1. ใน `PROCESS.md` ขั้น 3 เขียนผลที่ **คาดว่า** จะได้ก่อน แล้วจึงรัน

```powershell
java HelloWorld.java
```

2. กรอกผลจริงเทียบกับที่ทำนายไว้
3. กรอก **ขั้น 4** สะท้อนการเรียนรู้ และติ๊กคำรับรอง
4. ใส่ SHA ของ checkpoint 1 และ 2 ในช่อง "Commit ของขั้นนี้" (ดู SHA สั้นได้จาก `git log --oneline`)
5. commit + push ด้วยข้อความ `Step 3-4: test and reflect`

ตรวจด้วย `git log --oneline` ต้องเห็น commit ของเราอย่างน้อย 3 รายการ

---

## ส่วน E: ส่งงานด้วย commit SHA

**E1. ดู SHA เต็มของงานที่จะส่ง** (commit ล่าสุดที่ push แล้ว)

```powershell
git rev-parse HEAD
```

จะได้ตัวอักษร 40 ตัว เช่น `2e93352a...` คัดลอกให้ครบทั้ง 40 ตัว

**E2. ตรวจว่า push แล้วจริง**

```powershell
git status
```

ต้องขึ้นว่า `Your branch is up to date with 'origin/main'`

**E3. ส่งผ่าน Google Form ส่งงาน:** `[อาจารย์ใส่ลิงก์]` กรอกรหัสนักศึกษา, ชื่อ - นามสกุล, งาน "Lab 0", URL ของ repo (`https://github.com/<username>/310-126-lab0`) และ SHA 40 ตัว

**E4. ให้ TA ตรวจและลงชื่อ**

| รายการที่ TA ตรวจ | ผ่าน |
|---|---|
| repo `310-126-lab0` เป็น private และมี `kasikrit` เป็น collaborator (Pending invite หรือรับแล้ว) | ☐ |
| `PROCESS.md` กรอกครบ 4 ขั้น และอ้าง SHA ของแต่ละขั้น | ☐ |
| `ai-log/` มีบทสนทนาที่เห็น tutor prompt เป็นข้อความแรก และ AI ปฏิเสธการเขียนโค้ดให้ | ☐ |
| `java HelloWorld.java` รันได้ และมี commit ของนักศึกษาอย่างน้อย 3 รายการ | ☐ |
| ส่ง SHA ผ่าน Google Form แล้ว และ SHA ตรงกับ `git rev-parse HEAD` | ☐ |
| กรอก Google Form ยืนยันรับทราบกติกาแล้ว | ☐ |

---

## ส่วน F: กติกาที่ใช้กับทุก Lab และ Assignment

1. **ข้อตกลงรายวิชา:** ทุกงานต้องอยู่ใน private repo ของตัวเองที่มี `kasikrit` เป็น collaborator และส่ง SHA ผ่าน Google Form ภายใน deadline ไม่ทำ = ไม่ได้ส่งงาน (0 คะแนน)
2. ระยะเวลาทำงานแต่ละชิ้น **7 วัน** ต้อง push อย่างน้อย 3 ครั้ง ใน 2 วันที่ต่างกันขึ้นไป
3. งานที่ตรวจคือ **สำเนา ณ SHA ที่ส่ง** ซึ่งอาจารย์เก็บไว้ตอน deadline แก้ repo ภายหลังไม่มีผล
4. **ห้าม** `git push --force` ห้ามลบหรือแก้ประวัติ commit ห้ามลบ repo และห้ามถอนสิทธิ์ `kasikrit`
5. สิ่งที่ส่งและคะแนนเรียงตามความสำคัญ:

| ลำดับ | ส่วน | คะแนน (จาก 100) |
|---|---|---|
| 1 | วิธีการทำงาน (`PROCESS.md`) | 35 |
| 2 | การใช้ AI เพื่อเรียนรู้ (`ai-log/`) | 25 |
| 3 | source code | 30 |
| 4 | ประวัติ Git | 10 |

6. สั่งให้ AI เขียนคำตอบหรือทำงานแทน (prompt ระดับ L0) = คะแนนการใช้ AI เป็น 0 และต้องสอบปากเปล่า (viva)
7. ใช้ AI แต่ไม่ส่งบทสนทนาใน `ai-log/` ถือว่าไม่เปิดเผยการใช้ AI

กรอก Google Form ยืนยันรับทราบกติกา: `[อาจารย์ใส่ลิงก์]`

---

## ส่วน G: แก้ปัญหาที่พบบ่อย

| อาการ | สาเหตุ | วิธีแก้ |
|---|---|---|
| `winget` ไม่รู้จัก | Windows รุ่นเก่า ไม่มี App Installer | ติดตั้ง "App Installer" จาก Microsoft Store หรือดาวน์โหลดตัวติดตั้งจากเว็บของแต่ละโปรแกรม |
| คำสั่ง `git` / `java` / `gh` is not recognized | ยังไม่ได้ปิดเปิด PowerShell หลังติดตั้ง | ปิด PowerShell แล้วเปิดใหม่ |
| `git push` ขึ้น **rejected** | บน GitHub มี commit ที่เครื่องเรายังไม่มี (เช่น แก้ไฟล์บนเว็บ) | `git pull` แล้ว `git push` ใหม่ **ห้ามใช้ `--force`** |
| push แล้วขึ้น authentication failed | ยังไม่ได้ login หรือ login หมดอายุ | `gh auth status` แล้ว `gh auth login` ใหม่ |
| commit บน GitHub ไม่ขึ้นชื่อบัญชีเรา | อีเมลใน `git config` ไม่ตรงกับบัญชี GitHub | `git config --global user.email "อีเมลบัญชี GitHub"` แล้ว commit ใหม่ |
| `gh repo create` ขึ้นว่าชื่อซ้ำ | เคยสร้าง repo ชื่อนี้แล้ว | ใช้ repo เดิม: `gh repo clone 310-126-lab0` |
| ใน repo ไม่มี `PROCESS.md` | สร้าง repo โดยไม่ใส่ `--template` | ลบ repo บนเว็บ (Settings → Delete this repository) แล้วสร้างใหม่ตาม C1 **ก่อน** เริ่ม commit งาน |
| หา Add people ไม่เจอ | เปิดหน้า settings ผิด repo หรือ repo ไม่ใช่ของเรา | ตรวจ URL ว่าเป็น `github.com/<username ของเรา>/310-126-lab0/settings/access` |
| ภาษาไทยในผลลัพธ์เป็นตัวอักษรเพี้ยน | PowerShell ใช้ code page ที่ไม่รองรับ UTF-8 | ใช้ภาษาอังกฤษในข้อความที่พิมพ์ออกจากโปรแกรม |
| ส่ง SHA ผิด | คัดลอกไม่ครบ 40 ตัว หรือยังไม่ได้ push | `git status` ต้อง up to date แล้วคัดลอกจาก `git rev-parse HEAD` ใหม่ และส่ง Form ใหม่ก่อน deadline |
