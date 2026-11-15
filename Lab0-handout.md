# Lab 0: ส่งงานด้วย Git, PROCESS.md, Run.java และ AI แบบส่งเสริมการเรียนรู้
วิชา 310-126 OOP ภาคการศึกษา 2/69 · เครื่อง Windows หรือ macOS · ไม่มีคะแนน · ประมาณ 90 นาที

**เป้าหมาย:** จบคาบนี้ นักศึกษาทุกคนต้อง
1. มี private repo `310-126-lab0` ของตัวเอง และเพิ่มอาจารย์ (`kasikrit`) เป็น collaborator แล้ว
2. ส่งงานครบตามลำดับ: **`PROCESS.md` ขั้น 1 (เข้าใจโจทย์และออกแบบ) → `ai-log/` (บทสนทนากับ AI) → source code + `outputs.txt` (ผลการรันจาก `java Run.java`)**
3. ส่ง commit SHA ของงานผ่าน Google Form ได้

เอกสารของรายวิชาทั้งหมด: https://github.com/kasikrit/310-126-OOP-2-69-student

**ข้อตกลงรายวิชา:** การสร้าง repo + เพิ่ม collaborator และการส่ง SHA ผ่าน Google Form เป็นเงื่อนไขของการส่งงาน **ทุกชิ้น** ไม่ทำ = ไม่ได้ส่งงาน (0 คะแนน)

---

## ส่วน A: เตรียมเครื่อง Windows หรือ macOS (ทำก่อนเข้าคาบ)

ทำ A1 แล้วเลือกทำ **A2–A3 ตามระบบปฏิบัติการของเครื่องตัวเอง** (Windows หรือ macOS) จากนั้นทำ A4
ตั้งแต่ส่วน B เป็นต้นไป คำสั่งเหมือนกันทั้งสองระบบ พิมพ์ใน **PowerShell** (Windows) หรือ **Terminal** (macOS)

**A1. สมัครบัญชี GitHub** ที่ https://github.com/signup ด้วยอีเมลมหาวิทยาลัย `@psu.ac.th` และ **ตั้งชื่อผู้ใช้ (username) เป็นรหัสนักศึกษา 10 หลัก** เช่น `6910210001`
- ถ้า GitHub แจ้งว่าชื่อนี้มีผู้ใช้แล้ว ให้ใช้ `s` นำหน้ารหัส เช่น `s6910210001` และแจ้ง TA
- ถ้ามีบัญชี GitHub อยู่แล้ว ไม่ต้องสมัครใหม่ ให้เปลี่ยน username เป็นรหัสนักศึกษาที่ Settings → Account → **Change username** (repo เดิมยังอยู่ ลิงก์เดิมจะพาไปที่ชื่อใหม่ให้อัตโนมัติ)

### Windows

**A2-W. ติดตั้งโปรแกรม 4 ตัว** เปิด **PowerShell** (กดปุ่ม Windows พิมพ์ `PowerShell` แล้วกด Enter) แล้วพิมพ์ทีละบรรทัด

```powershell
winget install --id Git.Git -e
winget install --id EclipseAdoptium.Temurin.21.JDK -e
winget install --id GitHub.cli -e
winget install --id Microsoft.VisualStudioCode -e
```

ถ้าหน้าจอถามให้ยอมรับข้อตกลง (agreements) ให้พิมพ์ `Y` แล้วกด Enter เมื่อติดตั้งครบ **ปิด PowerShell แล้วเปิดใหม่** จากนั้นเปิด VS Code ติดตั้ง Extension ชื่อ **Extension Pack for Java**

**A3-W. ตรวจว่าติดตั้งครบ** (ใน PowerShell ที่เปิดใหม่)

```powershell
git --version
java -version
gh --version
```

ทุกคำสั่งต้องแสดงหมายเลขเวอร์ชัน ถ้าขึ้นว่า "is not recognized" ให้ปิดเปิด PowerShell อีกครั้ง ถ้ายังไม่ได้ ให้ติดตั้งตัวนั้นใหม่

### macOS

**A2-M. ติดตั้งโปรแกรม 4 ตัว** เปิด **Terminal** (กด `Command + Space` พิมพ์ `Terminal` แล้วกด Enter)

