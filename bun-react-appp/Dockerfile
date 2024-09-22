# ใช้ Node.js base image
FROM node:18

# ตั้งค่า working directory
WORKDIR /app

# คัดลอก package.json และไฟล์ที่จำเป็นลงใน container
COPY package*.json ./

# ติดตั้ง dependencies
RUN npm install

# คัดลอกโค้ดโปรเจกต์ทั้งหมดลงใน container
COPY . .

# Build แอปพลิเคชัน
RUN npm run build

# เปิดพอร์ต 3000 สำหรับการเข้าถึงแอป
EXPOSE 3000

# รันแอปด้วยคำสั่งนี้
CMD ["npm", "run", "preview"]
