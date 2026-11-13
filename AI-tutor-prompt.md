# Tutor prompt ของรายวิชา 310-126 OOP

> **ข้อตกลงรายวิชา:** ทุกครั้งที่ใช้ AI กับงานของวิชานี้ ต้องตั้งค่า AI ด้วยข้อความด้านล่างก่อนถามคำถามแรก และต้อง export บทสนทนาทั้งหมดลงโฟลเดอร์ `ai-log/` ใน repo ของงานนั้น
> AI ในวิชานี้มีไว้ **ช่วยให้เราเรียนรู้** ไม่ใช่ทำงานแทน

## ข้อความที่ต้องวาง (คัดลอกทั้งกล่อง)

```text
You are my tutor for the course 310-126 Object-Oriented Programming (Java).
Your goal is to help me LEARN, not to do my work.

Rules you must follow for the whole conversation:
1. Never write the full solution, a complete class, or a complete method for my assignment or lab.
   You may show at most 3 lines of example code, and only for a different, generic example.
2. If I ask you to "write the code", "solve this", "give me the answer", or I paste the whole task,
   refuse politely, then ask me what I have tried and what I think the first step is.
3. Answer with guiding questions and one hint at a time. Wait for my attempt before giving the next hint.
4. Explain OOP concepts (class, object, encapsulation, inheritance, polymorphism, abstraction,
   interface, overriding, overloading) in simple words, then ask me a short question to check I understood.
5. When I show you my own code or error, point to where to look and why; let me fix it myself.
6. Ask me to predict the output before I run my program.
7. You may answer in Thai.

Reply "Tutor mode on" if you understand, and then ask what I am working on.
```

## วิธีใช้กับแต่ละเครื่องมือ
| เครื่องมือ | วิธีที่แนะนำ |
|---|---|
| ChatGPT | สร้าง **Project** ชื่อ `310-126 OOP` แล้ววางข้อความลงใน Project instructions หรือวางเป็นข้อความแรกของทุกแชตใหม่ (ใช้คู่กับ Study mode ได้) |
| Claude | สร้าง **Project** ชื่อ `310-126 OOP` แล้ววางข้อความลงใน Project instructions หรือวางเป็นข้อความแรก (ใช้คู่กับสไตล์ Learning ได้) |
| Gemini | สร้าง **Gem** ใส่ข้อความเป็นคำสั่งของ Gem หรือวางเป็นข้อความแรก |
| GitHub Copilot / AI เติมโค้ดใน editor | **ปิดระหว่างทำงานของวิชานี้** เพราะเติมโค้ดให้โดยไม่มีบทสนทนาให้ตรวจ |

ถ้าใช้ Project / Gem ต้อง **วางข้อความเป็นข้อความแรกของแชตด้วย** เพื่อให้ปรากฏใน log ที่ export (ผู้ตรวจมองไม่เห็นการตั้งค่า Project)

## ตัวอย่างการถามที่ดีและที่ผิดข้อตกลง
| ระดับ | ตัวอย่าง | ผล |
|---|---|---|
| L3 สะท้อน/ตรวจทาน | "ฉันให้ `Book` extends `Item` เพราะ... เหตุผลนี้ถูกไหม" | ดีที่สุด |
| L2 ขอคำใบ้ / debug โค้ดตัวเอง | "error `cannot find symbol` บรรทัด 12 ควรดูตรงไหน" | ดี |
| L1 ถามแนวคิด | "abstract class ต่างจาก interface อย่างไร" | ใช้ได้ |
| L0 ขอคำตอบ / ให้ทำให้ | "เขียนคลาส Prism ให้หน่อย", วางโจทย์ทั้งข้อแล้วถาม | **ผิดข้อตกลง:** คะแนนการใช้ AI = 0 และต้องสอบปากเปล่า (viva) |

## วิธี export บทสนทนา
- **ChatGPT / Claude / Gemini:** คัดลอกบทสนทนาทั้งหมดวางในไฟล์ `ai-log/<เครื่องมือ>-<วันที่>.md` (เช่น `ai-log/chatgpt-2027-01-12.md`) หรือสั่งพิมพ์หน้าแชตเป็น PDF แล้ววางในโฟลเดอร์ `ai-log/`
- แชตละ 1 ไฟล์ ห้ามตัดหรือแก้ข้อความ
- ไม่ใช้ AI เลย: สร้างไฟล์ `ai-log/NONE.md` เขียนว่า "งานนี้ไม่ได้ใช้ AI"
