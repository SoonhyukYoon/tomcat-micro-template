# README

## Tomcat8 Server Template

### Redhat 계열 Linux OS(64Bit)에서 활용 가능한 Tomcat8 Template

#### Spec

* JVM Option Tuned
* APR Connector 적용
* JDBC Driver Library 탑제: ~/lib/datasource 디렉터리에는 아래와 같은 Lib를 제공한다.
   - MariaDB: mariadb-java-client-1.5.4.jar
   - MySQL: mysql-connector-java-5.1.40.jar
   - PostgreSQL: postgresql-9.4.1211.jre7.jar
   - MS SQL Server: sqljdbc41.jar

#### Installation

1. 계정 만들기

* Tomcat 서버를 설치하고 실행할 계정을 만들어야 한다.
   - 예) wasadm

2. Create Source & Log Directory

* APP_LONG_NAME: 각 Java 프로젝트 이름과 동일
* SERVER_ID: '응용 프로그램 약어'_'포트' (ex> API G/W Service = apigw_8080)
```shell
mkdir -p /srcw001/wasadm/APP_LONG_NAME/applications

mkdir -p /logs001/wasadm/tomcat8/servers/SERVER_ID/hdump
mkdir -p /logs001/wasadm/tomcat8/servers/SERVER_ID/nohup
mkdir -p /logs001/wasadm/tomcat8/servers/SERVER_ID/gclog
```

3. Create Tomcat Engine Directory & Template 압축 해제

```shell
mkdir -p /engn001/wasadm/tomcat8/servers/SERVER_ID
```

* Template 압축해제 --> 'template' 디렉터리 생성 --> 'template' 디렉터리의 모든 파일을 '/engn001/wasadm/tomcat8/servers/SERVER_ID'에 복사

4. Link Log Directory

```shell
cd /engn001/wasadm/tomcat8/servers/SERVER_ID
ln -s /logs001/wasadm/tomcat8/servers/SERVER_ID logs
```

5. Please correct the following files:
```shell
(응용 프로그램 환경변수, 설치 경로, DB 연계 설정-적용 DB에 따라 Driver 속성을 변경한다)
vi env.sh
```

6. Please check the following files:

```shell
(Tomcat 서버 Java 환경변수)
vi bin/setenv.sh
```

7. Please check the following files:

* Tomcat 서버의 응용 프로그램 참조 경로 및 DBCP 상세설정

```shell
vi conf/Catalina/localhost/ROOT.xml
```

8. Source Deploy to Application Archive Directory

* Copy ROOT.war to /srcw001/wasadm/APP_LONG_NAME/applications/

9. 시작/중단

* start.sh (기동)
* stop.sh (중단)
* ps.sh (프로세스 확인)
* restart.sh (재기동)