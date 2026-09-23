# Rove Beta Downloads

ที่เก็บ **private** นี้ใช้สำหรับไฟล์ติดตั้งและไฟล์อัปเดตของ Rove ช่วงทดสอบเท่านั้น ไม่มี source code ของแอป

## ดาวน์โหลดรุ่นทดสอบ

1. เข้า [Releases](https://github.com/ApisornL/Rove-Beta-Downloads/releases) ด้วยบัญชี GitHub ที่ได้รับสิทธิ์
2. เลือก prerelease สำหรับระบบปฏิบัติการของคุณ แล้วดาวน์โหลดไฟล์ติดตั้งจาก **Assets**
3. ตรวจ SHA-256 จาก release notes ก่อนติดตั้ง

ไฟล์ Windows เป็น NSIS installer (`.exe`) และไฟล์ macOS สำหรับ Apple Silicon เป็น DMG (`.dmg`). รุ่นทดสอบ macOS ยังไม่ได้ notarize กับ Apple; เมื่อเปิดครั้งแรกให้ใช้ **System Settings → Privacy & Security → Open Anyway** หาก macOS แจ้งเตือน

## สิทธิ์เข้าถึง

สิทธิ์ใน repo นี้ไม่ให้สิทธิ์เข้าถึง repo source code ของ Rove. อย่าเพิ่ม source code, build logs, credentials หรือ token ลงใน repo หรือ release. ไม่ควรส่ง token ให้ผู้อื่น และไม่ควรใส่ token ใน URL, issue หรือ screenshot.

**ข้อจำกัดของ GitHub:** Repo นี้อยู่ใต้บัญชีส่วนตัว จึงให้สิทธิ์ collaborator แบบอ่านอย่างเดียวไม่ได้; ผู้ที่ถูกเชิญจะมีสิทธิ์เขียนใน repo นี้ด้วย. ก่อนเชิญผู้ทดสอบจริง ควรย้าย repo ดาวน์โหลดไปอยู่ใต้ GitHub Organization และให้ผู้ทดสอบสิทธิ์ **Read**. ระหว่างนี้เจ้าของ repo สามารถส่ง installer ให้ผู้ทดสอบเป็นการส่วนตัวได้.

เมื่อ repo อยู่ใต้ Organization และให้สิทธิ์ Read แล้ว ผู้ทดสอบที่ใช้ Auto Update ควรสร้าง fine-grained personal access token ของตนเอง โดยเลือกเฉพาะ repo ดาวน์โหลดนี้และให้สิทธิ์ **Contents: Read** พร้อมวันหมดอายุสั้น ๆ. เก็บ token ไว้ในเครื่องของผู้ทดสอบเท่านั้น. [GitHub ระบุสิทธิ์ของ repo ส่วนตัว](https://docs.github.com/en/repositories/managing-your-repositorys-settings-and-features/repository-access-and-collaboration/permission-levels-for-a-personal-account-repository) และ [สิทธิ์อ่าน release asset ผ่าน API](https://docs.github.com/en/rest/releases/assets#get-a-release-asset).

Auto Update ช่วง beta จะเริ่มใช้ได้เมื่อแอปมีการลงลายเซ็น updater, มี release metadata ครบ และทดสอบการอัปเดตข้ามเวอร์ชันจริงแล้ว. การมีไฟล์ติดตั้งใน Releases อย่างเดียวไม่ได้ทำให้ Auto Update ทำงาน.
