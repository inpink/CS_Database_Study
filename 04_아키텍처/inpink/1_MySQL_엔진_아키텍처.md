# MySQL 엔진 아키텍처
　   
　   
> MySQL의 전체 구조

![image](https://github.com/inpink/CS_Database_Study/assets/108166692/fa116b19-6a69-4540-bc8a-fb80c875500d)　   
[ 사진 출처 : MySQL Documentation](https://dev.mysql.com/doc/refman/8.0/en/pluggable-storage-overview.html)　   
　   
　   
> 프로그래밍 API

이미지 상단을 보자.　   
MySQL은 대부분의 프로그래밍 언어로 접근하여 사용할 수 있다. 　   
MySQL은 C API, JDBC, .NET 등의 표준 드라이버를 제공한다. 　   
이 드라이버를 이용하여 C, C++, PHP, Java, Python 등의 많은 언어에서 MySQL 서버에 접근하고, 쿼리를 보내 사용할 수 있다.　   
　   
> MySQL 서버

"MySQL 서버"는 크게 ⓐ MySQL 엔진,  ⓑ 스토리지 엔진 2가지로 나누어진다.　   
　   
ⓐ MySQL 엔진 　   
  - 커넥션 핸들러 : 클라이언트와 소통　   
  - SQL 파서 및 전처리기　   
  - 옵티마이저 : 사용자가 입력한 쿼리를 분석하여, 쿼리의 실행을 최적화하기 위해 사용 (아래에서 더 자세히 설명)　   
  - 특징 : 표준 SQL 문법을 지원하여, 표준 문법을 사용한 쿼리는 타 DBMS와 호환하여 실행할 수 있다.　   

　   
ⓑ 스토리지 엔진　   
  - 실제 데이터를 디스크 스토리지에 저장하고, 데이터를 읽어온다.　   
  - MySQL에서 MySQL 엔진은 하나지만, "스토리지 엔진"은 여러 개를 사용할 수 있다. 　   
  - 스토리지 엔진의 핸들러 API를 구현하면 누구나 원하는대로 구현해서 MySQL에서 사용할 수 있다.　   
  - 기본적으로 MySQL은 InnoDB 스토리지 엔진을 사용한다.　   
  - 이외로도 MySQL은 여러 스토리지 엔진을 지원하는데, InnoDB, MyISAM, Memory 등이 있다.　   
  - 아래 코드와 같이, 각 테이블에 어떤 storage engine을 사용할 것인지 지정해줄 수 있다.　   
~~~
mysql> CREATE TABLE test (i INT) ENGINE = EXAMPLE;
~~~
=> 이렇게 생성한 test table은 EXAMPLE storage engine이 데이터를 읽고, 쓰고, 수정하는 작업(INSERT, UPDATE, DELETE, SELECT 등)을 담당한다.　   
EXAMPLE storage engine은 스토리지 엔진의 핸들러 API를 구현하여 내가 등록해준 스토리지 엔진이다.　   
　   
 

MySQL 서버에서 기본으로 제공되는 InnoDB 스토리지 엔진, MyISAM 스토리지 엔진을 구분

