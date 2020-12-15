---
title: 2020.5.0 릴리스 노트
seo-title: 2020.5.0용 AEM Cloud Manager 릴리스 노트
description: Cloud Manager 릴리스 2020.5.0에 대한 정보를 얻으려면 이 페이지를 따르십시오.
seo-description: AEM Cloud Manager 릴리스 2020.5.0에 대한 정보를 얻으려면 이 페이지를 따르십시오.
translation-type: tm+mt
source-git-commit: 0652436ec0c1c95d270a06a600424dbfd0140b27
workflow-type: tm+mt
source-wordcount: '187'
ht-degree: 66%

---

# 2020.5.0 릴리스 노트 {#release-notes-for}

다음 섹션에서는 [!UICONTROL Cloud Manager] 릴리스 2020.5.0에 대한 일반 릴리스 노트에 대해 간략하게 설명합니다.

## 릴리스 날짜 {#release-date}

[!UICONTROL Cloud Manager] 버전 2020.5.0의 릴리스 날짜는 2020년 5월 7일입니다.

## 새로운 기능 {#whats-new}

* 고객이 클라우드 서비스로의 마이그레이션을 계획할 때 발생할 수 있는 문제를 식별하는 데 도움이 되는 6개의 추가 코드 품질 규칙이 추가되었습니다.

* 호환성 관련 문제 수를 요약하기 위해 새로운 지표 *Cloud Service 호환성*&#x200B;이 추가되었습니다.

* 활동 페이지 및 파이프라인 실행 목록 API의 성능이 개선되었습니다.

* 이제 코드 품질 로그에 예외에 대한 전체 스택 추적이 포함됩니다.

## 버그 수정 {#bug-fixes}

* 프로덕션 파이프라인이 실행되는 동안 잘못된 카드가 개요 페이지에 표시되었습니다.

* *DontImplementOrExtendProviderTypesPomCheck* 코드 품질 규칙은 경우에 따라 Null 포인터 예외를 생성할 수 있습니다.

* 개요 페이지의 일부 설명서 링크가 제대로 작동하지 않았습니다.

* 개요 페이지의 특정 카드에 개체 이름이 올바로 표시되지 않았습니다.

* 특정 토폴로지 구성에서는 누락된 지표를 보고하는 대신 성능 테스트 단계에서 오류가 생성됩니다.

