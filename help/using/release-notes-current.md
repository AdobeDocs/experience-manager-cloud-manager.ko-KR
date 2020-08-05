---
title: 2020.8.0 릴리스 노트
seo-title: 2020.8.0용 AEM Cloud Manager 릴리스 노트
description: Cloud Manager 릴리스 2020.8.0에 대한 정보를 얻으려면 이 페이지를 따르십시오
seo-description: AEM Cloud Manager 릴리스 2020.8.0에 대한 정보를 얻으려면 이 페이지를 따르십시오
translation-type: tm+mt
source-git-commit: c0881ccf602a14b00b7cc68c3d1fc60e7b6954ed
workflow-type: tm+mt
source-wordcount: '191'
ht-degree: 6%

---

# 2020.8.0 릴리스 노트 {#release-notes-for}

다음 섹션에서는 릴리스 2020.8.0 [!UICONTROL Cloud Manager] 에 대한 일반 릴리스 노트에 대해 간략하게 설명합니다.

## 릴리스 날짜 {#release-date}

버전 2020.8.0 [!UICONTROL Cloud Manager] 의 릴리스 날짜는 2020년 8월 6일입니다.

## 새로운 기능 {#whats-new}

* 사이트 성능 테스트는 이제 선택적 인증 사용을 지원합니다.

   AEM Sites 성능 테스트 [를 인증하는](configuring-pipeline.md#authenticated-sites-performance) 방법을 알려면 인증된 사이트 성능 테스트를 참조하십시오.

* 이제 인증 바인딩된 개인 마웬 리포지토리가 지원됩니다.

## 버그 수정 {#bug-fixes}

* 불필요하고 불필요한 일부 SonarQube 플러그인이 코드 품질 스캐닝의 일부로 실행되었습니다.

* 파이프라인 실행 페이지에서 분기 이름의 형식이 잘못되었습니다.

* 단일 게시, 단일 디스패처 및 콜드 대기 작성자가 있는 토폴로지 배포 시 디스패처가 로드 밸런서에서 잘못 제거되었습니다.

* 경우에 따라 파이프라인 집행이 완료되었다고 기록되지 않아 파이프라인의 새로운 처형이 방지되는 경우도 있습니다.

* 가끔 내부 통신 문제로 인해 파이프라인 *실행이* 중단될 수 있습니다.

* 프로그램 카드에 대한 도구 설명이 일관되게 올바르지 않습니다.

* 개요 페이지에 색상 불일치가 있습니다.

