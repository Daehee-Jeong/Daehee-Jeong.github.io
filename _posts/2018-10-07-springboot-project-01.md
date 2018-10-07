---
layout: post
title: Springboot/JPA 프로젝트 - 01 (프로젝트 환경 구성)
categories: [Springboot]
excerpt: ""
comments: true
share: true
tags: [Springboot, JPA]
date: 2018-10-07
---

## 브랜드홈페이지 플랫폼 개발 프로젝트

&nbsp;사내 프로젝트로 브랜드홈페이지를 쉽고 빠르게 생산하기 위한 플랫폼 개발 프로젝트를 시작하게 되었습니다.
&nbsp;기본적으로 **사용자들이 접속하게될 프론트 페이지와, 사이트의 리소스를 관리할 수 있는 관리자 페이지를 개발하는 것**이 프로젝트의 주된 목적입니다.
&nbsp;개발을 위하여 현재 사내에서 PM을 중심으로 라이브코딩 형식의 스터디를 진행하며 기술을 학습하고있으며, 프로토타입을 완성시켜 가는 방향으로 프로젝트를 진행하려고 합니다.
&nbsp;앞으로의 포스팅은 해당 스터디를 진행하면서 배운내용을 정리한 글을 작성하고자 합니다.

<br>

## 개발 스펙

>**Springboot, JPA, MongoDB**, HTML5/CSS3, jQuery

&nbsp;최대한 빠르게 웹프로젝트를 구성하고, 배포를 하기위한 방안으로 **Springboot**를 선택하였습니다. 또한 브랜드홈페이지 구성을 위한 데이터의 형태가 상당히 정형화되어있다는 판단을 내리고 Persistance API 선정을 **JPA**로 하여, 빠르고 손쉬운 구축 및 소스 운영관리를 용이하게 하고자 하였습니다.
&nbsp;이외의 프론트엔드 구성요소로는, 고객의 특성상 매우 낮은 브라우저 버전을 감안하여 **jQuery** 기반의 홈페이지 템플릿을 구매하여 사용하게 되었습니다.
&nbsp;DB에 대해서는 현재 자사에서 Oracle기반의 ERP를 사용중인 상태지만, 브랜드홈페이지는 독립된 프로젝트로 개발될 것을 전제로 **MongoDB**를 적용하기로 하였습니다.
&nbsp;추후에 ERP연계 기능 등으로 Oracle 기반의 DB가 혼용되어야 한다면 이부분에 대해서도 추가적인 경험들에 대해 많이 포스팅이 가능할 것 같습니다.

<br>
<br>

##프로젝트 환경 구성

* 프로젝트 생성: 자바 1.8버전을 설정하였습니다.
![No Image](/assets/20181007/01.png)
<br><br>
* Dependency 설정 01 (Core)
![No Image](/assets/20181007/02.png)
생성자 및 Getter/Setter의 간편한 설정을 위해 Lombok을 추가하였습니다.
<br><br>
* Dependency 설정 02 (Web)
![No Image](/assets/20181007/03.png)
웹프로젝트 구성을 위한 Web, 손쉬운 RestAPI 구축 및 테스팅/확인을 위해 Rest Repositories, Rest Repositories HAL Browser를 추가하였습니다.
<br><br>
* Dependency 설정 03 (Template Engines)
![No Image](/assets/20181007/04.png)
사내 환경에서는 템플릿 엔진으로 jsp가 일반적이었지만, Springboot와 가장 친숙한 Thymeleaf로 설정하여 진행하였습니다.
<br><br>
* Dependency 설정 04 (SQL)
![No Image](/assets/20181007/05.png)
JPA 추가, H2를 추가하여 로컬 테스팅시 활용하기로 하였습니다.
<br><br>
* application.properties 설정
    ``` properties
    # SpringData REST의 기본 context path
    #http://localhost:8080/api
    spring.data.rest.basePath=api
    spring.data.rest.defaultPageSize=10
    # JPA 설정
    spring.jpa.hibernate.ddl-auto=create-drop
    spring.jpa.show-sql=true
    # H2 DB설정
    spring.datasource.url=jdbc:h2:~/test
    #spring.datasource.username=test
    #spring.datasource.password=test
    spring.datasource.driver-class-name=org.h2.Driver
    spring.h2.console.enabled=true
    spring.h2.console.path=/console
    ```
<br>
* [Finish] 를 선택하여 프로젝트 생성 완료 및 [Gradle - bootRun] 을 통해 실행확인을 한다.