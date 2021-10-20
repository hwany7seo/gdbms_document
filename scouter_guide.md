# Scouter\_Guide

Scouter 연동 모니터링

\* Overview

Scouter는 오픈소스 APMd으로 JVM(WAS, Standalone application)을 사용하는 어플리케이션 및 OS 자원에 대한 모니터링 모니터링 기능을 제공하고 있습니다.

Scouter 연동을 통해 CUBRID Manager Server에서 체크되는 데이터를 Scouter Server와 Client를 통해 모니터링 할 수 있습니다.

성능데이터는 CUBRID Manger Server에서 5초마다 데이터를 읽어 Scouter Server로 보냅니다.

이후 Scouter Client는 Scouter Server에 데이터를 요청하여 각 View를 통해 표시합니다.

\* Install Guide

Scouter를 통해 Cubrid 모니터링을 위해서는 Scouter Server와 Client 그리고 Agent 설치 및 설정이 필요합니다.

아래에서 간단한 설치 및 설정 방법을 설명합니다.

* Scouter Server ([https://github.com/scouter-project/scouter/releases/](https://github.com/scouter-project/scouter/releases/))

![](.gitbook/assets/0)

위 Url에서 차후 업데이트(Cubrid 지원) 될 Version을 다운 받습니다.

Linux Or Windows에서 압축을 해제하여 설치합니다.

\[압축 된 파일]

![](.gitbook/assets/1)

Linux 기준 startup.sh 실행

Windows 기준 startup.bat 실행

\[실행 화면]

![텍스트이(가) 표시된 사진

자동 생성된 설명](.gitbook/assets/2)

자세한 Setup Guide는 Scouter에서 제공하는 Setup.md 또는 문서를 참고하길 바랍니다.

[https://github.com/scouter-project/scouter/blob/master/scouter.document/main/Setup.md](https://github.com/scouter-project/scouter/blob/master/scouter.document/main/Setup.md)

* Cubrid Agent ([https://github.com/scouter-contrib](https://github.com/scouter-contrib))

추후 위 URL에서 코드 관리 및 Release 될 예정입니다.

**\[압축 파일]**

![](.gitbook/assets/3)

\[설정 관련]

/conf/scouter\_cubrid.conf (접속 설정)

![텍스트이(가) 표시된 사진

자동 생성된 설명](.gitbook/assets/4)

net\_local\_udp\_ip (default: 127.0.0.1) : cubrid-agent가 실행 될 machine IP.

net\_local\_udp\_port (default : 6200) : cubrid-agent가 사용 할 udp port.

net\_collector\_ip : scouter server가 실행 된 machine IP.

net\_collector\_udp\_port : scouter server가 사용하고 있는 udp port

net\_collector\_tcp\_port : scouter server와 agent가 tcp 통신 할 port. (Server 설정과 동일하게 설정)

cubrid\_cms\_ip : CUBRID Manager Server (CMS)가 실행 된 machine IP.

cubrid\_cms\_port : CUBRID Manager Server (CMS)에 설정 된 https port.\
(CUBRID/conf/cm.conf -> cms\_port 설정)

log\_keep\_days = log 최대 보관 일.

/conf/alert\_warning.conf (alert 설정)

![텍스트이(가) 표시된 사진

자동 생성된 설명](.gitbook/assets/5)

단독 Item을 모니터링 하는 값이 해당 값을 넘을 경우 warning으로 등록하여 Client를 통해 Alert 메시지 확인 가능. (scouter plugin 확장을 통해 타 client로 알림 가능)

Agent 실행 전 파일을 통해서도 설정 가능하며, 실행 후 Client를 통해 설정 가능 (UI Guild 참고)

\[실행 관련]

/startup.sh (linux에서 실행) , /stop.sh (linux에서 종료)

/startup.bat (windows에서 실행) /stop.bat (windows에서 종료)

![텍스트이(가) 표시된 사진

자동 생성된 설명](.gitbook/assets/6)

* Scouter Client ([https://github.com/scouter-project/scouter/releases/](https://github.com/scouter-project/scouter/releases/))

![](.gitbook/assets/7)

추후 위 URL에서 차후 업데이트(Cubrid 지원) 될 Version을 다운 받습니다.

Linux Or Windows에서 압축을 해제하여 설치합니다.

\[압축 된 파일]

![텍스트이(가) 표시된 사진

자동 생성된 설명](.gitbook/assets/8)

\[실행 관련]

Scouter.exe를 실행 합니다.

이후 User Interface Guide를 참고하여 진행 합니다.

\[ Client User Interface Guide ]

* 접속

![텍스트이(가) 표시된 사진

자동 생성된 설명](.gitbook/assets/9)

위와 같이 로그인 창을 이용하여 로그인 합니다.

* Agent 접속 확인

![](.gitbook/assets/10)

Cubrid Agent가 Server가 연결되었을 경우 위그림같이 Objects View에 Object가 추가되며,

Agent가 실행 된 HostName과 하위에 Cubrid Agent 연결이 확인됩니다.

* Perspective 추가

Cubrid Agent 정보를 확인하기 위해서 Perspective를 추가할 수 있습니다.

아래 그림과 같이 Perspective를 추가합니다.

![](.gitbook/assets/11) ![텍스트이(가) 표시된 사진

자동 생성된 설명](.gitbook/assets/12)

아래 그림과 같이 Perspective가 추가됩니다. 초기 View 종류 및 위치는 추후 달라질 수 있습니다.

![](.gitbook/assets/13)

* View 추가

ObjectView에 Cubrid Object를 선택한 후 Context Menu 및 MainMenu(Object)를 통해

초기 Perspective에 보다 많은 View를 추가할 수 있습니다.

각 View에 Context Menu로는 고정된 DB 와 Counter를 가진 View가 추가되며,

재시작시에도 DB, Counter 선택이 고정,유지 됩니다.

![테이블이(가) 표시된 사진

자동 생성된 설명](.gitbook/assets/14) ![테이블이(가) 표시된 사진

자동 생성된 설명](.gitbook/assets/15)

![](.gitbook/assets/16)

![텍스트이(가) 표시된 사진

자동 생성된 설명](.gitbook/assets/17)

* View 소개

**\[ServerInfo]**

![테이블이(가) 표시된 사진

자동 생성된 설명](.gitbook/assets/18)

CMS와 연결된 CUBRID DB 정보 및 DB에 CPU 사용량, ACTIVE SESSION,

LOCK WAIT SESSIONS 정보가 표시되며, 해당 View는 닫기가 되지 않고 최소화만 가능합니다.

\+ CPU(%) : DB에 CPU 사용량.

\+ ACTIVE SESSION : 각 DB에 접속된 Active TranList 합. (gettransactioninfo 정보)

\+ LOCK WAIT SESSIONS : 각 DB에서 wait\_for\_lock\_holder가 -1이 아닌 TranList 합. (gettransactioninfo 정보)

**\[SingleRealTimeMultiView]**

![](.gitbook/assets/19)

DB 정보 및 Broker 정보 중 단독 Item을 그래프로 표시하는 View로 지원하는 Item List는

위 그림과 같습니다.

* Item List

1. ServerInfo 정보와 동일 정보

Cpu Usage : DB에 CPU 사용량 (ServerInfo 정보와 동일)

Active Sessions : 각 DB에 접속된 활성화 된 TranList에 합. (gettransactioninfo 정보)

Lock Wait Sessions : 각 DB에서 DB LOCK Wait TranList에 합. (gettransactioninfo 정보)

1. StatDump 정보 List (cubrid statdump util을 통해 확인 가능한 Num 값)

Data Page IO Writes

Data Page IO Reads

Data Page Fetches

Data Page Dirties

Data Buffer Hit Ratio

Query Sscans

Sort IO Page

Sort Data Page

1. PlanDump 정보

XASL Plan Hit Rate (%) : plandump XASL Cache에 Hits 값을 Lookups 값으로 나눈 Percent(%) 정보.

Filter Predicate Hit Rate (%) : plandump에 Filter Predicate Cache에 EntryHits 값을 Lookups 값으로 나눈 Percent(%) 정보

1. Broker Status 정보

Transaction Per 5 Second : Broker Status 정보의 TPS 정보를 5초간 누적한 정보.

Query Per 5 Second : Broker Status 정보의 QPS 정보를 5초간 누적한 정보.

Error Query Per 5 Second : Broker Status 정보의 Error Query 정보를 5초간 누적한 정보.

**\[실시간 데이터와 과거 데이터 View]**

하기 그림과 같이 SingleRealTimeMutiView에서 지원하는 Counter Item은 Context Menu를 통해

실시간 데이터 또는 과거 데이터를 확인할 수 있는 RealTime View와 Past View 2가지를 추가 할 수 있다.

![테이블이(가) 표시된 사진

자동 생성된 설명](.gitbook/assets/20)

1. **실시간 데이터 (RealTime) View : CMS로부터 5초 단위로 넘어 오는 실시간 정보**

\[View 추가 팝업]

\[View 화면]

\[Warning Alert 설정]

RealTime View에서는 Setting 버튼을 통해 아래와 같이 각 Counter Item별로 Alert warning 값 설정이 가능하며 수정사항은 agent/conf/alert\_warning.conf파일에 저장되어 Agent에서 Alert Warning이 발생합니다.



1. **하루 이하 과거 데이터 (Past – Less than a day) View : 실시간 정보를 하루 이하에 설정으로 기간 Data를 그래프로 표시**

\[View 추가 팝업]

\[View 화면]

1. **하루 이상 과거 데이터 (Past – More then a day) View : 5초 단위에 데이터를 5분간 누적하여 Data를 그래프로 표시.**

\[View 추가 팝업]

\[View 화면]

**\[DB SpaceInfo]**

각 DB에 Volume에 관련 Space 정보를 나타내는 View

**\[Long Transaction List]**

Transaction중 3초이상에 Long Transaction 정보가 View가 생성된 이후 업데이트 됩니다.

같은 SQL TEXT라도 host, pid, user, program이 다를 경우 다른 Transaction으로 판단합니다.

MaxList 개수 변경이 가능하며 10\~1000까지 Data를 확인 할 수 있습니다.
