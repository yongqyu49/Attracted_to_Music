# 🎵 Attracted_to_Music (AMU)

[![GitHub](https://img.shields.io/badge/GitHub-Repository-blue)](https://github.com/yongqyu49/Attracted_to_Music)

## 📋 프로젝트 소개

**Attracted_to_Music (AMU)** 는 사용자들이 음악을 업로드하고, 스트리밍하며, 공유할 수 있는 풀스택 음악 플랫폼입니다. 

이 프로젝트는 프론트엔드와 백엔드를 Git 서브모듈로 분리하여 관리합니다.

## 🏗️ 프로젝트 구조

```
Attracted_to_Music/
├── front/    # React 기반 프론트엔드 (서브모듈)
├── back/     # Spring Boot 기반 백엔드 (서브모듈)
└── README.md
```

### 서브모듈

- **Frontend**: [AMU_Front](https://github.com/yongqyu49/AMU_Front.git)
- **Backend**: [AMU_Back](https://github.com/yongqyu49/AMU_Back.git)

## ✨ 주요 기능

### 🔐 사용자 관리
- 회원가입 / 로그인 / 로그아웃
- 프로필 관리 및 이미지 업로드
- 사용자별 음악, 좋아요, 리뷰, 플레이리스트 조회

### 🎵 음악 기능
- 음악 파일 업로드 (MP3 + 커버 이미지)
- 음악 스트리밍 및 재생 제어
- 가사 표시
- 검색 및 필터링 (장르별, 정렬)
- 조회수 관리
- 미니 플레이어

### 📝 소셜 기능
- 음악 리뷰 및 댓글 작성
- 좋아요 시스템
- 사용자 프로필 조회

### 📂 플레이리스트
- 플레이리스트 생성 및 관리
- 음악 추가/제거
- 플레이리스트 재생

## 🛠️ 기술 스택

### Frontend
- **React** 18.3.1
- **React Router** 6.28.0
- **React Bootstrap** 2.10.5
- **Styled Components** 6.1.13
- **Axios** 1.7.7
- **use-sound** 4.0.3

### Backend
- **Spring Boot** 3.3.5
- **Java** 17
- **MySQL** (Database)
- **MyBatis** 3.0.1
- **Spring Security**
- **Gradle** (Build Tool)

## 🚀 시작하기

### 필수 요구사항

- **Node.js** 14.x 이상
- **Java** 17 이상
- **MySQL** 데이터베이스
- **Git**

### 1. 저장소 클론 (서브모듈 포함)

```bash
# 메인 저장소 클론
git clone --recursive https://github.com/yongqyu49/Attracted_to_Music.git
cd Attracted_to_Music

# 또는 이미 클론한 경우 서브모듈 초기화
git submodule init
git submodule update
```

### 2. 데이터베이스 설정

MySQL에 데이터베이스를 생성합니다:

```sql
CREATE DATABASE amu;
CREATE USER 'amu'@'localhost' IDENTIFIED BY 'amu';
GRANT ALL PRIVILEGES ON amu.* TO 'amu'@'localhost';
FLUSH PRIVILEGES;
```

### 3. 백엔드 설정 및 실행

```bash
cd back

# 파일 저장 경로 설정 (application.yml 수정)
# - spring.file.upload-dir: 프로필 이미지 저장 경로
# - spring.web.resources.static-locations: 정적 리소스 경로

# 빌드 및 실행
./gradlew build
./gradlew bootRun

# 또는 JAR 파일로 실행
java -jar build/libs/amu_back-0.0.1-SNAPSHOT.jar
```

백엔드 서버는 `http://localhost:8787`에서 실행됩니다.

### 4. 프론트엔드 설정 및 실행

```bash
cd ../front

# 의존성 설치
npm install

# 개발 서버 실행
npm start
```

프론트엔드는 `http://localhost:3000`에서 실행됩니다.

## 📡 API 문서

### 주요 API 엔드포인트

#### User API (`/user`)
- `POST /user/signUp` - 회원가입
- `POST /user/signIn` - 로그인
- `POST /user/signOut` - 로그아웃
- `GET /user/current` - 현재 사용자 정보
- `POST /user/updateProfile` - 프로필 업데이트

#### Music API (`/music`)
- `POST /music/upload` - 음악 업로드
- `GET /music/sort/{sortType}` - 정렬된 음악 목록
- `GET /music/genre/{genreCode}` - 장르별 음악 목록
- `GET /music/play/{filename}` - 음악 스트리밍
- `GET /music/search` - 음악 검색
- `POST /music/like` - 좋아요 추가
- `POST /music/review/upload` - 리뷰 작성

#### Playlist API (`/playlist`)
- `GET /playlist/getPlaylist` - 플레이리스트 조회
- `POST /playlist/addMusic` - 플레이리스트에 음악 추가
- `GET /playlist/play/{filename}` - 플레이리스트 음악 재생

자세한 API 문서는 [백엔드 README](https://github.com/yongqyu49/AMU_Back)를 참조하세요.

## 🌐 주요 페이지

- `/` - 메인 콘텐츠 페이지
- `/signIn` - 로그인
- `/signUp` - 회원가입
- `/mainPage` - 메인 페이지
- `/upload` - 음악 업로드
- `/feed` - 플레이어 피드
- `/profile/:id` - 사용자 프로필
- `/music/:musicCode` - 음악 상세 정보

## ⚙️ 설정

### 백엔드 설정
- **포트**: 8787
- **세션 타임아웃**: 30분
- **최대 파일 크기**: 10MB

### 프론트엔드 설정
- **포트**: 3000
- **프록시**: http://localhost:8787

## 🔒 보안

- Spring Security를 통한 인증/인가
- 세션 기반 인증
- 비밀번호 암호화 (PasswordEncoder)

## 📦 빌드 및 배포

### 프론트엔드 프로덕션 빌드

```bash
cd front
npm run build
```

빌드된 파일은 `front/build` 디렉토리에 생성됩니다.

### 백엔드 프로덕션 빌드

```bash
cd back
./gradlew build
```

빌드된 JAR 파일은 `back/build/libs/` 디렉토리에 생성됩니다.

## 🤝 기여하기

1. Fork the Project
2. Create your Feature Branch (`git checkout -b feature/AmazingFeature`)
3. Commit your Changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the Branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## 📝 서브모듈 업데이트

서브모듈을 최신 상태로 업데이트하려면:

```bash
# 모든 서브모듈 업데이트
git submodule update --remote

# 특정 서브모듈 업데이트
git submodule update --remote front
git submodule update --remote back
```

## 📧 연락처

프로젝트 링크: [https://github.com/yongqyu49/Attracted_to_Music](https://github.com/yongqyu49/Attracted_to_Music)

- Frontend: [https://github.com/yongqyu49/AMU_Front](https://github.com/yongqyu49/AMU_Front)
- Backend: [https://github.com/yongqyu49/AMU_Back](https://github.com/yongqyu49/AMU_Back)

## 📝 라이선스

이 프로젝트는 개인 프로젝트입니다.

---

Made with ❤️ by yongqyu49