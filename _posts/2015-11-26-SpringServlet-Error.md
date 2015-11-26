---
layout: post
title: 스프링오류-JSP compile 관련
---



>org.apache.jasper.JasperException: java.lang.ClassNotFoundException: org.apache.jsp.WEB_002dINF.pages.hello_jsp
org.apache.jasper.servlet.JspServletWrapper.getServlet(JspServletWrapper.java:176)
org.apache.jasper.servlet.JspServletWrapper.service(JspServletWrapper.java:375)
org.apache.jasper.servlet.JspServlet.serviceJspFile(JspServlet.java:396)
org.apache.jasper.servlet.JspServlet.service(JspServlet.java:340)
javax.servlet.http.HttpServlet.service(HttpServlet.java:729)
org.apache.tomcat.websocket.server.WsFilter.doFilter(WsFilter.java:52)
org.springframework.web.servlet.view.InternalResourceView.renderMergedOutputModel(InternalResourceView.java:172)
org.springframework.web.servlet.view.AbstractView.render(AbstractView.java:303)
org.springframework.web.servlet.DispatcherServlet.render(DispatcherServlet.java:1228)
org.springframework.web.servlet.DispatcherServlet.processDispatchResult(DispatcherServlet.java:1011)
org.springframework.web.servlet.DispatcherServlet.doDispatch(DispatcherServlet.java:955)
org.springframework.web.servlet.DispatcherServlet.doService(DispatcherServlet.java:877)
org.springframework.web.servlet.FrameworkServlet.processRequest(FrameworkServlet.java:966)
org.springframework.web.servlet.FrameworkServlet.doGet(FrameworkServlet.java:857)
javax.servlet.http.HttpServlet.service(HttpServlet.java:622)
org.springframework.web.servlet.FrameworkServlet.service(FrameworkServlet.java:842)
javax.servlet.http.HttpServlet.service(HttpServlet.java:729)
org.apache.tomcat.websocket.server.WsFilter.doFilter(WsFilter.java:52)


**Spring MVC 프로젝트**에서 정상적인 설정에도 불구하고 위와 같은 오류가 날 때가 있다.


의존성 라이브러리들 간에 충돌이거나, servlet version 호환 문제로 JSP파일을 컴파일 하지 못하거나, 찾지 못해 생기는 오류로 결론을 내렸다.


pom.xml, 즉 메이븐 디펜던시에 아래 내용을 추가해주는 것과 같이 최신 버전의 서블릿 API를 추가해주면 된다.

~~~c
<dependency>
    <groupId>javax.servlet</groupId>
    <artifactId>javax.servlet-api</artifactId>
    <version>3.1.0</version>
</dependency>
~~~
