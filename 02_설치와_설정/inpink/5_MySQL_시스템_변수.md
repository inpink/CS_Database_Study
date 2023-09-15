
## MySQL 시스템 변수

MySQL 서버는 설정 파일의 내용을 읽어 필요한 설정들을 한다.
이 때, 필요한 값들을 **별도의 변수에 저장**해두는데, 이를 **시스템 변수(System Variables)** 라고 한다.

시스템 변수들은 아래 명령어를 통해 확인할 수 있다.
~~~
mysql > SHOW GLOBAL VARIABLES;
또는
mysql > SHOW VARIABLES;
~~~

> 시스템 변수 중 'GLOBAL VARIABLES'과 'VARIABLES'의 차이는 무엇일까?

우선 시스템 변수들의 목록이 담긴 documentataion를 보고오자.
https://dev.mysql.com/doc/refman/8.0/en/server-system-variable-reference.html 　   

위 docs 에 적혀있는 시스템 변수의 5가지 속성을 알아보자.
- Cmd-Line : Yes면, MySQL 서버의 명령어를 통해 이 시스템 변수의 값을 변경하는 것이 가능하다
- Option file : 설정 파일(my.cnf)로 제어할 수 있는 변수인지의 여부이다.
- System Var : 시스템 변수인지 유무이다. 당연히 위에선 다 Yes이다.
  예전에는 변수명에 '-'를 쓰기도 하고 '_'를 쓰기도 했는데,
  MySQL 8.0버전부터 ' _ '를 구분자로 사용하도록 통일되었다.
- Var Scope : 

내가 원하는 변수 명만 검색하려면, 아래와 같이 Like 연산자를 이용하자. 
![image](https://github.com/inpink/CS_Database_Study/assets/108166692/831d9637-0a49-41eb-a04b-a6f991a056bd)


44p set persist 관련  조회
performance_schema.varaibles_info  : performance_schema.variables_info 테이블은 이러한 시스템 변수의 메타데이터를 포함하고 있으며, 이를 통해 각 시스템 변수의 이름, 데이터 형식, 설명 등을 조회할 수 있습니다.


show variables like "%version%";
=> version과 관련된 "시스템 변수" 모두 출력



10. 데이터베이스 생성
CREATE DATABASE TESTDB;

11. 데이터베이스 목록 확인
SHOW DATABASES;




set persist_only로 max_connections를 바꾼 뒤, 
set persist_only나 set persist로 변경된 시스템 변수를 조회함. 
![image](https://github.com/inpink/CS_Database_Study/assets/108166692/572a9878-d395-4932-9c3a-540327f20f0d)
9번 참고해서 설명 추가 예정


![image](https://github.com/inpink/CS_Database_Study/assets/108166692/3776479e-13c1-4c4c-a308-892f12fa7860)
![image](https://github.com/inpink/CS_Database_Study/assets/108166692/9026aba3-0b31-4a13-9721-d288e51d4677)

![image](https://github.com/inpink/CS_Database_Study/assets/108166692/b38ee026-0693-4483-8035-7a2c0c818974)
