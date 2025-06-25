# POS Eureka Server

본 프로젝트는 POS 시스템의 마이크로서비스 간 서비스 디스커버리를 위한 [Spring Cloud Netflix Eureka](https://cloud.spring.io/spring-cloud-netflix/) 기반의 Eureka Server입니다.

---

## 📦 프로젝트 구조

```
pos-eureka-server/
├── src/
├── build.gradle
├── settings.gradle
├── application.yml
├── Dockerfile
└── README.md
```

---

## 🚀 실행 방법

### 1. 로컬 실행 (Java 17 이상 필요)

```bash
./gradlew bootRun
```

혹은 jar 빌드 후 실행:

```bash
./gradlew bootJar
java -jar build/libs/pos-eureka-server-0.0.1-SNAPSHOT.jar
```

### 2. Docker 실행

```bash
docker build -t pos-eureka-server .
docker run -d -p 8761:8761 --name pos-eureka-server pos-eureka-server
```

> `http://localhost:8761`에서 Eureka 대시보드를 확인할 수 있습니다.

---

## ⚙️ application.yml 설정 예시

```yaml
server:
  port: 8761

spring:
  application:
    name: pos-eureka-server

eureka:
  client:
    register-with-eureka: false
    fetch-registry: false
```

---

## 🧱 Dockerfile 예시

```dockerfile
FROM eclipse-temurin:17-jre

WORKDIR /app
COPY build/libs/*.jar app.jar

EXPOSE 8761

ENTRYPOINT ["java", "-jar", "app.jar"]
```

---

## ✅ 연동된 마이크로서비스 예시

- pos-api-gateway
- pos-order-service
- pos-inventory-service

---

## 📄 라이선스

본 프로젝트는 MIT 라이선스를 따릅니다.
