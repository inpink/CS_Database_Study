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

