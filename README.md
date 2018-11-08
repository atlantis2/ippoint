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
-----
# Changelog
* 2.0.356 - 20181108
* 차단 호스트 IP(IP6)변경시 일시적으로 정상동작
    * 원인 : ip(6)block요소 서치시 target IP(6)로 조회하여 문제 발생 
    * 해결책: ip(6)block요소 서치시 ip(6)block요소의 src/dst에 대한 주소로 서치
* upgrade/reboot/shutdown시 host write 순서 변경
    * 문제점: HostSelf가 적용되지 않은 2.0.342 버전 이전의 프로그램에서 upgrade시 저장된 호스트정보 삭제됨.
    * reboot/shutdown : [hostwrite -> reboot/shutdown] -> [hostwrite -> reboot/shutdown]
    * upgrade : [upgrade -> hostwrite -> reboot ] -> [hostwrite -> upgrade -> reboot]
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


