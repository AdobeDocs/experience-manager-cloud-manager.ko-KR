---
title: 2019.8.0 릴리스 노트
seo-title: AEM Cloud Manager 2019.8.0용 릴리스 노트
description: Cloud Manager 릴리스 2019.8.0에 대한 정보를 보려면 이 페이지를 따르십시오.
seo-description: AEM Cloud Manager 릴리스 2019.8.0에 대한 정보를 보려면 이 페이지를 따르십시오.
feature: 릴리스 정보
exl-id: 9b3da506-76f1-439f-8de0-a5e2ee88b979
source-git-commit: 43bb3c477ef9c1ce178509b8180479d7616edc66
workflow-type: tm+mt
source-wordcount: '225'
ht-degree: 6%

---

# 2019.8.0 릴리스 노트 {#release-notes-for}

[!UICONTROL Cloud Manager] 2019.8.0 릴리스에는 선택적 콘텐츠 패키지에 대한 지원이 추가되며, 빌드 성능을 향상시키고, 다양한 사소한 버그가 수정되었습니다.

## 릴리스 날짜 {#release-date}

[!UICONTROL Cloud Manager] 버전 2019.8.0의 출시일은 2019년 8월 19일입니다.

## 새로운 기능 {#whats-new}

* [Adobe I/O CLI](https://github.com/adobe/aio-cli-plugin-cloudmanager)에서 제공하는 Cloud Manager API에 대한 새 명령줄 인터페이스.
* 빌드에서 생성한 특정 컨텐츠 패키지는 건너뛴 것으로 선언할 수 있으며 배포되지 않습니다. 자세한 내용은 [컨텐츠 패키지 건너뛰기](/help/using/setting-up-project.md#skipping-content-packages)를 참조하십시오.
* 일부 불필요한 네트워크 요청을 방지하기 위해 빌드 컨테이너에 미리 로드된 종속성 세트가 다시 작성되었습니다.
* 잘못 구성된 특정 프로그램에 대한 개요 페이지의 메시지가 개선되었습니다.

## 버그 수정 {#bug-fixes}

* SLA 보고서에 액세스할 때 기본값은 2019년이 아니라 2018년입니다.
* 긴 환경 이름의 경우 보고서 화면의 환경 선택기 크기가 제대로 증가하지 않았습니다.
* Sling 재작성기 구성 요소를 사용할 때 ***ConfigAndInstallShouldOnlyContainOsgiNodes*** 코드 품질 규칙이 긍정 오류(false positive)를 생성했습니다.
* ***ConfigAndInstallShouldOnlyContainOsgiNodes*** 코드 품질 규칙이 흔하지 않은 특정 경로 구조에 대해 긍정 오류(false positive)를 생성했습니다.
* 자산 전용 고객이 AEM 환경으로 일관되게 이동하지 못했을 수 있습니다.
* 분기 및 프로젝트 만들기 대화 상자가 다른 브라우저에서 다르게 렌더링되었습니다.
