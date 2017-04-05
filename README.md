# README

## Tomcat8 Server Template

### Redhat 계열 Linux OS(64Bit)에서 활용 가능한 Tomcat8 Template

- APR Connector
- 

0. 계정 만들기
Tomcat 서버를 설치하고 실행할 계정을 만들어야 한다.
예) wasadm
<br>
1. Create Source & Log Directory
* APP_LONG_NAME: 각 Java 프로젝트 이름과 동일
* SERVER_ID: '응용 프로그램 약어'_'포트' (ex> Mobile Office Service = mosvc_8080)
<br>
  mkdir -p /srcw001/wasadm/APP_LONG_NAME/applications
<br>
  mkdir -p /logs001/wasadm/tomcat8/servers/SERVER_ID/hdump
  mkdir -p /logs001/wasadm/tomcat8/servers/SERVER_ID/nohup
  mkdir -p /logs001/wasadm/tomcat8/servers/SERVER_ID/gclog
<br>
<br>
2. Create Tomcat Engine Directory & Template 압축 해제
  mkdir -p /engn001/wasadm/tomcat8/servers/SERVER_ID
  Template 압축해제 --> 'template' 디렉터리 생성 --> 'template' 디렉터리의 모든 파일을 '/engn001/wasadm/tomcat8/servers/SERVER_ID'에 복사
<br>
<br>
3. Link Log Directory
  cd /engn001/wasadm/tomcat8/servers/SERVER_ID
  ln -s /logs001/wasadm/tomcat8/servers/SERVER_ID logs
<br>
<br>
4. Please correct the following files:
(응용 프로그램 환경변수 및 설치 경로)
  vi env.sh
<br>
<br>
5. Please check the following files:
(Tomcat 서버 Java 환경변수)
  vi bin/setenv.sh
<br>
<br>
6. Please check the following files:
(Tomcat 서버 DB 연동 환경설정)
  vi conf/Catalina/localhost/ROOT.xml
<br>
<br>
7. Source Deploy to Application Archive Directory
Copy ROOT.war to /srcw001/emsadm/APP_LONG_NAME/applications/
<br>
<br>
8. 시작/중단
start.sh (기동)
<br>
stop.sh (중단)
<br>
ps.sh (프로세스 확인)
<br>
restart.sh (재기동)
