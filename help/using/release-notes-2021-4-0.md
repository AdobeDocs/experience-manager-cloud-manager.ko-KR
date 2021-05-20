---
title: 2021.4.0 릴리스 노트
description: Cloud Manager 릴리스 2021.4.0에 대한 정보를 보려면 이 페이지를 따르십시오
feature: 릴리스 정보
exl-id: 2d38abb1-cfc7-44a9-b303-b555e2827eea
source-git-commit: 5f81fdb86b1dfa6c748bb7784ef00dc062c9f8ef
workflow-type: tm+mt
source-wordcount: '185'
ht-degree: 7%

---

# 2021.4.0 릴리스 노트 {#release-notes-for}

다음 섹션에서는 [!UICONTROL Cloud Manager] 릴리스 2021.4.0에 대한 일반 릴리스 노트를 간략하게 설명합니다.

## 릴리스 날짜 {#release-date}

[!UICONTROL Cloud Manager] 버전 2021.4.0의 출시일은 2021년 4월 8일입니다.

## 새로운 기능 {#whats-new}

* 성능 테스트 가상 사용자에 대한 요청 시간 제한이 20초에서 60초로 늘어났습니다.

* 파이프라인이 구성되지 않은 경우에도 파이프라인 카드에 Git 관리 단추가 표시됩니다.

* 파이프라인 실행 페이지의 배포 단계 동안 사용자는 *진행 중* 상태에 대한 UI의 현재 단계 외에 완료되고 향후 배포 단계를 볼 수 있습니다.

* Cloud Manager에서 사용하는 AEM 프로젝트 원형 버전이 버전 27로 업데이트되었습니다.

* 환경이 삭제되었을 때 파이프라인을 시작할 때 오류 메시지가 명확해졌습니다.

* Eclipse 프로젝트에서 제공하는 OSGi 번들은 이제 규칙 `CQBP-84--dependencies`에서 제외됩니다.

## 버그 수정 {#bug-fixes}

* 프로덕션 파이프라인의 *자산 테스트* 단계에서 발생할 수 있는 드문 일시적인 오류입니다.

* 프로덕션 파이프라인 로드 테스트의 후행 슬래시로 404 오류가 발생했습니다.

* `Runmode` 검사에서 비폴더 노드에서 긍정 오류(false positive)가 발생했습니다.