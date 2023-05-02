# DNS 와 작동원리
### DNS
도메인 네임 시스템(Domain Name System , DNS)은 호스트의 도메인네임(wwww.example.com)을 네트워크주소(192.1681.0)로 변환하거나, 그 반대역할을 수행하는 시스템이다
<ul>
<li>DNS 시스템은 이름과 숫자 간의 매핑을 관리하여 마치 전화번호부와 같은 기능을 한다.
<li>DNS 서버는 사용자가 도멩니 이름을 브라우저에 입력하면, 사용자를 어떤 서버에 연결할 것인지 제어한다. 이러한 요청을 쿼리 라고 한다.
</ul>

## DNS 기본 동작 설명
![img](https://velog.velcdn.com/images%2Fdoomchit_3%2Fpost%2F77b59702-69d4-433a-81bc-52d93aa75e83%2FNetmanias.2011.12.12-DNS_Basic.gif)
<ol>
<li>위의 그림과 같이 PC 브라우저에서 www.naver.com 을 입력한다. 그러면 PC는 미리 설정되어 있는 DNS (단말에 설정되어 있는 이 DNS를 Local DNS라 부름, 위에서는 203.248.252.2) 에게 "www.naver.com 이라는 hostname" 에 대한 IP 주소를 요청한다.</li> <br/>
<li>Local DNS 에는 "www.naver.com 의 IP 주소"가 있을 수도 없을 수도 있다. 만약 있다면 Local DNS 가 바로 PC에 IP 주소를 주고 끝난다. 하지만 본 설명에서는 Local DNS에 "www.naver.com 의 IP 주소"가 없다고 가정 한다.
</li><br/>
<li>Local DNS는 이제 "www.naver.com 의 IP 주소"를 찾아내기 위해 다른 DNS 서버들과 통신(DNS 메시지)을 시작한다. 먼저 Root DNS 서버에게 "www.naver.com 의 IP 주소"를 요청하며, 이를 위해 각 Local DNS 서버에는 Root DNS 서버의 정보 (IP 주소)가 미리 설정되어 있어야 한다. Root DNS 서버 는 전세계에 13대가 구축되어 있다. 미국에 10대, 일본/네덜란드/노르웨이에 각 1대씩이며, 우리나라의 경우 Root DNS 서버가 존재하지는 않지만 Root DNS 서버에 대한 미러 서버를 3대 운용하고 있다고 한다.</li><br/>
<li>Root DNS 서버 는 "www.naver.com 의 IP 주소" 를 찾을 수 없어 Local DNS 서버에게 "www.naver.com 의 IP 주소 찾을 수 없음. 다른 DNS 서버에게 물어봐" 라고 응답을 한다.

</li><br/>
<li>이 다른 DNS 서버는 com 도메인 을 관리하는 DNS 서버이다.

</li><br/>
<li>이제 Local DNS 서버는 com 도메인을 관리하는 DNS 서버에 다시 www.naver.com에 대한 IP 주소를 요청한다.

</li><br/>
<li>com 도메인을 관리하는 DNS 서버에도 해당 정보가 없으면, Local DNS 서버에게 "www.naver.com 의 IP 주소 찾을 수 없음. 다른 DNS 서버에게 물어봐" 라고 응답을 합니다. 이 다른 DNS 서버는 naver.com 도메인을 관리하는 DNS 서버 이다.

</li><br/>
<li>이제 Local DNS 서버는 naver.com DNS 서버에게 다시 "www.naver.com 의 IP 주소" 를 요청한다.

</li><br/>
<li>naver.com DNS 서버 에는 "www.naver.com 의 IP 주소" 가 있다. 그래서 Local DNS 서버에게 "www.naver.com에 대한 IP 주소는 222.122.195.6" 라는 응답을 한다.

</li><br/>
<li>이를 수신한 Local DNS는 www.naver.com 의 IP 주소를 캐싱을 하고 이후 다른 요청이 있을시 응답할 수 있도록 IP 주소 정보를 단말(PC)에 전달해 줍니다.

</li><br/>
</ol>