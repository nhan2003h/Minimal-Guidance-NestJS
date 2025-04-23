# Minimal-Guidance-NestJS

## I. Cài đặt môi trường ban đầu
> Các bạn cần cài đặt Node.js và NestJS CLI trước buổi học.

1. **Cài đặt Node.js (>= 16.x)**
   - Tải tại: [https://nodejs.org](https://nodejs.org)

2. **Cài NestJS CLI**
   ```bash
   npm install -g @nestjs/cli
   ```

3. **Tạo project NestJS mới**
   ```bash
   nest new my-nestjs-app
   cd my-nestjs-app
   ```

---

## II. Cài Prisma & Kết nối PostgreSQL
> 💡 Sử dụng Neon để tạo một database PostgreSQL miễn phí.

1. **Cài Prisma**
   ```bash
   npm install @prisma/client @nestjs/config
   npm install --save-dev prisma
   npx prisma init
   ```

2. **Chỉnh sửa file `.env` với DATABASE_URL**
   ```env
   DATABASE_URL="postgresql://username:password@hostname:5432/dbname?schema=public"
   ```

3. **Tạo schema ban đầu**
   ```bash
   npx prisma migrate dev --name init
   ```

---

## III. Cấu trúc sơ bộ trong NestJS
> Ghi nhớ 3 tầng chính: `Module`, `Controller`, `Service`.

- **Module**: Gom nhóm các thành phần liên quan (`@Module()`).
- **Controller**: Xử lý request và route (`@Controller()`).
- **Service**: Chứa logic nghiệp vụ (`@Injectable()`).

---

## IV. Tài liệu API với Swagger

1. **Cài Swagger**
   ```bash
   npm install @nestjs/swagger swagger-ui-express
   ```

2. **Thêm Swagger config vào `main.ts`**
   ```ts
   import { SwaggerModule, DocumentBuilder } from '@nestjs/swagger';

   const config = new DocumentBuilder()
     .setTitle('API Docs')
     .setDescription('Generated with Swagger')
     .setVersion('1.0')
     .build();

   const document = SwaggerModule.createDocument(app, config);
   SwaggerModule.setup('api', app, document);
   ```

---

## V. Deploy nhanh trên Render

1. **Tạo repo Git và push lên GitHub**

2. **Trên Render**
   - Build command:
     ```bash
     npm install && npx prisma generate
     ```
   - Start command:
     ```bash
     npm run start
     ```
   - Thêm biến môi trường:
     - Key: `DATABASE_URL`
     - Value: chuỗi kết nối từ Neon

---

## Ghi chú:
- Các bạn chuẩn bị sẵn một database trên [https://neon.tech](https://neon.tech).
- Sau khi hoàn tất cài đặt, chạy thử app:
   ```bash
   npm run start
   ```
- Truy cập tài liệu API tại:
  ```
  http://localhost:3000/api
  ```
