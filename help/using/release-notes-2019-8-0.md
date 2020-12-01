---
title: 2019.8.0 릴리스 노트
seo-title: AEM Cloud Manager 2019.8.0용 릴리스 노트
description: Cloud Manager 릴리스 2019.8.0에 대한 정보를 얻으려면 이 페이지를 따르십시오.
seo-description: AEM Cloud Manager 릴리스 2019.8.0에 대한 정보를 얻으려면 이 페이지를 따르십시오.
translation-type: tm+mt
source-git-commit: 2ada697ca21acd0c73dbce2bce3e9481ac50272c
workflow-type: tm+mt
source-wordcount: '223'
ht-degree: 5%

---

# 2019.8.0 릴리스 노트 {#release-notes-for}

[!UICONTROL Cloud Manager] 2019.8.0 릴리스는 선택적 빌드 컨텐츠 패키지에 대한 지원을 추가하고, 빌드 성능을 향상시키고, 다양한 사소한 버그를 수정합니다.

## 릴리스 날짜 {#release-date}

[!UICONTROL Cloud Manager] 버전 2019.8.0의 릴리스 날짜는 2019년 8월 19일입니다.

## 새로운 기능 {#whats-new}

* Cloud Manager API에 대한 새 명령줄 인터페이스(예: [Adobe I/O CLI](https://github.com/adobe/aio-cli-plugin-cloudmanager) 제공)
* 빌드에 의해 생성된 특정 콘텐츠 패키지는 생략된 것으로 선언되며 배포되지 않습니다. 자세한 내용은 [콘텐츠 패키지 건너뛰기](/help/using/setting-up-project.md#skipping-content-packages)를 참조하십시오.
* 빌드 컨테이너의 미리 로드된 종속성 집합이 불필요한 네트워크 요청을 방지하기 위해 다시 작업되었습니다.
* 잘못 구성된 특정 프로그램에 대한 개요 페이지의 메시지가 개선되었습니다.

## 버그 수정 {#bug-fixes}

* SLA 보고서에 액세스할 때 기본값은 2019가 아니라 2018년입니다.
* 긴 환경 이름의 경우 보고서 화면의 환경 선택기의 크기가 제대로 증가하지 않았습니다.
* Sling Rewriter 구성 요소를 사용할 때 ***ConfigAndInstallShouldOnlyContainOsgiNodes*** 코드 품질 규칙이 잘못된 양수를 생성했습니다.
* ***ConfigAndInstallShouldOnlyContainOsgiNodes*** 코드 품질 규칙은 일반적이지 않은 특정 경로 구조에 대해 잘못된 양수를 생성했습니다.
* 자산 전용 고객은 AEM 환경으로 일관되게 이동할 수 없었습니다.
* 분기 만들기 및 프로젝트 대화 상자가 여러 브라우저에서 다르게 렌더링되었습니다.
