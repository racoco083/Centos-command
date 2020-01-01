# Centos-command
get used to Centos

### service network restart

=> Failed to restart network.service: Unit network.service not found 이런 오류가 난다면

yum install network-scripts를 하면 된다.

### network ethernet setup
#### 장치명, 첫번째 이더넷카드 

DEVICE=eth0 

#### IP 부여 방식 결정, static 은 고정IP 

BOOTPROTO=static 

#### 이더넷카드의 MAC 주소 

HWADDR=XX:XX:XX:XX:XX:XX 

#### GUI 모드에서의 편리한 네트워크설정 허용, TUI에선 필요없음 

NM_CONTROLLED=no 

#### 시스템 시작시 자동으로 활성화

ONBOOT=yes 

#### Ethernet 에 대한 설정 

TYPE=Ethernet 

#### 고유ID를 부여하는 것으로 자동으로 부여됨 

UUID=XXXXXXX-XXX-XXX-XXX-XXXXXXX 

#### 브로드캐스트 지정 

BROADCAST=192.168.5.255 

#### 게이트웨이 지정

#### IP 주소 지정 

IPADDR=192.168.5.16 

#### 서브넷마스크 지정 

NETMASK=255.255.255.0 

#### 게이트웨이 지정

GATEWAY=192.168.5.1

### nmcli d (랜카드 설정 확인)

![image](https://user-images.githubusercontent.com/21019088/71590725-f845ae80-2b6c-11ea-9da4-4cee11a4c324.png)

### ss 명령어 항목 정리

[Status]

  - LISTEN : 서비스 요청을 기다리고 있는 상태(클라이언트)

  - UNCONN : UDP

  - ESTAB  : 실제로 데이터를 교환하고 있는 상태

  - TIME-WAIT : 연결 종료 후 일정시간동안 유지하고 있는 상태

  - FIN-WAIT  : 연결 종료 중인 상태

  - SYN-SENT  :  SYN 패킷을 보낸후 연결을 요청한 상태

  - SYN-RECEVIED : SYN 패킷을 받은후 ACK 패킷을 기다리고 있는 상태

[Recv-Q, Send-Q]

  - 소켓 버퍼 사이즈

 

[Local Address:Port , Peer Address:Port]

 - ipv4

  0.0.0.0:<port_number>

  *:<port_number>



 - ipv6

  :::<port_number> ( ipv4 포함한 모든 주소 )

 -> ipv6에서 ipv4 표현 방법

  ::ffff:<ipv4_address>:<port_number>

### ss -lt (현재 네트워크에 접속된 TCP 정보)

### ss -lu (현재 네트워크에 접속된 UDP 정보)

### ss -option | egrep -i 'mysql' (현재 네트워크에 접속된 정보에서 'mysql'찾기)

### ss -t state time-wait (연결 종료 후 일정 시간동안 유지하고 있는 상태를 확인합니다.)

### cat /etc/services | grep '^ssh.*tcp' (서비스 포트 정보 확인)

### /sbin/ip -6 addr add <IPv6>/<Prefix길이> dev <interface>
 
 ex) /sbin/ip -6 addr add 2001:2b8:2:fff3::105/64 dev eth0

### /sbin/ip -6 addr del <IPv6>/<Prefix길이> dev <interface>

 ex) /sbin/ip -6 addr del 2001:2b8:2:fff3::105/64 dev eth0