1. ติดตั้ง Homebrew (ตัวติดตั้งโปรแกรมของ macOS) ถ้ายังไม่มี ตรวจด้วย `brew --version` ถ้าขึ้น "command not found" ให้ติดตั้งด้วยคำสั่งจาก https://brew.sh

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

   ระหว่างติดตั้งจะถามรหัสผ่านเครื่อง (พิมพ์แล้วไม่แสดงบนจอ เป็นเรื่องปกติ) เมื่อเสร็จ ให้ทำตามข้อความ **Next steps** ที่ขึ้นท้ายจอ (เครื่อง Apple Silicon ต้องรันคำสั่ง 2 บรรทัดที่แสดงไว้) แล้ว **ปิด Terminal และเปิดใหม่**

2. ติดตั้งโปรแกรม พิมพ์ทีละบรรทัด

```bash
brew install git gh
brew install --cask temurin@21
brew install --cask visual-studio-code
```

   จากนั้นเปิด VS Code ติดตั้ง Extension ชื่อ **Extension Pack for Java**

**A3-M. ตรวจว่าติดตั้งครบ** (ใน Terminal ที่เปิดใหม่)

```bash
git --version
java -version
gh --version
```

ทุกคำสั่งต้องแสดงหมายเลขเวอร์ชัน ถ้าขึ้นว่า "command not found" ให้ปิดเปิด Terminal อีกครั้ง ถ้ายังไม่ได้ ให้ติดตั้งตัวนั้นใหม่ ถ้า `java -version` ขึ้นหน้าต่างให้ติดตั้ง Java ให้กดปิด แล้วรัน `brew install --cask temurin@21` ใหม่

