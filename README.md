# ippoint

# Changelog
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


