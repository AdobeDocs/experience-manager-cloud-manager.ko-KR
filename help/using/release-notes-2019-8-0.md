---
title: 2019.8.0 릴리스 노트
seo-title: 2019.8.0 용 AEM Cloud Manager 릴리스 노트
description: Cloud Manager 릴리스 2019.8.0에 대한 정보를 얻으려면 이 페이지를 따르십시오.
seo-description: AEM Cloud Manager 릴리스 2019.8.0에 대한 정보를 얻으려면 이 페이지를 따르십시오.
translation-type: tm+mt
source-git-commit: 548d18f251cf8c4c827d2208fec04cde235ce731

---

# 2019.8.0 릴리스 노트 {#release-notes-for}

[!UICONTROL Cloud Manager] 2019.8.0 릴리스에서는 선택적 빌드 컨텐츠 패키지에 대한 지원이 추가되고, 빌드 성능이 개선되었으며, 사소한 버그가 수정됩니다.

## 릴리스 날짜 {#release-date}

버전 2019.8.0 릴리스 [!UICONTROL Cloud Manager] 날짜는 2019 년 8 월 19 일입니다.

## 새로운 기능 {#whats-new}

* Adobe I/O CLI 기반의 클라우드 관리자 API에 대한 새로운 명령줄 [인터페이스](https://github.com/adobe/aio-cli-plugin-cloudmanager)
* 빌드에 의해 만들어진 특정 컨텐츠 패키지는 Skippable로 선언될 수 있으며 배포되지 않습니다. 자세한 내용은 ***AEM 애플리케이션*** 프로젝트 [만들기에서 콘텐츠 패키지 건너뛰기 섹션을](create-an-application-project.md) 참조하십시오.
* 일부 불필요한 네트워크 요청이 발생하지 않도록 빌드 컨테이너의 미리 로드된 종속성 집합이 수정되었습니다.
* 잘못 구성된 특정 프로그램에 대한 개요 페이지의 메시지가 개선되었습니다.

## 버그 수정 {#bug-fixes}

* SLA 보고서에 액세스할 때 기본 년은 2019 년이 아닌 2018 이었습니다.
* 긴 환경 이름의 경우 보고서 화면의 환경 선택기에 크기가 제대로 표시되지 않았습니다.
* sling rewriter 구성 요소가 사용될 때 ***configandinstallshouldonlycontainosginodes*** 코드 품질 규칙이 잘못된 양을 생성했습니다.
* ***Configandinstallshouldonlycontainosginodes*** 코드 품질 규칙은 특수한 경로 구조에 대한 잘못된 Positives를 만들었습니다.
* 에셋 전용 고객은 지속적으로 AEM 환경으로 이동할 수 없었습니다.
* [!UICONTROL Create a Branch and Project] 대화 상자는 서로 다른 브라우저에서 다르게 렌더링됩니다.
