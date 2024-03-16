# 2.URI - 웹 브라우저

- URI(Uniform Resource Identifier) - 리소스를 식별하는 방법
여기서의 resource : URI로 식별할 수 있는 모든 것
- URI ⇒ Locator, Nam 또는 둘 다 추가로 분류될 수 있다.
    - Locator → URL : 리소스가 있는 위치 지정
    - Nam → URN : 리소스에 이름을 부여
        
        즉 URI 안에 URL, URN이 있는 것
        
- URL, URN
    - 위치(L)는 변할 수 있지만, 이름(N)은 변하지 않음
    - 책의 isbn ⇒ 어떤 책의 URN 이라고 할 수 있다 — 실제 결과가 나오진 X
    - 따라서 URN 이름만으로 실제 리소스를 찾을 수 있는 방법은 보편화 되지 않음
    - URI를 URL과 같은 의미로 본다

- URL 분석 (https://www.google.com/search?q=sugar&hl=ko)
    - scheme://[userinfo@]host[:port][/path][?query][#fragment]
    - scheme : 거의 프로토콜 정보(https)
    호스트명(www.google.com)
    포트 번호(443 → https)
    패스(/search)
    쿼리 파라미터(q=sugar&hl=ko)
    
    - scheme
        - 주로 프로토콜
            - 프로토콜 : 어떤 방식으로 자원에 접근할 것인가 → 약속 규칙(클라이언트와 서버간의 약속) ex)http(80), https(443), ftp 등
            - cf) https는 http에 보안 추가한 것
    - userinfo
        - url 에 사용자 정보 포함해 인증 → 거의 사용X
    - host
        - 도메인명 또는 IP 주소를 직접 사용
    - port
        - 접속 포트, 일반적으로 생략(생략시 http 80, https 443이다)
    - path
        - 리소스 경로(path), 계층적 구조
        - EX) ~.com/members/id/100
    - query (=query parameter)
        - key = value 형태
        - ?로 시작, &로 추가 가능 ex) ?q=sugar&hl=ko
    - fragment
        - html 내부 북마크 등에 사용 - html 내부에서 중간으로 이동하고 싶을 때 → 한 화면 안에서 스크롤 위치를 이동할 때
        - 서버 전송 정보 아님

- 웹 브라우저 요청 흐름
    - 웹 브라우저가 HTTP 요청 메시지 생성 (GET /search?q=sugar ~ HTTP/1.1 Host:www.google.com)
    - 요청 메시지는 TCP/IP패킷 안에 들어가고 패킷은 서버에 전달된다
    - 서버는 응답 패킷을 다시 웹 브라우저에게 전달한다 (HTTP/1.1 200 OK ~)
    (웹 서버에서 응답 메시지를 만들어 낸다)
    - HTTP 메시지 전송
        
       ![http_2](https://github.com/RCNR/About-HTTP/assets/160254953/f16a195f-35ad-4f51-b4f3-987293b2b843)
        
    - 패킷(TCP/IP패킷) 안에는 출발지 IP, PORT
    목적지 IP ,PORT
    **전송 데이터 가 들어있다**
    - 패킷 생성
        
        ![http_1](https://github.com/RCNR/About-HTTP/assets/160254953/f62deaab-196b-4eb1-a14c-3aa81d1f3afb)
        
        이 요청 패킷을 웹 브라우저가 어떤 서버로 전달한다
        그럼 서버는 HTTP 응답 메시지와 함께 응답 패킷을 전달한다.
