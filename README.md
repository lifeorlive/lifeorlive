实验1 Part 2 : Containerize an application

Dockerfile文件内容：

# syntax=docker/dockerfile:1
FROM node:12-alpine 
RUN sed -i 's/dl-cdn.alpinelinux.org/mirrors.ustc.edu.cn/g' /etc/apk/repositories
RUN apk add --no-cache python2 g++ make
WORKDIR /app
COPY . .
RUN yarn install --production
CMD ["node", "src/index.js"]
EXPOSE 3000
docker run -dp 3000:3000 getting-started
docker ps
 http://192.168.126.130:3000
