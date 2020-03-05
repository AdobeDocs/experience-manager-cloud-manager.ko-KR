---
title: 2020.3.0 릴리스 노트
seo-title: 2020.3.0용 AEM Cloud Manager 릴리스 노트
description: Cloud Manager 릴리스 2020.3.0에 대한 정보를 얻으려면 이 페이지를 따르십시오
seo-description: AEM Cloud Manager 릴리스 2020.3.0에 대한 정보를 얻으려면 이 페이지를 따르십시오.
translation-type: tm+mt
source-git-commit: 44671d89edad0ccb6ded998b62beb5fa012678e9

---

# 2020.3.0 릴리스 노트 {#release-notes-for}

다음 섹션에서는 릴리스 2020.3.0 [!UICONTROL Cloud Manager] 에 대한 일반 릴리스 노트에 대해 간략하게 설명합니다.

## Release Date {#release-date}

버전 2020.3.0 [!UICONTROL Cloud Manager] 의 릴리스 날짜는 2020년 3월 5일입니다.

## 새로운 기능 {#whats-new}

* 이제 빌드 단계가 실행되는 동안 빌드 단계에 대한 로그를 사용할 수 있습니다.
* 파이프라인 실행 세부 정보 페이지의 메시지 중 일부가 명확히 편집되었습니다.

## 버그 수정 {#bug-fixes}

* 특정 배포 구성으로 인해 배포에 실패한 경우 배포 단계에 대한 로그를 사용할 수 없습니다.
* Managed Services 프로그램의 배포 단계 내에서 특정 오류가 발생하면 후속 실행이 시작되지 않을 수 있습니다.
* 빌드 단계에서 사용되는 임시 SonarQube 인스턴스가 구성된 제한 시간 내에 시작하지 못하는 경우가 있었습니다.
* 특정 프로젝트에서 ResourceResolver *개체를 항상 닫으면* Null 포인터 예외가 발생합니다.그러나 파이프라인 실행에는 영향을 주지 않았습니다.


