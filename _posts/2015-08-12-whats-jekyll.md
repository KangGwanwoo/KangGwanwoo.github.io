---
layout: post
title: GitHub Page와 Jekyll을 가지고 블로그 포스팅하기
---

 

 **블로그**를 시작하는데 있어서 어떤 서비스를 이용해 블로깅을 할 것인가를 오랫동안 고민했었다.<br>
 다음의 [티스토리](www.tistory.com), [네이버블로그](http://section.blog.naver.com/) 같은 가입형 블로그를 쓸 것인가,
 [워드프레스](https://ko.wordpress.org/), [재로보드](http://www.xpressengine.com/) 같은 설치형 블로그를 쓸 것인가,
 둘 다 장단점이 여러가지 있었지만 내가 블로그를 시작하는 목적인 포토폴리오로 이용할 것, 삽질에 대한 기록을 남기는 것 이란 관점에서 
 가볍게 - 확장성 있게 - 블로깅이 가능한 서비스는 위에 서비스들에서는 너무 과한 서비스들 인 것도 같고, 저 서비스들에 정이 가지 않는 가장 큰 이유는
 식상했다. 식상하지 않을려면 여러가지 플러그인을 설치하고 UI를 편집하고 해야됬는데 그 길도 너무 복잡해보였다 !

 **[Jekyll](http://jekyllrb.com/)**은 여러(특히 마크다운) 형태의 텍스트와 테마를 소스로 하여 정적 HTML 웹사이트를 제너레이트하는 툴이다. Ruby 스크립트로 만들어져 있으나, 블로그를 만드는 데에는 루비를 전혀 몰라도 된다. 워드프레스를 사용하여 블로그를 만드는 노력이면 워드프레스보다 훨씬 더 빠르고 보안에도 뛰어난 블로그를 깃허브에 무료로 만들 수 있고, 별도의 페이지를 만들기도 쉽다. 또한, HTML과 CSS에 대한 약간의 지식만 있으면 페이지는 물론 각 포스트마다 다른 레이아웃을 줄 수도 있다. [출처](https://nolboo.github.io/blog/2013/10/15/free-blog-with-github-jekyll/)

 **정적 HTML 웹사이트**는 동적인 서비스(댓글,게시판,회원가입 등)를 제공하지 않는다 라는 의미를 담고있는데 웹 구동원리를 모르는 분들은 이해하기 어려운 말 일 수도 있지 않을까 싶다.
 그러니까 웹 서버에서는 HTML문서를 접속하는 브라우저(사용자)마다 넘겨주는데, 사용자가 주는 동적인...그니까 사용자 마다 다를 수 있는 데이터를 가지고 일련에 프로그래밍적 로직을 거쳐서 커스텀된 HTML문서를 제작하여 제공하는 것이다. 

 그래서 서버에서 미리 제작된 HTML 문서만 제공해 준다면 정적인 HTML 사이트라 할 수 있는데, 그러면 이건 단점만 있는거 아니냐! 라 할 수 있지만 
 신문만 보여주거나, 특정 정보만 사용자에게 제공하고 피드백이 필요 없는 사이트에서는 적합한 구조라 할 수 있다. 왜냐하면 동적인 문서는 동적인 데이터와 그에 맞는 로직을 처리하기 위해서
 추가적인 서버 작업이 필요하기 때문에 서버에 자원을 소모하는 문제가 있기도하고, 구현상에 조금 더 깊은 전문성을 요구하기도 한다.

**[GitHub](www.github.com)**은 Jekyll 방식의 블로그를 무료로 호스팅 해준다.<br>
내가 만든 Jekyll 컨텐츠를 github 저장소를 만들고 push하면 jekyll 엔진을 내장하고 있어 조금의 컴파일 시간이 지나면 바로 호스팅을 해준다. 



> Jekyll is a simple, blog aware, static site generator. It takes a template directory [...] and spits out a complete, static website suitable for serving with Apache or your favorite web server. This is also the engine behind GitHub Pages, which you can use to host your project’s page or blog right here from GitHub.

