## 시스템 
- RHEL 7, 8 모두 Systemd를 사용하여 부팅, 시스템 서비스를 관리.

## 네트워크
- 네트워크 관리 방법이 서로 다름.
- RHEL 7은 `network`라는 서비스를 사용, `network-scripts`라는 스크립트를 작성함.
- RHEL 8은 `NetworkManager`라는 서비스를 사용.

예시: eth0 인터페이스 구성하기:
``` (RHEL 7의 network-scripts)
DEVICE=eth0
BOOTPROTO=static
ONBOOT=yes
IPADDR=192.168.1.100
NETMASK=255.255.255.0
GATEWAY=192.168.1.1
DNS1=8.8.8.8
DNS2=8.8.4.4
```
``` (RHEL 8의 NetworkManager를 관리하기 위한 Bash 스크립트)
nmcli device status

nmcli con mod eth0 ipv4.addresses 192.168.1.100/24
nmcli con mod eth0 ipv4.gateway 192.168.1.1
nmcli con mod eth0 ipv4.dns "8.8.8.8,8.8.4.4"
nmcli con mod eth0 ipv4.method manual
nmcli con mod eth0 connection.autoconnect yes

nmcli con down eth0
nmcli con up eth0
```

## 컨테이너화
- RHEL 7은 Docker 기반의 컨테이너화를 지원.
- RHEL 8은 Podman 등 기반의 컨테이너화를 지원.

## 다음 주 화요일까지?
* 구글 트렌드, 스택오버플로 자료량, 깃허브 스타 등.
* 화요일 ==> 1시간 전체 PPT 발표, 수요일==> 실습.
* 화요일: esxi에 설치하기 위한 가상매모리, UEFI 등, 고려해야 할 요소.