# MySQL 설정 파일

일반적으로 MySQL 서버는 **단 하나의 설정 파일**을 이용한다. 　   
 　   
설정 파일의 이름은 아래와 같다. 　   
Unix, Linux : my.cnf 　   
Windows : my.ini 　   
 　   
MySQL은 지정된 여러 개의 디렉터리를 순차적으로 탐색하다가, **처음 발견된 단 하나의 my.cnf 설정 파일을 이용한다** 　   
 　   
아래 명령어를 통해, 내 MySQL 서버가 어디에 있는 어떤 my.cnf 파일을 사용하는지 확인할 수 있다. 　   
~~~
linux> mysql --verbose --help
~~~
 　   
실행 결과 중, 아래와 같은 부분을 보자. 　   
~~~
Default options are read from the following files in the given order:
/etc/my.cnf /etc/mysql/my.cnf ~/.my.cnf
~~~
① /etc/my.cnf 　   
② /etc/mysql/my.cnf 　   
③ ~/.my.cnf 　   
위의 3가지 순서대로 탐색을 하며 설정파일 1개를 찾는다는 뜻이다. 　   
 　   
내 MySQL 서버 환경에서는 ① /etc/my.cnf 파일은 존재하지 않고, 　   
② /etc/mysql/my.cnf 파일이 존재했다.  　   
즉, 이 파일이 설정 파일로 선택된다. 　   
![image](https://github.com/inpink/CS_Database_Study/assets/108166692/663f216e-8d8f-407d-9252-b53738e3fa01) 　   
cat을 사용하여 설정 파일을 열어보자. 　   

위 사진에서 볼 수 있듯,  　   
② /etc/mysql/my.cnf 파일에는 !includedir이 이용되어,  　   
이 파일 1개의 내용만을 설정 파일로 사용하는 것이 아니라, 　   
추가로 2개의 directory에 있는 모든 파일의 내용을 설정으로 사용하는 것을 알 수 있다. 　   
 　   
> 설정 그룹

설정 파일에 있는 [mysqld] [mysql] [mysqldump] 같은 것을 **설정 그룹** 이라고 한다. 　   
MySQL 설정 파일은 여러 개의 설정 그룹을 담고 있다.  　   
보통, **실행 프로그램 이름**이 설정 그룹명이다. 　   
예를 들어, [mysqldump] 설정 그룹은 mysqldump 프로그램이 참조하게 된다. 　   
 　   
위의 사진에서 볼 수 있듯, 　   
!includedir을 이용하여 설정 그룹을 여러 file로 구분해두었다. 　   
 　   
 　   
> MySQL 명령어 !includedir

!includedir는 MySQL 설정 파일에서 사용되는 특수한 지시어.  　   
설정 파일 내에서 다른 설정 파일들을 포함시킨다.  　   
!includedir 뒤에 디렉터리 경로를 지정하면 해당 디렉터리 내의 설정 파일들을 모두 포함시킨다.  　   
  　   
일반적으로 MySQL 설정 파일은 크고 복잡할 수 있으므로, 설정을 모듈화하고 유지 관리를 쉽게 하기 위해 여러 개의 설정 파일로 나누는 것이 좋다.  　   
  　   
참고로, my.cnf 파일에서 # 기호는 주석(comment)을 나타낸다.  　   
  　   
  　   
