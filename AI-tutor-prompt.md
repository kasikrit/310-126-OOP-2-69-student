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
| ระดับ | ลักษณะ | ผล |
|---|---|---|
| L3 สะท้อน / ตรวจทาน | ให้ AI ตรวจความคิดหรือการออกแบบที่ **เราทำเองแล้ว** | ดีที่สุด |
| L2 ขอคำใบ้ / debug โค้ดตัวเอง | ถามเรื่องโค้ดหรือ error **ของเราเอง** และขอแค่ทิศทาง | ดี |
| L1 ถามแนวคิด | ถามความหมายหรือความแตกต่างของแนวคิด OOP / Java ทั่วไป | ใช้ได้ |
| L0 ขอคำตอบ / ให้ทำให้ | ให้ AI เขียนโค้ด ออกแบบ หรือตอบโจทย์แทน | **ผิดข้อตกลง:** คะแนนการใช้ AI = 0 และต้องสอบปากเปล่า (viva) |

### L3 สะท้อน / ตรวจทาน (ดีที่สุด)
| ตัวอย่างคำถาม | ทำไมจึงเป็น L3 |
|---|---|
| "ฉันให้ `RightTriangularPrism` extends `RightTriangle` เพราะปริซึมใช้ฐานและสูงของสามเหลี่ยม เหตุผลนี้เป็นความสัมพันธ์ is-a ที่ถูกต้องไหม หรือควรเป็น has-a" | เสนอการออกแบบของตัวเองพร้อมเหตุผล แล้วให้ AI ช่วยตรวจ |
| "ฉันทำนายว่า `bk.display()` จะพิมพ์ 2 บรรทัด เพราะ `Book` override `display()` และเรียก `super.display()` ก่อน การให้เหตุผลแบบนี้ถูกไหม" | ทำนายผลเองก่อน แล้วถามว่าเหตุผลถูกหรือไม่ |
| "ฉันเก็บ `area` เป็น attribute แทนการคำนวณในเมธอด `area()` ข้อดีข้อเสียของสองแบบนี้ต่างกันอย่างไรสำหรับงานของฉัน" | เปรียบเทียบทางเลือกที่ตัวเองตัดสินใจไปแล้ว |
| "นี่คือสิ่งที่ฉันสรุปใน PROCESS.md ขั้น 4 ว่า polymorphism คือ ... ฉันเข้าใจผิดตรงไหนบ้าง" | ให้ AI ตรวจความเข้าใจที่เขียนด้วยคำของตัวเอง |

### L2 ขอคำใบ้ / debug โค้ดตัวเอง (ดี)
| ตัวอย่างคำถาม | ทำไมจึงเป็น L2 |
|---|---|
| "โค้ดของฉันขึ้น error `cannot find symbol: variable height` ที่บรรทัด 12 ในคลาสลูก ควรเริ่มดูตรงไหน" | ถามจาก error ของโค้ดตัวเอง และขอแค่จุดที่ควรดู |
| "ฉันเรียก `super(name)` แล้วขึ้น `constructor Shape in class Shape cannot be applied to given types` เกิดจากอะไรได้บ้าง ไม่ต้องแก้ให้" | ขอสาเหตุที่เป็นไปได้ แล้วแก้เอง |
| "ผลลัพธ์ปริมาตรของฉันเป็น 0.0 ทั้งที่ใส่ค่าแล้ว ควรตรวจอะไรเป็นอันดับแรก" | อธิบายอาการที่เจอ และขอทิศทางการหา bug |
| "เมธอด `printInfo()` ในคลาสลูกของฉันไม่ถูกเรียก ทั้งที่ใส่ `@Override` แล้ว ขอคำใบ้ข้อเดียวพอ" | ขอคำใบ้ทีละข้อตามที่ tutor prompt กำหนด |

### L1 ถามแนวคิด (ใช้ได้)
| ตัวอย่างคำถาม | ทำไมจึงเป็น L1 |
|---|---|
| "abstract class ต่างจาก interface อย่างไร ใช้แบบไหนเมื่อไร" | ถามแนวคิดทั่วไป ไม่ได้ผูกกับคำตอบของโจทย์ |
| "`public static void main(String[] args)` แต่ละคำหมายถึงอะไร" | ถามความหมายของ syntax |
| "overloading กับ overriding ต่างกันอย่างไร ขอตัวอย่างที่ไม่เกี่ยวกับรูปทรงเรขาคณิต" | ขอตัวอย่างที่เป็นเรื่องอื่น ไม่ใช่โจทย์ของเรา |
| "ทำไมควรประกาศ attribute เป็น `private` แล้วมี getter แทนการเป็น `public`" | ถามเหตุผลของหลัก encapsulation |

### L0 ขอคำตอบ / ให้ทำให้ (ผิดข้อตกลง)
| ตัวอย่างคำถาม | ทำไมผิดข้อตกลง | ถามใหม่ให้ถูกข้อตกลง |
|---|---|---|
| "เขียนคลาส `RightTriangularPrism` ที่ extends `RightTriangle` พร้อม `volume()` ให้หน่อย" | ให้ AI เขียนโค้ดคำตอบ | (L3) "ฉันออกแบบ `RightTriangularPrism` ให้มี attribute `length` และเมธอด `volume()` ที่เรียก `area()` ของคลาสแม่ แบบนี้ถูกหลัก inheritance ไหม" |
| วางโจทย์ทั้งข้อ แล้วพิมพ์ "ทำข้อนี้ให้หน่อย" หรือ "ตอบข้อนี้" | ให้ AI ทำโจทย์แทน | (L1) ถามเฉพาะแนวคิดที่ยังไม่เข้าใจในโจทย์ เช่น "การส่งอ็อบเจกต์เป็นพารามิเตอร์ของเมธอดทำงานอย่างไร" |
| "ผลลัพธ์ของโปรแกรมนี้คืออะไร" แล้ววางโค้ดของโจทย์ | ให้ AI trace แทน ทั้งที่การทำนายผลคือสิ่งที่ต้องฝึก | (L3) "ฉันทำนายว่าผลลัพธ์คือ ... เพราะ ... เหตุผลข้อไหนที่ยังผิด" |
| "แก้โค้ดของฉันให้รันผ่านหน่อย" แล้ววางโค้ดทั้งไฟล์ | ให้ AI แก้แทน | (L2) "โค้ดของฉันขึ้น error ... ที่บรรทัด ... ควรเริ่มดูตรงไหน" |

**หลักจำง่าย:** ถ้าคำถามทำให้ AI ต้องเขียนโค้ด ออกแบบ หรือตอบแทนเรา = L0 ถ้าคำถามทำให้ **เรา** ต้องคิดต่อ = L1–L3

## วิธี export บทสนทนา
- **ChatGPT / Claude / Gemini:** คัดลอกบทสนทนาทั้งหมดวางในไฟล์ `ai-log/<เครื่องมือ>-<วันที่>.md` (เช่น `ai-log/chatgpt-2027-01-12.md`) หรือสั่งพิมพ์หน้าแชตเป็น PDF แล้ววางในโฟลเดอร์ `ai-log/`
- แชตละ 1 ไฟล์ ห้ามตัดหรือแก้ข้อความ
- ไม่ใช้ AI เลย: สร้างไฟล์ `ai-log/NONE.md` เขียนว่า "งานนี้ไม่ได้ใช้ AI"
