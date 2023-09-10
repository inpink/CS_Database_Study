# MySQL 소개

- 전세계 DBMS서버 사용 순위 1~2위　   
- RDBMS (Relational DataBase Management System, 관계형 데이터베이스 관리 시스템, 테이블/행/열을 사용하는 RDB를 위한 서버)

- 'MySQL 엔터프라이즈 에디션'과 'MySQL 커뮤니티 에디션' 두 가지 버전이 있음
- 'MySQL 엔터프라이즈 에디션'은 유료이다. 커뮤니티 에디션에 없는 기능들을 지원한다.
- 'MySQL 커뮤니티 에디션'은 오픈소스이자 무료이다. 이 책에선 이를 사용한다.
  
- MySQL은 '오픈 코어 모델(Open Core Model)'이다.  무료 버전의 핵심 내용도 엔터프라이즈 에디션과 동일하고, 특정 부가 기능만 유료 버전에 포함된다는 뜻이다.
- Percona의 플러그인 등을 활용하면, 커뮤니티 에디션의 부족한 부분을 메꿀 수도 있다. 
즉, 많은 작은 및 중소규모 프로젝트에서는 오픈 소스 MySQL 버전만으로 충분할 수 있다.
엔터프라이즈 에디션에서 지원하는 내용을 살펴보고, 프로젝트 요구 사항을 신중하게 평가하고 비용 대비 혜택을 고려하는 것이 좋다.

> Enterprise Edtion 제공 부가 기능

- Thread Pool (4단원에서 설명)
- Enterprise Audit
- Enterprise TDE
- Enterprise Authentication
- Enterprise Firewall
- Enterprise Monitor
- Enterprise Backup
- MySQL측으로부터 기술 지원 받을 수 있음

등
데이터베이스 성능 최적화, 고가용성, 강화된 보안, 백업 및 복구, 모니터링 및 관리를 향상하는데 도움을 주는 기능들이다. 


> DBMS 선택 기준

다음 우선순위대로 고려할 것.
1. 안정성
2. 성능, 기능
3. 관련 커뮤니티 활성도, 인지도

=> 안정성이 가장 중요하다.
성능/기능은 돈으로 해결될 수 있지만, 안정성이 낮다면 특히 대규모 서버에서 큰 문제가 생길 가능성이 높다.
또, 유명하지 않은 DBMS를 선택한다면 학습과 문제 해결에 어려움을 겪을 수 있고, 전문가 수도 적다.


> DBMS 랭킹

![image](https://github.com/inpink/CS_Database_Study/assets/108166692/bdbfedcc-ab1f-4fa6-8500-4c136ddea512)
https://db-engines.com/en/ranking


# MySQL 서버 설치

> 설치 환경

필자는 Windows 환경에서 WSL(Windows Subsystem for Linux)을 이용하여 Ubuntu(linux)에서 mysql 설치하여 사용함

윈도우10부터 윈도우에서 리눅스 사용 가능.
'우분투'라는 기능 자체 제공


> WSL, 우분투 설치

![image](https://github.com/inpink/CS_Database_Study/assets/108166692/528be79c-25b0-4980-a142-59e738e6c72d)
WSL : Windows에서 Linux 배포판을 실행할 수 있게 해주는 기술

WSL(Windows Subsystem for Linux, Linux용 Windows 하위 시스템)을 사용하면 개발자가 Linux 배포판(예: Ubuntu)을 설치하고,
기존 가상 머신 또는 이중 부팅 설정의 오버헤드 없이 Windows에서 직접 Linux 애플리케이션, 유틸리티 및 Bash 명령줄 도구를 사용할 수 있습니다.
(출처 : Microsoft)

![image](https://github.com/inpink/CS_Database_Study/assets/108166692/648aca19-be4c-4a18-ade1-deb786100fee)
우분투 : 리눅스의 여러 가지 배포판 중 하나

Windows에서 WSL를 설치하고, Ubuntu를 설치하고, 그 내부에 mysql를 설치해주면 된다.
아래의 마이크로소프트 공식 홈페이지를 참고하자.
https://learn.microsoft.com/ko-kr/windows/wsl/install

위 공식 홈페이지에서 알려주는대로
Windows에서 관리자 모드로 Powershell을 열고, 
~~~
wsl --install
~~~
명령어를 통해 wsl와 ubuntu를 쉽게 설치할 수 있다. 
설치 후 컴퓨터 재부팅을 해줘야 한다. 
![image](https://github.com/inpink/CS_Database_Study/assets/108166692/cdc9b1ef-9e1a-4e8e-86be-8d5d1b2e9234)




> mysql을 windows에서 안쓰고 linux를 굳이 깔아 쓰는 이유?

ㄹㅇ

![image](https://github.com/inpink/CS_Database_Study/assets/108166692/663f216e-8d8f-407d-9252-b53738e3fa01)

set persist_only로 max_connections를 바꾼 뒤, 
set persist_only나 set persist로 변경된 시스템 변수를 조회함. 
![image](https://github.com/inpink/CS_Database_Study/assets/108166692/572a9878-d395-4932-9c3a-540327f20f0d)
9번 참고해서 설명 추가 예정


![image](https://github.com/inpink/CS_Database_Study/assets/108166692/3776479e-13c1-4c4c-a308-892f12fa7860)
![image](https://github.com/inpink/CS_Database_Study/assets/108166692/9026aba3-0b31-4a13-9721-d288e51d4677)

![image](https://github.com/inpink/CS_Database_Study/assets/108166692/b38ee026-0693-4483-8035-7a2c0c818974)


3단원
![image](https://github.com/inpink/CS_Database_Study/assets/108166692/fd7a9958-474a-4ea7-81bf-53066a70bcca)

![image](https://github.com/inpink/CS_Database_Study/assets/108166692/1038445f-8601-4340-acc8-a4f2d251a9b1)

![image](https://github.com/inpink/CS_Database_Study/assets/108166692/ef9d1838-c07b-49e4-af50-652b402a5d96)> 목차


![image](https://github.com/inpink/CS_Database_Study/assets/108166692/b6727b8a-a287-43ea-82cc-62b47c42d2b5)
=> medium 수준으로 비밀번호 지정해줘야만 생성, 변경 가능

![image](https://github.com/inpink/CS_Database_Study/assets/108166692/ce514fe9-d929-4987-88e9-91cd1b3073f5)
=> password history 남김, 따로 옵션 설정안해줬으므로 SHA-2방식으로 비밀번호 암호화, 여기도 마찬가지 medium 적용됨


![image](https://github.com/inpink/CS_Database_Study/assets/108166692/eb599fc3-8f62-43ca-8bd6-eafc15ac030d)
=> view도 하나의 테이블로 인식됨. 다만 특성이 많이 다른 것. (필기 추가 예정)

![image](https://github.com/inpink/CS_Database_Study/assets/108166692/d8b345e4-7eda-48f4-92cd-e417c21164bf)
=> view는 조회시마다 테이블에서 데이터를 가져와 생성됨!

![image](https://github.com/inpink/CS_Database_Study/assets/108166692/8873487d-26f0-46ae-9f40-0f934ff472e0)
70p


![image](https://github.com/inpink/CS_Database_Study/assets/108166692/d23b1390-42ce-4385-9f01-d937166b50e0)

![image](https://github.com/inpink/CS_Database_Study/assets/108166692/1d713c28-0ff0-4e07-be0c-a24557d47a98)
=>현재 로그인한 사용자를 확인


## 이 책의 특징 

1.  
