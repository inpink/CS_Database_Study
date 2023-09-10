## 2.1 MySQL 서버 설치
- 권장: 리눅스의 RPM or 운영체제의 인스톨러 이용

### 2.1.1 버전과 에디션 선택
- MySQL 8.0 사용하는 경우 8.0.15 ~ 8.0.20 사이 버전 권장 
- 에디션
    - 커뮤니티 에디션
        - 무료버전
        - Percona에서 출시하는 Percona Server 백업 및 모니터링 도구 또는 Percona Server에서 지원하는 플러그인을 활용하면 굳이 엔터프라이즈 에디션 사용하지 않아도 됨
    - 엔터프라이즈 에디션
        - 이제 소스코드 공개하지 않음
        - 커뮤니티 버전과 핵심 내용은 동일하나, 상용 버전 부가 기능들이 포함되어 있음
            - Thread Pool
            - Enterprise Audit
            - Enterprise TDE(Master Key 관리)
            - Enterprise Authenticatino
            - Enterprise Firewall
            - Enterprise Monitor
            - Enterprise Backup
            - MySQL 기술 지원
### 2.1.2 MySQL 설치
- 리눅스 서버의 Yum 인스톨러 설치
- 리눅스 서버에서 Yum 인스톨러 없이 RPM 파일로 설치
- macOS용 DMG 패키지 설치
- 윈도우 MSI 인스톨러 설치

## 2.2 MySQl서버의 시작과 종료

### 2.2.1 설정 파일 및 데이터 파일 준비
### 2.2.2 시작과 종료
### 2.2.3 서버 연결 테스트

## 2.3 MySQL 서버 업그레이드
### 2.3.1 인플레이스 업그레이드 제약 사항
### 2.3.2 MySQL 8.0 업그레이드 시 고려 사항
### 2.3.3. MySQL 8.0 업그레이드
## 2.4 서버 설정
### 2.4.1 설정 파일의 구성
### 2.4.2 MySQL 시스템 변수의 특징
### 2.4.3 글로벌 변수와 세션 변수
### 2.4.4 정적 변수와 동적 변수
### 2.4.5 SET PERSIST
### 2.4.6 my.cnf 파일
