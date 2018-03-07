---
layout: default
title: "JHipster 최신 버전으로 프로젝트 생성하기"
tags: interface trying
---

## JHipster 최신 버전으로 프로젝트 생성하기

1. generator-jhipster 설치

    기존 설치되어있는 jhipster 가 아닌, 최신 소스로 깃헙에서 받아와 yarn에 등록해 사용해야한다.
	git clone https://github.com/jhipster/generator-jhipster.git
	cd generator-jhipster
	yarn global remove generator-jhipster
	yarn global add D:\mnt\work_other\generator-jhipster

2. 프로젝트 디렉토리 생성

	cd mybackend

3. 프로젝트 generation

	yarn jhipster --experimental
        (아래는 차례대로 직접 선택 필요)
        Monolithic application
        mybackend
        info.mybackend
        No
        OAuth2/OIDC...
        SQL (H2, MySQL, MariaDB, PostgreSQL, Oracle, MSSQL)
        MySQL
        H2 with disk-based persistence
        Yes, with the Ehcache implementation (local cache, for a single node)
        Yes
        Maven
        WebSockets using Spring Websocket, API first development using swagger-codegen
        Angular 5 (만약 최신버전이 아니라면, Angular 4가 나올 것이다)
        Yes
        Yes
        English
        korean
        Gatling, Protractor
        No

4. 설명

    프로젝트가 생성되었을 것이다.
    Pom.xml은 백엔드, package.json은 프론트엔드라고 생각하면 된다.
    소스코드는 src에 다 들어있다.
    메이븐에서는 java, resources 폴더를 사용하고, 나머지 docker와 webapp은 jhipster에서 만들었고, 사용된다.

    Docker는 컴퓨터의 cpu, 메모리 등의 자원을 나눠 쓸 수 있는 구글에서 만든 것으로, 맥은 최근에 네이티브로 내장, 윈도우도 프로 버전에 내장되어있다.(홈버전에서는 버츄얼 박스를 사용해야 한다)
    리눅스에서 그루핑시켜서, 도커에서 cpu 일부 리소스 일부를 나눠서 쓰는, 커널에서 지원하는 것이다. 리눅스 컨테이너.
    도커는 yml 파일만 있으면 받아와 컨테이너 만들어 줌.
    jhipster 생성 파일 중 dockerfile이라는것은 내 프로젝트를 docker 를 위한 이미지로 만드는 것.
    jhipster는 readme가 잘 적혀있으니 참고.
    maven start 하면 백엔드, yarn 하면 프론트엔드 구동한다.
    도커는 컴포즈로 하면 됨(?)

    소스/resources/conf?/application.yml 인가 들어가보면 아까 선택했던 OAUTH2 때문에 키클록 접속정보가 나온다. 로컬호스트 9080으로 접속함을 알 수 있다.
    도커를 띄우고(인텔리J에서는 도커 플러그인 설치 해야함), 키클록 부터 yml 파일로 도커 이미지를 통해 컨테이너를 생성하여 띄운다.
    띄워 admin/admin으로 접속, jhipster 렐름이 나온다.(만약 버츄얼박스로 띄웠다면, 처음에 jhipster 렐름이 나오지 않는다. 이땐 add 렐름 하여 렐름컨피그(이것도 jhipster가 만들어놔줌) 를 하면 된다.
    처음엔 키클록에 유저가 아무도 없다. 매니지-임포트 에서 users 하면 유저도 읽어오는데, 데모용 키클록은 인메모리 디비라 껏다 키면 사라진다(아, 네이티브 도커는 재가동시 다 물고와서 다시 해준다). 프로덕션에서는 db를 고려해야한다.

    백엔드는 MyBackendApp 실행하면 된다.
    로그인을 해본다.

