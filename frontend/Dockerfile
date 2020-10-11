#운영을 위한 Dockerfile
# Nginx가 제공을 해줄 build 파일들을 생성하는 단계
FROM node:alpine as builder
WORKDIR /app
COPY ./package.json ./
RUN npm install
COPY . .
RUN npm run build

# Nginx를 가동하고 윗 단계에서 생성된 빌드 그리고 default.conf 에서 해준 설정을 nginx ~게 복사를 해준다. 
FROM nginx
EXPOSE 3000
COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf
COPY --from=builder /app/build /usr/share/nginx/html