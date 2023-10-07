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
=> MySQL은 Oracle에 이은 2위이다.
　   
　   
