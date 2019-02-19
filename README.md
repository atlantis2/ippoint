# ippoint
# UPGRADE시 주의사항
-----
* 1 기존 설치된 IPPoint의 버전을 확인하고 설치된 버전에 대한 패키지를 준비해 둔다.
* 2 업그레이드시 기존버전에 대한 정책에 대하여 백업을 한다. 
    * 모든 시스템 설정 백업 (SYSTEM >  Backup > Export) 
    * Host에 대한 정보를 Excel로 백업을 한다. ( IPPoint > Profile > Host > Excel Export)
* 3 새롭게 업그레이드를 한다. 
* 4 모든 설정이 정상 로딩 시 정상 OK
* 5 설정이 비정상적으로 올라온경우에는 이전버전으로 rollback
    * 기존 설치된 버전으로 새롭게 Upgrade를 실행한다. 
    * 기존버전으로 설치가 완료가 되면 설정을 복원한다. ( SYSTEM > Backup > Import )
* 6 고객사에서 운영중에 시스템에 적용시 설치버전에 대한 업그레이드 테스트 요망.
-----
# Changelog
* 2.0.418 - 20190219
* Scanner default 값 변경:
    * IPScan: Enable
    * NBScan: Disable
    * OSScan: Disable
    * OUIScan: Disable
* DHCPScan 추가 
-----
* 2.0.415 - 20190215
* WEB: host : ipblock, ip6block list array : 4 -> 5
* logserver key : sendkey -> logserverkey 
* auditlog 검색: command: standalone과 manager구분
* WEB: debug messages disable
-----
* 2.0.411 - 20190214
* eventviewer : column resizable
* 차단페이지 변경 : 
    * 기존 1개의 페이지(차단페이지) -> 3개의 페이지 (차단, 허용, IP충돌페이지)로 나눔.
    * image 삽입기능: /image/filename
    * preview기능: 미리보기 기능
* host: securemode icon 작업
```diff
    2.0.409 이전 버전에서는 패치시 차단페이지 내용이 없으지므로
    관리자 혹은 엔지니어가 내용을 넣어주어야 함.
```
-----
* 2.0.402 - 20190207
* GUI: Main Change: TabMenu
* GUI: hostfilter-object: resizable
-----
* 2.0.382 - 20190114
* IP/IP6 reset
    * 해결: 관리자가 IP/IP6 Reset가능하게
-----
* 2.0.38 - 20190111
* TeamAC버그 
    * 증상: IP충돌호스트가 발생시 허용 Host에대하여 차단이 되는 현상 발생
    * 해결: ipprocessing에서 기존의 ipblock list에 미체크된 리스트 삭제, ipcollision ipaddress에대해서는 skip, vtysh: host allow host deny 수정
* Host List 늦음 현상
    * 증상: Host List시 리스트가 많으면 오래걸림.
    * 해결: profile_host_list시 clearcache를 edit시에만
-----
* 2.0.373 - 20181227
* VLAN Delete 행업
    * 증상: unregister_netdevice 메세지 발생 및 행업 현상 
    * 해결: 정상적으로 hangup VLAN삭제 
-----
* 2.0.370 - 20181224
* log send format 변경 : IPPoint Format -> Tranditional Format ( receiver쪽에서 facility, severity를 구분하지 못함 )
* dhcp 설정 변경 ( 이전버전이랑 설정포맷 변경) 
* dhcp relay 설정 추가 
-----
* 2.0.360 - 20181116
* 호스트가 차단 혹은 멀티일 경우에 30분동안 응답이 없을 경우에는 차단메세지 보내는것 금지 
    * host(A), host(B)가 동일 IP주소를 가지고 있고, host(A)가 차단 혹은 멀티이고 장기 미사용중(Poweroff)일 경우 host(B)가 허용으로 사용중일 경우 host(B)가 host(A)의 정책에 대한 시그널을 받게 되어 차단되는 경우 발생
    * host(B)에는 VM(VMware, VirtualBox)이 설치되어 브리지로 운영중 interface카드가 promiscuous모드로 전환되는것같음. 
    * promiscuous모드로 전환되어 모든 차단 시그널을 받게 되어 자신의 IP에 대한 요청으로 인식하여 cache 
-----
* 2.0.359 - 20181109
* 차단 호스트 IP(IP6)변경시 일시적으로 정상동작
    * 원인 : ip(6)block요소 서치시 target IP(6)로 조회하여 문제 발생 
    * 해결책: ip(6)block요소 서치시 ip(6)block요소의 src/dst에 대한 주소로 서치
* upgrade/reboot/shutdown시 host write 순서 변경
    * 문제점: HostSelf가 적용되지 않은 2.0.342 버전 이전의 프로그램에서 upgrade시 저장된 호스트정보 삭제됨.
    * reboot/shutdown : [hostwrite -> reboot/shutdown] -> [hostwrite -> reboot/shutdown]
    * upgrade : [upgrade -> hostwrite -> reboot ] -> [hostwrite -> upgrade -> reboot]
    * backup-import: backup-import -> reboot (hostwrite disable)
* backup import시 dhcp-server 설정의 nameserver 미적용 버그 수정
-----
* 2.0.352 - 20181027
 * Host IPPoint장비의 ONOFFLINE상태를 usermode에서 rebuild 
   (system에서 읽은 interface linkstate 참조)
-----
* 2.0.350 - 20181026
 * Host Viewer 추가 (CreateTime, RegTime, LastTime)
-----
* 2.0.349 - 20181026
 * Host 'Long Unused' 필터 
 * Visual Address List에 'Long Unused' IP 주소 표시
 * Host: 부팅시 lasttime 적용(이전버전에서는 lasttime 미적용)
 * Shutdown/Reboot 시 host정보 재저장
-----
* 2.0.342 - 20181022
 * IPPoint장비가 가지고 있는 Interface/VLAN의 정보(H/W ADDRESS, IP, IP6 ADDRESS)를 Host리스트에 표시
 * IPPoint장비의 VLAN설정시 parent Interface의 H/W주소와 VLAN주소가 같지 않게 AUTOGEN하여 생성 및 Editable
 * IPPoint장비가 가지고있는 Interface/VLAN의 정보를 주기적으로 업데이트
-----
* 2.0.333 - 20181018
 * WEB환경에서 host 삭제시 multiple 하게 지울수 있게 selectable checkbox 지원
-----
* 2.0.331 - 20181017
 * host delete후 iplist에 대하여 arps보내기
-----
* 2.0.330 - 20181016
 * IP충돌방지 옵션이 되어있는 장비(A)의 IP주소를 임의의 장비(B)가 사용할경우: A장비 OFF, B장비 ON일 경우 IPPoint장비에서 대신 응답
-----
* 2.0.327 - 20181016
 * Visual Address List (WEB) 추가 : 사용/미사용 IP리스트 보기 
-----
* 2.0.326 - 20181008
 * hostaction-state: wait -> ready
-----
* 2.0.325 - 20181005
 * host의 (IP|IP6)action에 wait state 추가
-----
* 2.0.324 - 20181004 : 
 * 차단메세지 보낼때 offline호스트에 대한 메세지 전송 skip
 * send GARP -> send ARP(해당 네트워크대역의 호스트에게) when ipcollision


