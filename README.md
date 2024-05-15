# วิธีตั้งค่าและใช้งาน SSH ด้วย Public Key Authentication
## ทำการสร้างไฟล์ SSH Key ด้วย ssh-keygen
```
ssh-keygen
```

ระบบจะแสดงข้อความสอบถามว่า `Enter file in which to save the key (/Users/[Your Username]/.ssh/id_ed25519): ` หากต้องเปลี่ยน Path ให้พิมพ์ Fullpath ลงไปเช่น
`
/Users/[Your Username]/certificate/[ชื่อ Key]
`
ตัวอย่างเช่น `/Users/johne/certificate/key-hosts`
จากนั้นกดปุ่ม Enter ไปสองสามรอบ เราก็จะได้ Private Key และ Public Key มาแล้ว


## วิธีนำมาใช้
ให้ทำการ copy public key ของเราบนเครื่องสร้างไว้ไปยัง server ปลายทางด้วยคำสั่ง `ssh-copy-id` ตามตัวอย่างต่อไปนี้
```
ssh-copy-id -i [Public key path] [user ssh]@[ssh host]
```
ตัวอย่างเช่น ssh-copy-id -i /Users/johne/certificate/key-hosts.pub userssh@99.99.99.99

จากนั้นทำการใส่ Password เพื่อบันทึก Key ของเราลงเครื่องปลายทาง และสามารถ SSH ไปยังเครื่องปลายทางได้เลยตามตัวอย่างนี้

```
ssh -i [Pivate key path] [user ssh]@[ssh host]
```
ตัวอย่างเช่น ssh -i /Users/johne/certificate/key-hosts userssh@99.99.99.99

จากนั้นก็แนะนำให้ตั้งค่า SSH Server ให้สามารถเข้าผ่าน Key ได้อย่างเดียวเพื่อความปลอดภัย
