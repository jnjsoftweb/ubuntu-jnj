# ubuntu-jnj - 메타데이터 기반 개발 플랫폼

이 플랫폼은 메타데이터를 기반으로 하는 풀스택 개발 환경을 제공합니다.

## 🏗️ 아키텍처

```
workspace/
├── docker/                    # Docker 설정
├── infrastructure/            # 공유 인프라 서비스
├── management-hub/           # 통합 관리 허브
├── projects/                 # 개별 프로젝트들
├── shared/                   # 공통 리소스
├── guidelines/               # 개발 가이드라인
├── environments/             # 환경별 설정
└── scripts/                  # 자동화 스크립트
```

## 🚀 시작하기

### 1. 환경 설정
```bash
# 환경변수 파일 생성
cp .env.sample .env

# 환경변수 수정
vim .env
```

### 2. 인프라 서비스 시작
```bash
# 전체 인프라 시작
docker-compose -f docker/docker-compose.yml up -d

# 개발 환경으로 시작
docker-compose -f docker/docker-compose.yml -f docker/docker-compose.dev.yml up -d
```

### 3. 새 프로젝트 생성
```bash
cd projects
./cp.sh <project-name>
```

## 📋 주요 구성 요소

### Infrastructure Services
- **Auth Service** (Port 3001): JWT 기반 통합 인증
- **Database Service** (Port 3002): 프로젝트별 DB 자동 생성
- **API Gateway** (Port 3000): 통합 API 게이트웨이
- **Redis Cache** (Port 6379): 세션 관리 및 캐싱

### Management Hub
- **Frontend**: 통합 관리 대시보드
- **Backend**: 관리 허브 백엔드 서비스

### Development Tools
- **Meta Editor**: 웹 기반 메타데이터 편집기
- **Code Generator**: 자동 코드 생성 엔진
- **Multi-Environment**: 개발/스테이징/프로덕션 환경

## 🔧 개발 워크플로우

1. **프로젝트 초기화**: `./cp.sh <project-name>`
2. **메타데이터 정의**: 웹 기반 편집기에서 테이블/컬럼 정의
3. **코드 자동 생성**: Watch Mode 또는 수동 트리거
4. **개발 및 테스트**: Hot Reload 환경에서 개발
5. **배포**: 자동화된 배포 파이프라인

## 📖 문서

- [아키텍처 문서](docs/99.summary.md)
- [메타데이터 관리](docs/40.%20Meta%20데이터관리.md)
- [Docker 설정](docs/10.%20docker.md)
- [공유 서비스](docs/50.%20shared.md)
- [Redis 활용](docs/70.%20redis.md)

## 🛠️ 기술 스택

- **Backend**: Node.js + TypeScript + GraphQL
- **Frontend**: Next.js + React
- **Database**: PostgreSQL (메타데이터), 프로젝트별 DB
- **Infrastructure**: Docker + Redis + Nginx
- **Monitoring**: Prometheus + Grafana

## 📈 기대 효과

- **80% 이상의 보일러플레이트 코드 자동 생성**
- **즉시 프로토타이핑 가능**
- **일관된 코드 품질 보장**
- **중앙집중식 사용자/권한 관리**
- **프로젝트별 독립적 환경**