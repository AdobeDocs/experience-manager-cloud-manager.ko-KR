---
title: 2018.7.0 릴리스 노트
seo-title: 2018.7.0 릴리스 노트
description: Cloud Manager 릴리스 2018.7.0에 대한 자세한 내용
seo-description: Cloud Manager 릴리스 2018.7.0에 대한 정보를 얻으려면 이 페이지를 따르십시오.
uuid: d7b49e32-01dc-48ce-b744-e6a806fbdd8a
contentOwner: jsyal
topic-tags: release-notes
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
discoiquuid: b64bf9ab-27ed-4f33-adc8-d73d34094f1b
translation-type: tm+mt
source-git-commit: 2dda85baa5e7ed9bfd8933df3580ec6fc3c210fd
workflow-type: tm+mt
source-wordcount: '354'
ht-degree: 12%

---


# 2018.7.0 릴리스 노트 {#release-notes-for}

다음 섹션에서는 *자동 처리* 기능을 제공하는 [!UICONTROL Cloud Manager] 2018.7.0 릴리스에 대해 간략하게 설명합니다.

**로드, 볼륨, 액세스 및 기타 정의된 모니터링 지표가 급격히 증가하는 경우를 지원하기 위해서 프로덕션 환경의 세그먼트를 수평 확장하여 자동 크기 조절을 활성화합니다.**`Dispatcher/Publish`

## 릴리스 날짜 {#release-date}

[!UICONTROL Cloud Manager] 버전 2018.7.0의 릴리스 날짜는 2018년 9월 10일입니다.

## 새로운 기능 {#what-s-new}

* **프로비저닝**  - 이제  [!UICONTROL Cloud Manager] 발송자/게시 세그먼트에서 수평으로 크기를 조정하여 고객 프로그램에서 제작 환경의 크기를 자동으로 조정할 수 있습니다. 고객 프로그램에서 자동 지정이 활성화되어 있는 경우 프로그램 설정의 프로비저닝 섹션이 UI에서 새로 추가되었습니다. 자세한 내용은 [프로그램 설정](setting-up-program.md)을 참조하십시오.

* **환경**  - 이제 각 환경과 연관된 노드의 크기, 스토리지, 지역 및 상태와 함께 프로덕션 및 스테이지 환경에 대한 자세한 보기를 볼 수 있습니다. 자세한 내용은 [환경 관리](manage-your-environment.md)를 참조하십시오.

* **코드 품질 분석**  - 잘못된 API 사용을 식별하는 새로운 규칙입니다. 자세한 내용은 [사용자 지정 코드 품질 규칙](custom-code-quality-rules.md)을 참조하십시오.

* **성능 테스트**  - 성능 테스트 결과를 보는 동안 CPU 활용률, 디스크 I/O 대기 시간, 페이지 오류율, 디스크 대역폭 사용률, 네트워크 대역폭 사용률, 최대 페이지 응답 시간 및 95번째 백분위수 페이지 응답 시간을 확인할 수 있습니다. [테스트 결과 이해](understand-your-test-results.md) 페이지의 *성능 테스트* 섹션을 참조하십시오.

* **성능 테스트**  - 성능 테스트 결과를 보는 동안 페이지 오류 및 느린 요청 목록을 다운로드할 수 있습니다. [테스트 결과 이해](understand-your-test-results.md) 페이지의 *성능 테스트* 섹션을 참조하십시오.

## 버그 수정 {#bug-fixes}

* 특정 상황에서 내부 시스템 동기화가 부적절하게 실패하여 데이터 보기가 일관되지 않습니다.
* 경우에 따라 수동 파이프라인 트리거가 자동으로 선택되지 않아 양식 유효성 검사 문제가 발생했습니다.
* 특정 고객 빌드 스크립트로 인해 플러그인 비호환성을 기반으로 빌드 단계 동안 오류가 발생할 수 있습니다.

## 알려진 문제 {#known-issues}

* 고객이 커밋 트리거를 선택할 수 있지만 새 커밋을 기반으로 파이프라인이 실제로 시작되지 않을 수 있습니다.
* [!UICONTROL Experience Cloud] 알림 사이드바는 알림을 일관되게 로드하지 못할 수 있습니다. 그러나 알림은 [!UICONTROL Experience Cloud]에 표시되며, 구성된 경우 여전히 이메일을 통해 전송됩니다.

