# ippoint

# Changelog


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


