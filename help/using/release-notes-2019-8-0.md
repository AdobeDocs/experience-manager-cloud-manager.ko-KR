---
title: 2019.8.0용 릴리스 노트
seo-title: 2019.8.0용 AEM Cloud Manager 릴리스 노트
description: Cloud Manager 릴리스 2019.8.0에 대한 정보를 얻으려면 이 페이지를 따르십시오.
seo-description: AEM Cloud Manager 릴리스 2019.8.0에 대한 정보를 얻으려면 이 페이지를 따르십시오.
translation-type: tm+mt
source-git-commit: 548d18f251cf8c4c827d2208fec04cde235ce731

---

# 2019.8.0용 릴리스 노트 {#release-notes-for}

2019. [!UICONTROL Cloud Manager] 8.0 릴리스에는 선택적 빌드 컨텐츠 패키지에 대한 지원이 추가되어 빌드 성능이 향상되고 다양한 사소한 버그가 수정되었습니다.

## 릴리스 날짜 {#release-date}

버전 2019. [!UICONTROL Cloud Manager] 8.0의 릴리스 날짜는 2019년 8월 19일입니다.

## 새로운 기능 {#whats-new}

* Adobe I/O CLI에서 제공하는 Cloud Manager API에 대한 새로운 [명령줄 인터페이스](https://github.com/adobe/aio-cli-plugin-cloudmanager).
* 빌드에 의해 생성된 특정 컨텐츠 패키지는 확장 가능한 패키지로 선언될 수 있으며 배포되지 않습니다. 자세한 ***내용은 AEM 애플리케이션 프로젝트*** [만들기의 컨텐츠](create-an-application-project.md) 패키지 건너뛰기 섹션을참조하십시오.
* 빌드 컨테이너의 미리 로드된 종속성 집합이 불필요한 네트워크 요청을 방지하기 위해 다시 작동되었습니다.
* 잘못 구성된 특정 프로그램에 대한 개요 페이지의 메시지가 개선되었습니다.

## 버그 수정 {#bug-fixes}

* SLA 보고서에 액세스할 때 기본 연도는 2019년이 아니라 2018년이었습니다.
* 긴 환경 이름의 경우 보고서 화면의 환경 선택기의 크기가 제대로 증가하지 않았습니다.
* ConfigAndInstallShouldOnlyContainOsgiNodes ****** 코드 품질 규칙은 Sling Rewriter 구성 요소를 사용할 때 잘못된 양수를 생성했습니다.
* ConfigAndInstallShouldOnlyContainOsgiNodes ****** 코드 품질 규칙은 일반적이지 않은 특정 경로 구조에 대해 잘못된 양수를 생성했습니다.
* 자산 전용 고객은 AEM 환경으로 일관되게 이동할 수 없었습니다.
* 대화 [!UICONTROL Create a Branch and Project] 상자는 다양한 브라우저에서 다르게 렌더링됩니다.
