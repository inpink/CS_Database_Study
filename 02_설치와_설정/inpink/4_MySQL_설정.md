


9. 시스템 변수 ( 38p~)
https://dev.mysql.com/doc/refman/8.0/en/server-system-variable-reference.html


44p set persist 관련  조회
performance_schema.varaibles_info  : performance_schema.variables_info 테이블은 이러한 시스템 변수의 메타데이터를 포함하고 있으며, 이를 통해 각 시스템 변수의 이름, 데이터 형식, 설명 등을 조회할 수 있습니다.


show variables like "%version%";
=> version과 관련된 "시스템 변수" 모두 출력



10. 데이터베이스 생성
CREATE DATABASE TESTDB;

11. 데이터베이스 목록 확인
SHOW DATABASES;



![image](https://github.com/inpink/CS_Database_Study/assets/108166692/663f216e-8d8f-407d-9252-b53738e3fa01)

set persist_only로 max_connections를 바꾼 뒤, 
set persist_only나 set persist로 변경된 시스템 변수를 조회함. 
![image](https://github.com/inpink/CS_Database_Study/assets/108166692/572a9878-d395-4932-9c3a-540327f20f0d)
9번 참고해서 설명 추가 예정


![image](https://github.com/inpink/CS_Database_Study/assets/108166692/3776479e-13c1-4c4c-a308-892f12fa7860)
![image](https://github.com/inpink/CS_Database_Study/assets/108166692/9026aba3-0b31-4a13-9721-d288e51d4677)

![image](https://github.com/inpink/CS_Database_Study/assets/108166692/b38ee026-0693-4483-8035-7a2c0c818974)

