# README

## Tomcat8 Server Template

### Redhat 계열 Linux OS(64Bit)에서 활용 가능한 Tomcat8 Template

* JVM Option Tuned
* APR Connector 적용
* JDBC Driver Library 적용: Oracle/MySQL/MariaDB/PostgreSQL

1. 계정 만들기
Tomcat 서버를 설치하고 실행할 계정을 만들어야 한다.<br>
예) wasadm
<br>
2. Create Source & Log Directory<br>
* APP_LONG_NAME: 각 Java 프로젝트 이름과 동일<br>
* SERVER_ID: '응용 프로그램 약어'_'포트' (ex> API G/W Service = apigw_8080)<br>
<br>
  mkdir -p /apps/wasadm/APP_LONG_NAME/applications<br>
<br>
  mkdir -p /logs/wasadm/tomcat8/servers/SERVER_ID/hdump<br>
  mkdir -p /logs/wasadm/tomcat8/servers/SERVER_ID/nohup<br>
  mkdir -p /logs/wasadm/tomcat8/servers/SERVER_ID/gclog<br>
<br>
3. Create Tomcat Engine Directory & Template 압축 해제<br>
  mkdir -p /servers/wasadm/tomcat8/servers/SERVER_ID<br>
  Template 압축해제 --> 'template' 디렉터리 생성 --> 'template' 디렉터리의 모든 파일을 '/servers/wasadm/tomcat8/servers/SERVER_ID'에 복사
<br>
<br>
4. Link Log Directory<br>
  cd /servers/wasadm/tomcat8/servers/SERVER_ID<br>
  ln -s /logs/wasadm/tomcat8/servers/SERVER_ID logs<br>
<br>
5. Please correct the following files:<br>
(응용 프로그램 환경변수 및 설치 경로)<br>
  vi env.sh
<br>
<br>
6. Please check the following files:<br>
(Tomcat 서버 Java 환경변수)<br>
  vi bin/setenv.sh
<br>
<br>
7. Please check the following files:<br>
(Tomcat 서버 DB 연동 환경설정: 적용 DB에 따라 Driver 속성을 변경한다)<br>
('lib/datasource': 기본제공 JDBC 라이브러리 경로)<br>
  vi conf/Catalina/localhost/ROOT.xml
<br>
<br>
8. Source Deploy to Application Archive Directory
Copy ROOT.war to /apps/wasadm/APP_LONG_NAME/applications/
<br>
<br>
9. 시작/중단<br>
start.sh (기동)
<br>
stop.sh (중단)
<br>
ps.sh (프로세스 확인)
<br>
restart.sh (재기동)
