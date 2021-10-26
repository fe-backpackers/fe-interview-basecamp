#ISO/OSI 7계층에 대해 설명하시오.

## 결론

ISO/OSI 모델은 application(7계층) , presentation(6계층), session(5계층), transport(4계층), network(3계층), datalink(2계층), physical(1계층)으로 나위어진다

## 설명

- OSI 7계층은 왜 나누는 것일까?
통신이 일어나는 복잡한 과정을 단계적으로 나눠 단계별로 알 수 있다. 그리고 유지 보수가 용이하다.

ISO/OSI 모델은 application(7계층) , presentation(6계층), session(5계층), transport(4계층), network(3계층), datalink(2계층), physical(1계층)으로 나위어진다.

- Application(응용) 7계층은 최종 목적지로 응용 프로세스와 직접 관계하여 일반적인 응용 서비스를 수행한다.
사용자 인터페이스, 전자우편, 데이터베이스 관리 등의 서비스를 제공한다. 
데이터 전송 단위는 메시지이며 HTTP, FTP, DNS,SMTP 프로토콜 등이 해당된다.

- Presentation(표현) 6계층은 응용 계층으로 부터 받은 데이터를 하위 계층인 세션 계층에 보내기 전 통신에 적당한 형태로 변환시킨다.
세션 계층에서 받은 데이터는 응용 계츠에 맞게 변환한다.
즉, 코드 간의 번역을 담당하여 사용자 시스템에서 데이터의 형식상 차이를 다루는 부담을 응용 계층으로부터 덜어준다.
파일 인코딩, 코드변환 구문 검색,데이터 압축 및 암호화 등의 기능을 수행한다.
데이터 전송 단위는 메시지이며 JPg, Mpeg,Afp 프로토콜 등이 해당된다.

- Session(세션) 5계층은 양 끝 단의 응용 프로세스가 통신을 관리하기 위한 방법을 제공한다. 
데이터가 통신하기 위한 논리적인 연결을 담당한다. (통신 세션(TCP/IP)을 구성하며 포트번호를 기반으로 연결하고 없애는 책임을 지닌다.)
데이터 전송 단위는 메시지이며 NetBlos 프로토콜 등이 해당된다.

- Transport(전송) 4계층은 TCP,UDP 프로토콜을 통해 통신을 활성화한다. 
포트를 열어두고 프로그램들이 전송을 할 수 있게끔 해주어, 양 끝 단의 사용자들이 데이터를 주고받을 수 있다.
TCP : 신뢰성, 연결 지향적
UDP : 비신뢰성, 비연결성, 실시간
데이터 전송 단위는 TCP일경우 Segment, UDP일경우 Datagram이며 GateWay 장비를 쓴다. 

- Network(네트워크) 3계층은 데이터를 목적지까지 가장 안전하고 빠르게 전달하는 기능을 담당한다. 
라우터를 통해 이동 경로를 선택하여 IP 주소를 지정하고, 해당 경로에 따라 패킷을 전달해준다.
라우팅, 흐름 제어, 오류 제어, 세그먼테이션 등을 수행한다.
데이터 전송 단위는 패킷이며 사용 프로토콜은 IP,RIP,ARP,ICMP이다. 장비는 라우터를 사용한다.

- 데이터 링크(Data link) 2계층은 물리 계층으로 송수신되는 정보(오류, 흐름)를 관리하여 안전하게 전달되도록 도와주는 역할을 한다.
MAC 주소를 이용해 통신한다.
Frame에 MAC 주소를 부여하고 신뢰성 있는 전송을 위해 에러검출, 재전송 및 회복을 위한 오류제어기능 수행,송수신측 속도차를 해결하기 위해 흐름 제어를 진행한다.
데이터 전송 단위는 frame이며, Ethernet, ALOHA 등의 프로토콜을 사용하고, 브릿지, 스위치 등의 장비가 해당된다.

- 물리(Physical) 1계층은 데이터 링크 계층의 프레임을 받고, 다음 장치에 구리나 광섬유 또는 무선 통신 매체를 통신해 전송하기 위한 신호로 바꾸어준다.
물리적 매체를 통해 bits(데이터)를 전송하기 위해 요구되는 기능들을 정의하고, 실제 디바이스간 접속을 위한 규칙을 정의한다.
데이터 전송 단위는 bit이며 Rs232 등의 케이블을 프로토콜로 사용하고 장비는 허브, 리피터가 해당된다.

## 요약

ISO/OSI 모델은 application(7계층) , presentation(6계층), session(5계층), transport(4계층), network(3계층), datalink(2계층), physical(1계층)으로 나위어진다

## Further Stemp

TCP/IP 계층

## Reference

https://togll.tistory.com/37?category=954561 [OSI 7계층이란]
https://togll.tistory.com/40?category=954561 [OSI 7계층 계층별 장비 정리]
https://github.com/WooVictory/Ready-For-Tech-Interview/blob/master/Network/OSI%207%20%EA%B3%84%EC%B8%B5.md
[https://github.com/WooVictory/Ready-For-Tech-Interview/blob/master/Network/OSI%207%20%EA%B3%84%EC%B8%B5.md]
전공책
