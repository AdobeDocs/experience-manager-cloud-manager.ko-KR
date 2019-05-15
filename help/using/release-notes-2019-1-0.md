---
title: 2019.1.0 릴리스 노트
seo-title: 2019.1.0 용 AEM Cloud Manager 릴리스 노트
description: Cloud Manager 릴리스 2019.1.0에 대한 정보를 얻으려면 이 페이지를 따르십시오.
seo-description: AEM Cloud Manager 릴리스 2019.1.0에 대한 정보를 얻으려면 이 페이지를 따르십시오.
uuid: 3 AF 5808 F -828 F -4846-BEE 4-1 E 62194 B 48 AD
contentOwner: Jsyal
products: sg_ Experiencemanager/Cloudmanager
topic-tags: 릴리스 노트
discoiquuid: 85 a 1 DCF 3-2 EEF -4 BA 8-B 4 D 1-09 E 4 A 88 C 7 BD 0
translation-type: tm+mt
source-git-commit: 1dfb065c09569f811e5a006d3d74825d3bd7cc8d

---


# 2019.1.0 릴리스 노트 {#release-notes-for}

[!UICONTROL Cloud Manager] 2018.9.0 릴리스에서는 제작 및 코드 품질 단계를 실행하는 추가 파이프라인 유형뿐만 아니라, 제작 및 코드 품질 단계를 실행하는 추가 파이프라인 유형도 추가합니다.

## 릴리스 날짜 {#release-date}

버전 2019.1.0 릴리스 [!UICONTROL Cloud Manager] 날짜는 2019 년 1 월 17 일입니다.

## 새로운 기능 {#whats-new}

* AEM 자산의 성능 테스트에 대한 지원을 추가했습니다. 자세한 내용은 [CI/CD 파이프라인](configuring-pipeline.md)구성을 참조하십시오.
* 제작 및 코드 품질 단계 및 비프로덕션 환경에 배포하는 파이프라인만 실행하는 파이프라인에 대한 지원을 추가했습니다. 자세한 내용은 **CI/CD 파이프라인 구성에서 비제작 및 코드 품질 전용 파이프라인** [섹션을](configuring-pipeline.md) 참조하십시오.
* 빌드 환경에서 사용자 지정 환경 변수에 대한 지원을 추가했습니다. 자세한 내용은 [AEM 애플리케이션 프로젝트](create-an-application-project.md) 만들기를 참조하십시오.
* 스테이지 또는 프로덕션 환경이 여러 개인 고객의 경우 프로덕션 파이프라인의 일부로 배포할 환경이 프로덕션 파이프라인의 일부로 선택되면 CI/CD [파이프라인](configuring-pipeline.md) 페이지를 구성할 수 있습니다.
* HTTXT 2 DBM 이 컨테이너 컨테이너에 추가되었습니다.
* 모든 도움말 메뉴 항목 새 탭을 엽니다.

## 버그 수정 {#bug-fixes}

* 프로그램을 편집하는 동안 모든 페이지 세트를 선택 해제할 수 있었습니다.
* 승인 단계에 제목이 잘못 지정되었습니다.
* 경우에 따라 프로그램 로고가 잘못 매트되었습니다.
* Dispatcher 구성 패키지만 빌드하면 배포 단계가 실패합니다.
* Cold Standby 인스턴스가 포함된 환경이 제대로 처리되지 않았습니다.
* 일부 종료된 프로그램이 프로그램 전환기에 나타났습니다.
* 파이프라인이 편집되는 동안 새 분기를 Git 리포지토리에 추가하면 즉시 선택 가능하지 않았을 수 있습니다.
* 일부 화면에서 도움말 메뉴의 Developer Connection 아이콘이 보이지 않았습니다.
* Dispatcher 플러시 구성 대화 상자에서 탭 키가 제대로 처리되지 않았습니다.

## 알려진 문제 {#known-issues}

* 자산, KPI 설정이 아닌 사이트가 있는 프로그램을 열면 모든 사용자는 **설정 프로그램** 단추와 함께 동작 카드 호출을 볼 수 있습니다. 하지만 비즈니스 소유자 역할의 사용자만 실제로 **설정 프로그램** 단추를 클릭할 수 있습니다.