# w8-ci-cd
Lab w8 ci/cd

1. ส่วนใดของงานนี้คือ Continuous Integration?
การที่ GitHub Actions รัน npm ci และ npm test อัตโนมัติทุกครั้งที่มีการ push หรือ Pull Request เข้า main คือ Continuous Integration เพราะช่วยตรวจสอบว่าโค้ดที่เปลี่ยนแปลงยังทำงานร่วมกับระบบเดิมได้
2. งานนี้มี Continuous Delivery หรือ Continuous Deployment แล้วหรือยัง? เพราะเหตุใด?
ยังไม่มี เพราะ workflow ตอนนี้ทำเพียงติดตั้ง dependencies และทดสอบโค้ด ยังไม่มีขั้นตอนนำ application ไป deploy หรือส่งต่อไปยัง staging/production
3. Green pipeline ยืนยันอะไรได้บ้าง และยืนยันอะไรไม่ได้?
Green pipeline ยืนยันได้ว่า ขั้นตอนและ automated tests ที่กำหนดไว้ผ่านทั้งหมด แต่ไม่ได้ยืนยันว่า application จะไม่มี bug หรือใช้งานจริงใน production ได้สมบูรณ์
4. เหตุใดเราจึงต้องทดลองสร้าง red pipeline?
เพื่อให้เข้าใจว่า CI สามารถตรวจพบความผิดพลาดได้จริง และฝึกอ่าน error log เพื่อหาสาเหตุและแก้ไขจน pipeline กลับมาเป็น green
5. หาก test ผ่านแต่ application ใช้งานจริงไม่ได้ ควรเพิ่ม test หรือ pipeline stage ใด?
ควรเพิ่ม Integration Test หรือ End-to-End (E2E) Test เพื่อทดสอบการทำงานร่วมกันของระบบและจำลองการใช้งานจริง รวมถึงอาจเพิ่มขั้นตอน deploy ไปยัง staging ก่อนนำขึ้น production

## Self-study Extension: Add Test Coverage

เพิ่ม automated test อีก 2 กรณี ได้แก่ empty string และชื่อภาษาไทย

- Empty string test ช่วยตรวจสอบพฤติกรรมของระบบเมื่อผู้ใช้ส่งชื่อว่าง
- Thai name test ช่วยตรวจสอบว่าฟังก์ชันรองรับ Unicode และชื่อภาษาไทยได้ถูกต้อง

หลังเพิ่ม test ระบบมีทั้งหมด 4 tests และทั้งหมดผ่านบน local และ GitHub Actions
