![Header](./Assets/Banner.jpg)

# แนวทางการเขียนโปรแกรมที่มีความปลอดภัย

การเขียนโปรแกรมให้ทำงานได้ดี ครอบคลุมหลาย Function ทำงานตามเป้าหมายหรือความต้องการของลูกค้า หรือมีการจัดการ Responsive ที่รัดกุมถือว่าเป็นเรื่องดี แต่ถ้าจะดียิ่งกว่านี้ถ้ามีความปลอดภัยเข้ามาด้วย ซึ่งใน Repository นี้ของผมจะรวบรวมปัญหาและช่องโหว่เกี่ยวกับความปลอดภัยในการพัฒนาแอปพลิเคชั่น โดยจะอ้างอิงจากหลายๆ แหล่ง Open Source ได้แก่
- [10 อันดับช่องโหว่แอปพลิเคชันโดย OWASP (OWASP Top 10)](https://owasp.org/www-project-top-ten/)
- [คู่มือการทดสอบเว็ปแอปพลิเคชั่นโดย OWASP](https://owasp.org/www-project-web-security-testing-guide/v42/)
- [จุดอ่อนที่มักพบในซอฟต์แวร์และฮาร์ดแวร์ (CWE)](https://cwe.mitre.org/)
- [MITRE ATTACK - Framework สำหรับจัดการภัยคุกคาม](https://attack.mitre.org/)
- และอื่นๆ (เดี๋ยวมาเพิ่มเติมทีหลัง)

คำว่า "ช่องโหว่" ไม่ได้จำกัดถึงช่องโหว่ที่ร้ายแรง เช่น Bypass การเข้าสู่ระบบ รันคำสั่งจากทางไกล หรือขโมยบัญชีผู้อื่นๆ ช่องโหว่จะต้องรวมไปถึงส่วนที่ช่วยเพิ่มโอกาสหรืออำนวยความสะดวกให้ผู้ไม่หวังดีมีโอกาสโจมตีสำเร็จมากขึ้นด้วย เช่น การที่แอปพลิเคชั่นอณุญาตให้ตั้งรหัสผ่านสั้นๆ ก้ได้ก็เสี่ยงต่อการถูกคาดเดารหัสได้ นี่ก็ถือว่าเป็นช่องโหว่เช่นกัน

# ทำไมต้องสนใจความปลอดภัยของ Application

- คุณอาจถูกฟ้องจากลูกค้าหรือรัฐบาลได้หากข้อมูลส่วนบุคคลรั่วไหลจากช่องโหว่ของโปรแกรมคุณ
- คุณอาจสูญเสียทั้ง Infrastructure หรือ Server ได้เพียงแค่มีช่องโหว่มาจากเว็ปๆ เดียว
- ค่าใช้จ่ายในการแก้ไขช่องโหว่ย่อมสูงกว่าค่าใช้จ่ายตอนพัฒนาซอฟต์แวร์ให้ปลอดภัยเสียอีก
- ยิ่งไปกว่านั้นค่าใช้จ่ายในการจัดการข้อมูลรั่วไหลไม่ว่าจะเป็นค่าปรับ ค่าจ้างที่ปรึกษา ค่าทดสอบ และอื่นๆ อีกมากมายก็ย่อมสูงกว่าค่าใช้จ่ายในการพัฒนาซอฟต์แวร์ให้ปลอดภัยอีกเช่นกัน

ดังนั้นแล้วคุณอยากเอาเงินทั้งหมดทุ่มไปกับการพัฒนาซอฟต์แวร์ที่ดีและปลอดภัย หรือทุ่มไปกับค่าใช้จ่ายในการจัดการความเสียหายที่เกิดจากการถูกโจมตีละ

# สารบัญ

ผมได้ทำการแยกเป็น 12 หัวข้อหลักๆ อ้างอิงตามคู่มือการทดสอบเว็บแอปพลิเคชั่นของ OWASP

1. [การเก็บข้อมูลเบื้องต้นและการเรียนรู้เป้าหมายในการโจมตี](./1%20-%20Information%20Gathering/README.md)
2. [ช่องโหว่ตอน Configuration และ Deployment](./2%20-%20Deployment%20Management/README.md)
3. [ช่องโหว่เกี่ยวกับการจัดการตัวตนผู้ใช้งาน](./3%20-%20Identity%20Management/README.md)
4. [ช่องโหว่เกี่ยวกับระบบ Login หรือการยืนยันตัวตน](./4%20-%20Authentication/README.md)
5. [ช่องโหว่เกียวกับการจัดการสิทธิ์](./5%20-%20Authorization/README.md)
6. [ช่องโหว่เกี่ยวกับการจัดการ Session](./6%20-%20Session%20Management/README.md)
7. [ช่องโหว่เกี่ยวกับความถูกต้องของการส่งข้อมูล](./7%20-%20Input%20Validation/README.md)
8. [ช่องโหว่เกี่ยวกับการจัดการ Error](./8%20-%20Error%20Handling/)
9. [ช่องโหว่เกี่ยวกับการเข้ารหัสและ Hash](./9%20-%20Cryptography/README.md)
10. [ช่องโหว่เกี่ยวกับ Work Flow และการดำเนินงานของโปรแกรม](./10%20-%20Business%20Logic/README.md)
11. [ช่องโหว่เกี่ยวกับ Browser ของผู้ใช้งาน](./11%20-%20Client-Side/README.md)
12. [ช่องโหว่เกี่ยวกับ API และ Library](./12%20-%20API/README.md)