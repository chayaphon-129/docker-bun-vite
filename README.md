How to use
1. sudo apt update
2. sudo apt install docker.io

sudo apt install npm

3. sudo docker pull chayasu/bun-react:latest
 
4. sudo docker run -d --name bun-react-app -p 5173:5173 chayasu/bun-react:latest
   
6. sudo docker exec -it bun-react-app /bin/bash
   
7. npm run dev


วิธีการนำโปรเจคขึ้น Docker

1. install docker.io
   
2. สร้าง Dockerfile ดังต่อไปนี้

```
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

```

3. แก้ไขไฟล์ tsconfig.json ดังนี้

```
{
  "compilerOptions": {
    "jsx": "react-jsx", 
    "moduleResolution": "node",
    "target": "esnext",
    "module": "esnext",
    "strict": true,
    "esModuleInterop": true,
    "skipLibCheck": true,
    "forceConsistentCasingInFileNames": true,
    "noEmit": true
  },
  "include": ["src"],
  "exclude": ["node_modules"]
}
```

4. สร้าง Repositorie ใน DockerHub แล้ว docker build -t chayasu/bun-react:latest .
5. docker push chayasu/bun-react:latest
