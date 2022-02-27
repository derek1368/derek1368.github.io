---
title:  "Apache/Tomact Error 처리법"
excerpt: "Apache/Tomcat Error 처리법"

categories:
  - network
tags:
  - network
last_modified_at: 2021-06-23T08:06:00-05:00
toc: true
toc_label: "목차"
toc_icon: "cog"
toc_sticky: true
---
## 1. Apache
- HTTP 웹서버로서 아파치재단에서 관리하는 Web Server
- 정적인 웹의 대한 것을 처리함
- 172.483.12.1:8080 에서 172.483.12.1이 apache  

## 2. Tomcat 
- 톰캣은 아파치 재단의 Web Application Server로서, Java servlet을 실행시키고 JSP code가 포함됨
- 데이터를 송수신하여 바꿔주는 웹의 동적인 활동을 처리함  
- 172.483.12.1:8080/v2 에서 8080이 tomcat  

※ server start 시 가장 먼저 Web.xml의 내용을 읽음. web.xml을 기반으로 서버가 돌아가기 위해 필요한 내용 읽어들인다.  
## 3. Apache/Tomcat 관계
Client에서 Request/Response를 하는 역할이 Servlet Container임.    
![](/assets/images/backend/apacheTomcat.png){: .align-center} 

## 4. Apache/Tomcat 애러 처리
### Apache(Debian계열)
1. 아래의 경로의 `000-default.conf` 수정필요(/etc/apache2/sites-enabled)
2. 사진과 같이 각 애러번호에 대한 document 혹은 문구 적어줌
![](/assets/images/backend/apache_info_solve.png){: .align-center} 
3. html화면을 넣고 싶으면 아래의 이미지와 같이 경로설정 필요(상위경로: /var/www/html/)
![](/assets/images/backend/apache_info_solve2.png){: .align-center} 
4. Root 계정을 통해 apache 재실행 (명령어: service apache2 restart) 



### Tomcat
1. 아래와 사진과 같이 tomcat의 정보를 숨기기 위해 server.xml 파일을 수정필요
![](/assets/images/backend/tomcat_info_prob.png){: .align-center} 
2. <host></host> 태그 안에 아래의 문구 입력  
```JAVA
	<Valve className="org.apache.catalina.valves.ErrorReportValve" showReport="false" showServerInfo="false"/>
```
![](/assets/images/backend/tomcat_info_solve.png){: .align-center} 

3. Tomcat 재실행
4. 아래와 같이 Tomcat의 정보를 숨김
![](/assets/images/backend/tomcat_info_result.png){: .align-center} 