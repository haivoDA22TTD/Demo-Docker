# Bước 1: Chọn image node.js 22 làm base image
FROM node:22 AS build

# Bước 2: Cài đặt thư mục làm việc bên trong container
WORKDIR /app

# Bước 3: Copy package.json và package-lock.json vào container
COPY package*.json ./

# Bước 4: Cài đặt các dependencies
RUN npm install

# Bước 5: Copy toàn bộ mã nguồn của ứng dụng vào container
COPY . .

# Bước 6: Build ứng dụng React (sản phẩm tĩnh)
RUN npm run build

#  Serve with Nginx
FROM nginx:alpine

# Sao chép các file build từ giai đoạn trước vào thư mục của Nginx
COPY --from=build /app/dist /usr/share/nginx/html

# Bước 8: Expose cổng mà ứng dụng sẽ chạy
EXPOSE 80


