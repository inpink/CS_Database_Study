#MySQL 서버 연결

1. 우분투 실행

2. mysql 실행
~~~
sudo systemctl start mysql
~~~
이 시점에서 이미 mysql은 실행되어 있다. 
우분투에서 접속을 해서 mysql을 사용할 수 있다.
아직은 접속하지 않은 상태이다.

3. 시작된 mysql 서버 상태 확인
~~~
sudo systemctl status mysql
~~~


4. mysql 접속
~~~
sudo /usr/bin/mysql -u root -p
~~~
이제부터, linux> 라고 떴던 shell에서 
mysql> 이라는 shell로 바뀌며  mysql을 사용한다.

코드를 조금 더 분석해보자.

💙sudo
 : 리눅스에서 sudo는 "Superuser Do"의 약자로,
 사용자가 슈퍼유저(root) 또는 다른 특정 사용자의 권한을 사용하여 명령어나 프로그램을 실행할 수 있게 해주는 명령어다.
 슈퍼유저는 시스템 전체에 대한 제한 없는 권한을 가진 특별한 사용자 계정이며, sudo를 사용하면 보안과 권한 관리를 효과적으로 관리할 수 있다.

💙/usr/bin/mysql 
: 리눅스에서 우리가 실행하려는 mysql가 있는 위치

💙 -u
 : 이 옵션은 사용자 이름을 지정한다. 
 root는 사용자 이름으로, 보통 MySQL 데이터베이스 서버에 대한 최상위 권한을 가진 사용자인 "root" 사용자를 나타낸다. 
 (실제로 mysql에서 user를 조회하면 최상위 권한을 가진 root라는 이름의 user가 있다.)
 사용자 이름을 지정하여 해당 사용자로 로그인할 수 있다.
 
💙 -p
: 이 옵션은 비밀번호를 입력할 것임을 나타냅니다. MySQL에 로그인할 때 비밀번호를 사용자로부터 입력받도록 합니다. -p 옵션을 사용하면 MySQL 클라이언트가 비밀번호를 요청할 것입니다. 실제 비밀번호는 이 옵션 뒤에 따라오는 비밀번호를 입력하여 제공해야 합니다.

따라서 -u root -p를 사용하면 MySQL 데이터베이스 서버에 "root" 사용자로 로그인하고 해당 사용자의 비밀번호를 입력할 수 있게 됩니다. 이를 통해 MySQL 서버에 대한 권한 있는 작업을 수행할 수 있습니다.


MySQL서버에 접속하는 다른 방법들도 알아보자.
~~~
linux> mysql -u root -p --host=localhost --socket=/tmp/mysql.sock
~~~
위와 같이 host와, socket을 지정해줄 수도 있다. 
지정해주지 않으면 default로 호스트는 localhost, 소켓 파일은 **MySQL 서버의 설정 파일에 저장된 위치**를 참고해서 소켓을 넣어 사용한다.

5. 성공적으로 접속되었다면, 
쉘에 mysql > 라고뜨며 리눅스에서 mysql 서버를 사용할 수 있다. 


6. 실행중인 mysql 서버 종료
sudo systemctl stop mysql


우분투에서는 mysqld말고 mysql으로 사용(책에는 mysqld라고 되어있지만)

7. 우분투 재시작 시, 항상 mysql도 자동으로 재시작하도록
~~~
sudo systemctl enable mysql
~~~

8. mysql 서버 재시작
~~~
sudo systemctl restart mysql
~~~

