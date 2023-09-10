# MySQL 서버 설치

> 설치 환경

필자는 Windows 환경에서 WSL(Windows Subsystem for Linux)을 이용하여 Ubuntu(linux)에서 mysql 설치하여 사용함　   
　   
윈도우10부터 윈도우에서 리눅스 사용 가능.　   
'우분투'라는 기능 자체 제공　   
　   
　   
> WSL, 우분투 설치

![image](https://github.com/inpink/CS_Database_Study/assets/108166692/528be79c-25b0-4980-a142-59e738e6c72d)　   
WSL : Windows에서 Linux 배포판을 실행할 수 있게 해주는 기술　   
　   
- WSL(Windows Subsystem for Linux, Linux용 Windows 하위 시스템)을 사용하면 개발자가 Linux 배포판(예: Ubuntu)을 설치하고,　   
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
위 사진과 같이,　   
~~~
wsl -l -v
~~~
명령어를 실행했을 때 　   
WSL 버전이 2여야 mysql이 정상적으로 설치된다.　   
　   
Powershell에서 wsl --install 을 사용하지 않고 다른 방법을 사용한다면 wsl 버전 1이 설치될 가능성이 있다.　   
그러면 ubuntu에서 mysql이 제대로 설치되지 않을 수 있다.　   
　   
　   
> Ubuntu에 mysql 설치

위의 방법대로 잘 따라왔다면, 재부팅 이후 WSL 2와 Ubuntu가 정상적으로 설치되었다. 　   
윈도우 검색창에서 Ubuntu를 열어준다.　   
![image](https://github.com/inpink/CS_Database_Study/assets/108166692/387a5672-319b-49c2-8f35-567cc0b50b2c)　   
　   
　   
ⓐ 우분투 서버 업데이트　   
~~~
sudo apt-get update
~~~
　   
ⓑ mysql 설치　   
~~~
sudo apt-get install mysql-server
~~~

　   
만약 설치 도중에 아래와 같은 에러가 뜬다면,　   
~~~
Renaming removed key_buffer and myisam-recover options (if present)
Cannot open /proc/net/unix: No such file or directory
Cannot stat file /proc/1/fd/5: Operation not permitted
Cannot stat file /proc/1/fd/10: Operation not permitted
Cannot stat file /proc/1/fd/7: Operation not permitted
Cannot stat file /proc/19/fd/10: Operation not permitted
Cannot stat file /proc/19/fd/11: Operation not permitted
Cannot stat file /proc/19/fd/5: Operation not permitted
~~~
WSL 1버전을 쓰고 있을 가능성이 높다.　   
그럴 땐, WSL와 Ubuntu와 MySQL 관련 내용을 모두 깔끔하게 삭제해준 뒤　   
위에 적힌 WSL 2버전으로 설치해준 뒤 재부팅해주면 잘 설치된다.　   
　   
　   
> mysql을 windows에서 안쓰고 linux를 굳이 깔아 쓰는 이유?

1) 리눅스는 오픈소스, 무료 OS이다.　   
무료이기에 365일 24시간 돌아가야 하는 웹 서버로 쓰기에 적합하다.　   
　   
2) 많은 웹 서버를 리눅스로 사용하고 있다. 　   
그만큼 커뮤니티가 크기에, 정보도 많다.　   
　   
3) 오픈소스이고, 커뮤니티가 큰 만큼 버그가 적고 보안이 뛰어나다.　   
오픈소스라 보안에 취약하지 않을까 생각할 수 있지만　   
오히려 오픈소스이기에 정보가 다 공개되어 있고, 많은 사용자들이 사용하고, 많은 보안 위협과 버그들이 빠르게 수정되고 업데이트 된다.　   
　   
4) 리눅스 서버는 업데이트 후 재부팅을 하지 않아도 된다.　   
따라서 365일 24시간 돌아가야 하는 웹서버로 적합하다. 　   
sudo apt-get update로 리눅스 서버 업데이트를 해도, 재시작이 필요없다.　   
우리가 Windows에 Ubuntu를 설치할 때만 생각해봐도 Windows는 재시작이 필요하다.　   
