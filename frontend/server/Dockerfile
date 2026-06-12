# Node.js 22 Alpine 이미지
FROM node:22-alpine

# 작업 디렉토리 생성
WORKDIR /app

# package.json 복사
COPY package*.json ./

# 의존성 설치
RUN npm install

# 소스 복사
COPY . .

# 애플리케이션 포트
EXPOSE 3001

# 서버 실행
CMD ["npm", "start"]