# 310-126 Object-Oriented Programming (2/69)

เอกสารสำหรับนักศึกษา วิชา 310-126 OOP ภาคการศึกษา 2/69

| เอกสาร | ใช้ทำอะไร |
|---|---|
| [ANNOUNCEMENT.md](ANNOUNCEMENT.md) | ประกาศกติกาการใช้ AI และการส่งงาน (ข้อตกลงรายวิชา) |
| [Lab0-handout.md](Lab0-handout.md) / [Lab0-handout.docx](Lab0-handout.docx) | Lab 0: ติดตั้งเครื่อง Windows / macOS, สร้าง repo `310-126-oop`, ส่งงานด้วย commit SHA, ย้ายจาก `310-126-lab0` |
| [AI-tutor-prompt.md](AI-tutor-prompt.md) | tutor prompt ที่ต้องใช้ทุกครั้งที่ใช้ AI กับงานของวิชานี้ และวิธี export บทสนทนา |

## repo เดียวทั้งภาค: `310-126-oop`
ทุก Lab และ Assignment อยู่ใน repo เดียว แยกเป็นโฟลเดอร์ย่อย เช่น `Lab0/`, `Assignment1/`

**ครั้งแรกครั้งเดียว:** สร้าง repo จาก template ของรายวิชา [kasikrit/310-126-lab-template](https://github.com/kasikrit/310-126-lab-template)

```powershell
gh repo create 310-126-oop --private --template kasikrit/310-126-lab-template --clone
```

แล้วเพิ่ม collaborator 3 บัญชี **ครั้งเดียวทั้งภาค**: `kasikrit` (อาจารย์) + TA 2 คน `tonethana` และ `kroekchanwit`

**ทุกงาน:** ที่ root ของ repo สร้างโฟลเดอร์ของงานด้วย `java NewTask <ชื่อโฟลเดอร์>` (เช่น `java NewTask Assignment1`) ทำงานในโฟลเดอร์นั้น แล้วส่ง URL ของ repo (เหมือนเดิมทุกงาน) + commit SHA ผ่าน Google Form ตาม handout

**เคยสร้าง `310-126-lab0` แล้ว:** เปลี่ยนชื่อ repo เป็น `310-126-oop` และย้ายงานเข้า `Lab0/` ตามหัวข้อ "ย้ายจาก 310-126-lab0" ใน handout
