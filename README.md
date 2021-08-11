# news_crawling
-------
뉴스기사를 스크랩하고, 해당 뉴스 내용을 자동으로 분류 및 요약 할 수 있는 프로그램을 위한 리포지토리입니다.

현재 개발 진행중이고, 단계는 다음과 같습니다.

> 1. 뉴스기사 크롤링 클래스, DB 저장소 확정 및 배포

> 2. NLP 를 이용한 분류 작업 진행

> 3. 주요내용 요약 알고리즘 적용

> 4. CD : smart factory 키워드로 테스트 적용     

## 패키지 버전
--------
1. python : 3.8.5
2. goose3
3. requests
4. feedparser

## 버전 관리
------
### __21-08-11__

* 관심사 분리
> 기존 다양한 키워드의 기사들을 한번에 파싱해온 결과 테이블이 길어지는 문제가 발견됨     
> 따라서 메인 키워드(테이블로 표시), 추가 키워드(뉴스 링크로 전달) 메소드 분리 적용 완료
> HTML 에 추가 할 수 있는 형태로 변경 완료    

## 기초 상식
-------
### RSS 란?
Really Simple Syndication 또는 Rish Site Summary 라고 부른다.
뉴스 사이트가 있을때, 매일 방문해서 재미있는 새로운 기사가 있는지 확인하는 것은 매우 번거롭다. 특히 새 기사가 메일 또는 정기적으로 올라오는 것이 아니라 불규칙 할 때는 더욱 심할 것이다.

그 사이트를 직접 방문하지 않고, 새 기사들만 자신의 컴퓨터로 "배달" 될 수 있다면 굉장히 편리할 것이다.

RSS 라는 사이트 피드를 통해 새 기사들의 제목, 링크, 날짜 등 대표 데이터들만 뽑아서 하나의 파일로 만들어 놓을 수 있다.

또한 각 사이트들에서 제공하는 RSS 파일 주소만 수집하여 확인하면, 자신의 취향에 맞는 새로운 읽을 거리를 쉽게 찾아서 읽을 수 있다.

그러나 모든 사이트가 RSS 를 제공하는 것은 아니다. 보통 `뉴스형` `블로그형` 사이트에서 사용하는 방식이다.

일반적으로 `XML 기반의 문서 포맷` 으로 이루어져 있다.

## Goolgle News Crawling
------
일반적으로 웹패이지에서 개발자 도구를 이용해 백엔드 서비스를 후킹해서 스크랩해온다.
구체적으로 requests 모듈을 사용해서 html 을 가져오고, bueatiful soup를 이용해 dom tree를 가져오는 방법이 널리 알려져있다.

구글은 공식적인 방법으로 가져올 수가 있다. 
[구글뉴스](https://news.google.com/search?q=%EC%8A%A4%EB%A7%88%ED%8A%B8%ED%8C%A9%ED%86%A0%EB%A6%AC&hl=ko&gl=KR&ceid=KR%3Ako)

위 링크를 접속해보면 뉴스 테이블이 따로 존재하고, 위 URI의 쿼리스트링을 조작하여 우리가 원하는 데이터랄 가져올 수 있다. 뿐만 아니라 


### requests 란?
HTTP 통신은 요청(Request) 와 응답(Response)로 이루어져있다. 클라이언트가 HTTP request 를 보내면 서버는 HTTP response 를 보내는 구조이다.

request 는 크게 3가지로 구성되어 있다.
1. Start line
> 말 그대로 HTTP request 의 초기 라인
> HTTP Method : 해당 요청이 의도한 action 정의, Get, Post, Put, Delete, Options...
> Request target : uri
> HTTP version : 1.0, 1.1, 2.0 등을 명시

2. Headers
> request 의 additional information : 바디의 총길이.. 등
> key : value 로 구성
> 3가지 구성 (General headers + Request headers, Entity headers)
> Host : 호스트의 uri
> User-Agent : 요청을 보내는 클라이언트의 정보
> Accept : response 타입
> Connection : 커넥션 유지 여뷰
> Content-Type : body message 의 타입
> Content-Length : body 길이..

3. Body
> post, put.. 메서드에서 사용하며 보통 JSON, XML 과 같은 통신 마크업(맵) 정보가 담겨있음