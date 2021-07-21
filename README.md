# news_crawling
-------
I make this repository to scrape and make use of NLP.

There're couples of steps to finish this project

1. crawl news material in google, naver, daum, bing...

2. write datasets in excel sheet

3. ...and so on

## 패키지 버전
--------
1. python : 3.8.5
2. goose3
3. requests
4. feedparser

## 기초 상식
-------
__1. RSS 란?__
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