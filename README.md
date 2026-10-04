# Rove Beta Downloads

ที่เก็บสาธารณะสำหรับไฟล์ติดตั้งและไฟล์อัปเดตของ Rove ช่วงทดสอบ ไม่มี source code ของแอป

## ดาวน์โหลด

เปิด [Releases](https://github.com/ApisornL/Rove-Beta-Downloads/releases) แล้วเลือกไฟล์สำหรับระบบปฏิบัติการของคุณ ไม่ต้องมีบัญชี GitHub หรือ token

| ระบบ | ไฟล์ติดตั้ง |
| --- | --- |
| Windows x64 | `Rove_<version>_x64-setup.exe` |
| macOS Apple Silicon | `Rove_<version>_aarch64.dmg` |

ตรวจ SHA-256 ตาม release notes ก่อนติดตั้ง รุ่นทดสอบ macOS ปัจจุบันยังไม่ได้ notarize กับ Apple และ Windows ยังไม่มี Authenticode signing; ระบบปฏิบัติการอาจแจ้งเตือนเมื่อเปิดครั้งแรก

## สถานะ Auto Update

ไฟล์ล่าสุดที่เผยแพร่ขณะเตรียม feed นี้คือ **0.1.2** ซึ่งยังใช้ updater แบบเก่า ระบบเช็คอัปเดตทุกครั้งที่เปิดโดยไม่ต้องตั้งค่าอยู่ในโค้ดรุ่น **0.1.3** และยังไม่ได้เผยแพร่ installer ของรุ่นนั้น

เมื่อเผยแพร่รุ่นที่มี updater ใหม่แล้ว แอปจะอ่าน [signed beta policy](https://raw.githubusercontent.com/ApisornL/Rove-Beta-Downloads/main/updates/beta.json) และดาวน์โหลดจาก Releases โดยไม่ใช้ GitHub token:

- รุ่นที่ยังรองรับสามารถเลือกอัปเดตตอนนี้หรือภายหลัง
- รุ่นต่ำกว่า minimum supported version ต้องอัปเดตก่อนใช้งาน
- แอปตรวจลายเซ็นของ policy และไฟล์อัปเดตด้วย public key ที่ฝังไว้ในแอป
- หากเช็คไม่ได้และยังไม่เคยได้รับ policy ที่บังคับอัปเดต แอปเปิดใช้งานได้หลัง timeout; policy บังคับที่เคยตรวจสอบและบันทึกไว้ยังมีผลขณะออฟไลน์

ผู้ใช้ที่ติดตั้ง 0.1.0 หรือ 0.1.1/0.1.2 โดยไม่มี token ต้องติดตั้งรุ่น migration ด้วย installer หนึ่งครั้งเมื่อรุ่นนั้นพร้อม รุ่นเก่าไม่เริ่มตรวจอัปเดตเองเพียงเพราะ server เปลี่ยน feed

`latest.json` คงรูปแบบเดิมไว้สำหรับ updater เก่า ส่วน `updates/beta.json` เป็น feed ที่มี signed policy สำหรับ updater ใหม่ การเตรียม feed ด้วยไฟล์ 0.1.2 ไม่ได้เปลี่ยนพฤติกรรมของ installer เก่า

## ข้อมูลใน repository

Repository นี้มีเฉพาะเอกสารดาวน์โหลด, update manifests, installers, updater bundles และ signatures เท่านั้น ห้ามเพิ่ม source code, workspace ของผู้ใช้, credentials, token หรือ private signing key ลงใน repository หรือ Releases

Updater signatures ใช้ตรวจความถูกต้องของไฟล์ เป็นคนละส่วนกับการรับรอง installer โดย Windows หรือ macOS