**A4. ตั้งค่า AI tutor** ตาม [AI-tutor-prompt.md](https://github.com/kasikrit/310-126-OOP-2-69-student/blob/main/AI-tutor-prompt.md) ใช้ได้ **เฉพาะแบบแชตบนเว็บหรือแอป** (ChatGPT / Claude / Gemini) ปิด GitHub Copilot หรือ AI เติมโค้ดใน VS Code และ **ห้ามใช้ AI ที่แก้ไฟล์หรือรันคำสั่งในเครื่องได้** (เช่น Claude Code, Cursor หรือ Copilot แบบ agent mode, Codex)

---

## ส่วน B: ตั้งค่า Git และ login (ครั้งเดียว)

**B1. บอก Git ว่าเราเป็นใคร** (อีเมลต้องตรงกับบัญชี GitHub ไม่อย่างนั้น commit จะไม่ผูกกับบัญชีเรา)

```shell
git config --global user.name "Firstname Lastname"
git config --global user.email "อีเมลที่ใช้สมัคร GitHub"
git config --global --list
```

**B2. Login GitHub จากเครื่อง**

```shell
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

```shell
cd ~/Documents
gh repo create 310-126-lab0 --private --template kasikrit/310-126-lab-template --clone
cd 310-126-lab0
code .
```

repo ที่ได้มีไฟล์จาก template มาให้แล้ว ไม่ต้องสร้างเอง:
- `PROCESS.md`: ขั้น 1 เข้าใจโจทย์และออกแบบ + คำรับรอง
- `ai-log/`: โฟลเดอร์เก็บบทสนทนากับ AI
- `Run.java`: ตัวช่วยรันของรายวิชา บันทึกผลการรันลง `outputs.txt` (ห้ามแก้ทั้งสองไฟล์)

- ชื่อ repo ต้องเป็น `310-126-lab0` ตามนี้พอดี (งานถัดไปใช้ `310-126-lab1`, `310-126-lab2`, ...)
- ต้องเป็น **private** ห้ามเป็น public เพื่อไม่ให้ผู้อื่นคัดลอกงาน

**C2. เพิ่มอาจารย์และ TA เป็น collaborator 3 บัญชี** (ทำบนเว็บ)
1. เปิด `https://github.com/<รหัสนักศึกษา>/310-126-lab0/settings/access`
2. กด **Add people** → พิมพ์ `kasikrit` → เลือก → กด **Add kasikrit to this repository**
3. ทำซ้ำข้อ 2 กับ TA อีก 2 บัญชี: `[username ของ TA1]` และ `[username ของ TA2]`
4. หน้าจอต้องแสดงทั้ง 3 บัญชี สถานะ **Pending invite** (อาจารย์และ TA จะกดรับเอง) **ห้ามลบคำเชิญจนจบภาคการศึกษา**

---

## ส่วน D: ทำงานตามลำดับ และ commit ทุก checkpoint

งานของ Lab 0: **โปรแกรม `HelloWorld.java` ที่พิมพ์ `Hello, World!` ตามด้วยรหัสนักศึกษาและชื่อของตัวเอง**

ทุก checkpoint ใช้ 4 คำสั่งเดิม (ข้อความ commit เขียนอะไรก็ได้ที่บอกว่าทำอะไร)

```shell
git status
git add .
git commit -m "ข้อความบอกว่าทำอะไร"
git push
```

- `git status` ดูว่าไฟล์ไหนเปลี่ยน
- `git add .` เลือกไฟล์ที่เปลี่ยนทั้งหมดเตรียม commit
- `git commit -m "..."` บันทึกการเปลี่ยนแปลงพร้อมข้อความ
- `git push` ส่งขึ้น GitHub (Lab 0 ต้อง push อย่างน้อย **3 ครั้ง**)

### Checkpoint 1: กรอกขั้น 1 ใน `PROCESS.md` (ก่อนเปิด AI และก่อนเขียนโค้ด)
1. เปิดไฟล์ `PROCESS.md` ที่มาจาก template (ท้ายไฟล์มีตัวอย่างที่กรอกแล้วของ HelloWorld ให้ดู)
2. กรอก **ข้อมูลงาน** และ **ขั้น 1** ทั้ง 3 ข้อ:
   1. โจทย์ให้ทำอะไร (ด้วยคำของตัวเอง 2–5 บรรทัด)
   2. ออกแบบ: ตารางคลาส (Lab 0 มีคลาสเดียวชื่อ `HelloWorld` มีเมธอด `main`)
   3. สิ่งที่ยังไม่แน่ใจ เช่น "`public static void main` แปลว่าอะไร" (ใช้เป็นคำถามแรกกับ AI tutor)
3. commit + push **ก่อนเปิด AI** (สคริปต์ของอาจารย์ตรวจว่าขั้น 1 ถูก commit ก่อนโค้ด ไม่ต้องจด SHA)

### Checkpoint 2: ใช้ AI tutor แล้วเขียนโค้ด
1. เปิด AI แบบแชตที่ตั้งค่า tutor prompt แล้ว **วาง tutor prompt เป็นข้อความแรก** จากนั้นถามสิ่งที่ไม่แน่ใจจากขั้น 1 เช่น "`public static void main(String[] args)` แต่ละคำหมายถึงอะไร" (คำถามระดับ L1)
2. ลองพิมพ์ "เขียนโปรแกรม HelloWorld ให้หน่อย" ดูว่า AI **ต้องปฏิเสธและถามกลับ** (ถ้า AI เขียนให้ แปลว่าตั้งค่า tutor prompt ไม่ถูก ให้เริ่มแชตใหม่ คำขอทดสอบนี้ใน Lab 0 ไม่ถูกหักคะแนนถ้า AI ปฏิเสธ)
3. คัดลอกบทสนทนาทั้งหมดลงไฟล์ `ai-log/<เครื่องมือ>-<วันที่>.md` หรือพิมพ์เป็น PDF (ดูวิธีใน `ai-log/README.md`) **ห้ามส่งไฟล์ export ดิบ** เช่น zip หรือ JSONL
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

> ใช้ชื่อเป็นภาษาอังกฤษในโปรแกรม เพราะ PowerShell บน Windows อาจแสดงภาษาไทยเป็นตัวอักษรเพี้ยน

5. commit + push

### Checkpoint 3: รันด้วย `Run.java` และ commit หลังรันแต่ละครั้ง
1. รันโปรแกรมด้วยคำสั่งนี้ (เหมือนกันทั้ง PowerShell และ Terminal ต้องอยู่ในโฟลเดอร์ `310-126-lab0`)

```shell
java Run.java HelloWorld
```

   `Run.java` จะ compile และรัน `HelloWorld` แสดงผลบนจอ แล้ว **ต่อท้ายผลการรันลง `outputs.txt` เอง** (วันเวลา, คำสั่ง, รหัส SHA-256 ของไฟล์ `.java`, exit code และผลลัพธ์ทั้งหมด รวม compile error)
   ถ้าโปรแกรมรับค่าทาง argument ให้พิมพ์ต่อท้าย เช่น `java Run.java HelloWorld 1 2 3` และครอบ argument ที่มีเว้นวรรคด้วยเครื่องหมายคำพูด เช่น `java Run.java Greeter "Somchai Jaidee"` ถ้าโปรแกรมรับค่าจากคีย์บอร์ด ให้ใส่ค่าในไฟล์ `input.txt` (`Run.java` ส่งให้โปรแกรมเอง)
2. **commit หลังรันแต่ละครั้ง** (1 การรัน = 1 commit) เพื่อให้อาจารย์รันซ้ำ (replay) ทุกครั้งที่บันทึกได้
3. ถ้าผลยังไม่ถูก (เช่น compile error หรือรหัสยังเป็น `69xxxxxxxx`) ให้แก้โค้ด รัน `java Run.java HelloWorld` ใหม่ แล้ว commit อีกครั้ง
4. **ห้ามแก้ `outputs.txt` เอง** และห้ามแก้ `Run.java` อาจารย์รันโค้ดทุก commit ซ้ำแล้วเทียบกับผลใน `outputs.txt`
5. เมื่อผลถูกแล้ว ติ๊ก **คำรับรอง** ท้าย `PROCESS.md` ให้ครบ (เปลี่ยน `[ ]` เป็น `[x]`) แล้ว commit + push เป็น commit สุดท้าย

ตรวจด้วย `git log --oneline` ต้องเห็น commit ของเราอย่างน้อย 3 รายการ และ push แล้วอย่างน้อย 3 ครั้ง

---

## ส่วน E: ส่งงานด้วย commit SHA

**E1. ดู SHA เต็มของงานที่จะส่ง** (commit ล่าสุดที่ push แล้ว)

```shell
git rev-parse HEAD
```

จะได้ตัวอักษร 40 ตัว เช่น `2e93352a...` คัดลอกให้ครบทั้ง 40 ตัว

**E2. ตรวจว่า push แล้วจริง**

```shell
git status
```

ต้องขึ้นว่า `Your branch is up to date with 'origin/main'`

**E3. ส่งผ่าน Google Form ส่งงาน:** https://forms.gle/bBoW9cMVGLHi8Tgu8 กรอกรหัสนักศึกษา, ชื่อ - นามสกุล, งาน "Lab 0", URL ของ repo (`https://github.com/<รหัสนักศึกษา>/310-126-lab0`) และ SHA 40 ตัว

**E4. ให้ TA ตรวจและลงชื่อ**

| รายการที่ TA ตรวจ | ผ่าน |
|---|---|
| repo `310-126-lab0` เป็น private และมี `kasikrit` + TA 2 คนเป็น collaborator (Pending invite หรือรับแล้ว) | ☐ |
| `PROCESS.md` กรอกขั้น 1 ครบ 3 ข้อ (commit ก่อนโค้ด) และติ๊กคำรับรองครบ | ☐ |
| `ai-log/` มีบทสนทนาที่เห็น tutor prompt เป็นข้อความแรก และ AI ปฏิเสธการเขียนโค้ดให้ | ☐ |
| `java Run.java HelloWorld` รันได้, `outputs.txt` มีบล็อกผลการรัน และมี commit ของนักศึกษาอย่างน้อย 3 รายการ | ☐ |
| ส่ง SHA ผ่าน Google Form แล้ว และ SHA ตรงกับ `git rev-parse HEAD` | ☐ |
| กรอก Google Form ยืนยันรับทราบกติกาแล้ว | ☐ |

---

## ส่วน F: กติกาที่ใช้กับทุก Lab และ Assignment

1. **ข้อตกลงรายวิชา:** บัญชี GitHub ใช้รหัสนักศึกษาเป็น username และทุกงานต้องอยู่ใน private repo ของตัวเองที่มี `kasikrit` และ TA 2 คนเป็น collaborator และส่ง SHA ผ่าน Google Form ภายใน deadline ไม่ทำ = ไม่ได้ส่งงาน (0 คะแนน)
2. ระยะเวลาทำงานแต่ละชิ้น **7 วัน** ต้อง push อย่างน้อย **N ครั้ง** ภายใน 7 วันนั้น (อาจารย์กำหนด N รายงานและประกาศพร้อมโจทย์ Lab 0: N = 3)
3. งานที่ตรวจคือ **สำเนา ณ SHA ที่ส่ง** ซึ่งอาจารย์เก็บไว้ตอน deadline แก้ repo ภายหลังไม่มีผล
4. **ห้าม** `git push --force` ห้ามลบหรือแก้ประวัติ commit ห้ามลบ repo และห้ามถอนสิทธิ์ `kasikrit`
5. สิ่งที่ส่งและคะแนนต่อชิ้นงาน (100) เรียงตามความสำคัญ:

| ลำดับ | ส่วน | คะแนน | ใช้ AI | ไม่ใช้ AI (`ai-log/NONE.md`) |
|---|---|---|---|---|
| 1 | การเรียนรู้ | 65 | ขั้น 1 ใน `PROCESS.md` (15) + `ai-log/` (50) | ขั้น 1 ใน `PROCESS.md` (15) + viva โดย TA ทุกคน (50) |
| 2 | source code | 20 | รันได้, ผลถูกตามโจทย์, `outputs.txt` ตรงกับโค้ดที่ส่งเมื่ออาจารย์รันซ้ำ | เหมือนกัน |
| 3 | ประวัติ Git | 15 | push ≥ N ครั้ง (10), ไม่มี force-push (5) | เหมือนกัน |

6. คำขอให้ AI เขียนคำตอบหรือทำงานแทน (ระดับ L0): AI ปฏิเสธและไม่ได้นำผลไปใช้ = หักข้อระดับคำถาม 10 คะแนนต่อครั้ง · AI ทำให้แล้วนำไปใช้ = ข้อระดับคำถามได้ 0 และต้องสอบปากเปล่า (viva)
7. ใช้ AI แต่ไม่ส่งบทสนทนาใน `ai-log/` ถือว่าไม่เปิดเผยการใช้ AI ใช้ได้เฉพาะ AI แบบแชต และส่ง log เป็น `.md` หรือ PDF เท่านั้น
8. งานหลัง Lab 0 ที่ไม่ใช้ AI เลย: ใส่ `ai-log/NONE.md` แล้ว **TA เรียก viva ทุกคน** และใช้คะแนน viva เป็นคะแนนส่วนการเรียนรู้ 50 คะแนน (Lab 0 ต้องฝึกใช้ AI tutor อย่างน้อย 1 ครั้ง)
9. รันโปรแกรมด้วย `java Run.java <ชื่อคลาส>` ทุกครั้ง แล้ว commit ห้ามแก้ `outputs.txt` เอง

กรอก Google Form ยืนยันรับทราบกติกา: https://forms.gle/Xm1w8e5WX5JYzyFn9

---

## ส่วน G: แก้ปัญหาที่พบบ่อย

| อาการ | สาเหตุ | วิธีแก้ |
|---|---|---|
| `winget` ไม่รู้จัก (Windows) | Windows รุ่นเก่า ไม่มี App Installer | ติดตั้ง "App Installer" จาก Microsoft Store หรือดาวน์โหลดตัวติดตั้งจากเว็บของแต่ละโปรแกรม |
| คำสั่ง `git` / `java` / `gh` is not recognized (Windows) หรือ command not found (macOS) | ยังไม่ได้ปิดเปิด PowerShell / Terminal หลังติดตั้ง | ปิด PowerShell / Terminal แล้วเปิดใหม่ |
| `brew` command not found หลังติดตั้ง Homebrew (macOS) | ยังไม่ได้ทำ Next steps ที่ตัวติดตั้งแสดง | รันคำสั่งใน Next steps ที่ขึ้นท้ายการติดตั้ง แล้วเปิด Terminal ใหม่ |
| `code .` command not found (macOS) | VS Code ยังไม่ได้ลงคำสั่ง `code` | เปิด VS Code กด `Command + Shift + P` พิมพ์ `Shell Command: Install 'code' command in PATH` แล้วกด Enter |
| `git push` ขึ้น **rejected** | บน GitHub มี commit ที่เครื่องเรายังไม่มี (เช่น แก้ไฟล์บนเว็บ หรืออาจารย์ commit `FEEDBACK.md` ผลตรวจเข้ามา) | `git pull` แล้ว `git push` ใหม่ **ห้ามใช้ `--force`** |
| push แล้วขึ้น authentication failed | ยังไม่ได้ login หรือ login หมดอายุ | `gh auth status` แล้ว `gh auth login` ใหม่ |
| commit บน GitHub ไม่ขึ้นชื่อบัญชีเรา | อีเมลใน `git config` ไม่ตรงกับบัญชี GitHub | `git config --global user.email "อีเมลบัญชี GitHub"` แล้ว commit ใหม่ |
| `gh repo create` ขึ้นว่าชื่อซ้ำ | เคยสร้าง repo ชื่อนี้แล้ว | ใช้ repo เดิม: `gh repo clone 310-126-lab0` |
| ใน repo ไม่มี `PROCESS.md` | สร้าง repo โดยไม่ใส่ `--template` | ลบ repo บนเว็บ (Settings → Delete this repository) แล้วสร้างใหม่ตาม C1 **ก่อน** เริ่ม commit งาน |
| หา Add people ไม่เจอ | เปิดหน้า settings ผิด repo หรือ repo ไม่ใช่ของเรา | ตรวจ URL ว่าเป็น `github.com/<รหัสนักศึกษา>/310-126-lab0/settings/access` |
| ภาษาไทยในผลลัพธ์เป็นตัวอักษรเพี้ยน (Windows) | PowerShell ใช้ code page ที่ไม่รองรับ UTF-8 | ใช้ภาษาอังกฤษในข้อความที่พิมพ์ออกจากโปรแกรม |
| ส่ง SHA ผิด | คัดลอกไม่ครบ 40 ตัว หรือยังไม่ได้ push | `git status` ต้อง up to date แล้วคัดลอกจาก `git rev-parse HEAD` ใหม่ และส่ง Form ใหม่ก่อน deadline |
| `Run.java: HelloWorld.java not found` | รันนอกโฟลเดอร์ repo หรือชื่อไฟล์ไม่ตรงกับชื่อคลาส | `cd` เข้าโฟลเดอร์ `310-126-lab0` ก่อน และตั้งชื่อไฟล์ให้ตรงกับชื่อคลาส (ตัวพิมพ์เล็ก/ใหญ่ต้องตรง) |
| `Run.java: no Java compiler found` | เครื่องมีแค่ JRE ไม่ใช่ JDK | ติดตั้ง JDK ตาม A2 (Temurin 21) แล้วเปิด PowerShell / Terminal ใหม่ |
| ลืม commit หลังรันครั้งสุดท้าย (หรือแก้โค้ดหลังรันครั้งสุดท้าย) | บล็อกสุดท้ายใน `outputs.txt` ไม่ตรงกับโค้ดที่ส่ง | รัน `java Run.java HelloWorld` อีกครั้งกับโค้ดล่าสุด แล้ว `git add .` + `git commit` + `git push` **ห้ามลบหรือแก้บล็อกเดิม** ใน `outputs.txt` |
| รันหลายครั้งก่อน commit ครั้งเดียว | ไม่ผิดกติกา แต่บล็อกที่โค้ดไม่อยู่ใน commit ใดอาจารย์ตรวจซ้ำไม่ได้ | ครั้งต่อไป commit หลังรันแต่ละครั้ง |
| โปรแกรมค้าง ไม่จบ | โปรแกรมรอรับค่าจากคีย์บอร์ด หรือวนไม่รู้จบ | ใส่ค่าที่ต้องพิมพ์ใน `input.txt` `Run.java` หยุดโปรแกรมเองหลัง 30 วินาที |
