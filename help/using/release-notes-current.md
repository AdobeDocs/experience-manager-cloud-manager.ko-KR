---
title: 2021.10.0 릴리스 노트
description: Cloud Manager 릴리스 2021.10.0에 대한 정보를 보려면 이 페이지를 따르십시오
feature: Release Information
exl-id: 2d38abb1-cfc7-44a9-b303-b555e2827eea
source-git-commit: b28f8f1bedb92428d332716510cbf0fd714fada6
workflow-type: tm+mt
source-wordcount: '365'
ht-degree: 3%

---

# 2021.10.0 릴리스 노트 {#release-notes-for}

다음 섹션에서는 [!UICONTROL Cloud Manager] 릴리스 2021.10.0에 대한 일반 릴리스 노트를 간략하게 설명합니다.

>[!NOTE]
>AEM as a Cloud Service에서 Cloud Manager에 대한 최신 릴리스 노트를 보려면 [현재 릴리스 노트](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/getting-access/release-notes-cloud-manager/release-notes-cm-current.html?lang=en#getting-access)를 참조하십시오.

## 릴리스 날짜 {#release-date}

[!UICONTROL Cloud Manager] 버전 2021.10.0의 릴리스 날짜는 2021년 10월 14일입니다.
다음 릴리스는 2021년 11월 4일에 예정되어 있습니다.

## 새로운 기능 {#whats-new}

* 이제 긴급 배포를 위한 보안 및 성능 테스트 단계를 우회하여 프로덕션 파이프라인을 &quot;응급&quot; 모드로 실행할 수 있습니다.

* Cloud Service과 일관성을 위해 이제 기존 배포 파이프라인이 참조되고 UI에서 &#39;전체 스택&#39; 파이프라인으로 레이블이 지정됩니다.

* 이제 파이프라인 카드가 새로 고쳐져서 프로덕션 파이프라인과 비프로덕션 파이프라인을 모두 표시하는 통합된 단일 면을 표시할 수 있으며, 사용자는 각 파이프라인과 연관된 작업 메뉴에서 직접 실행/일시 중지/재개 를 선택할 수 있습니다.

* 이제 배포 관리자 역할의 사용자는 UI를 통해 셀프 서비스 방식으로 프로덕션 파이프라인을 삭제할 수 있습니다.

* 이제 익숙하고 현대적인 모듈을 사용할 수 있도록 파이프라인 경험을 추가 및 편집할 수 있습니다.

* 이제 Cloud Manager 사용자는 랜딩 페이지의 오른쪽 상단에 있는 **피드백** 버튼을 통해 UI에서 직접 피드백을 제출할 수 있습니다.

* 이제 Cloud Manager 사용자 인터페이스에서 연간 SLA 그래프를 다운로드할 수 있습니다.

* 이제 코드 품질 및 비프로덕션 파이프라인 실행에서는 빌드 단계에서 보다 효율적인 약식 복제 프로세스를 사용하므로 고객이 특히 큰 git 저장소를 사용하는 경우 빌드 시간이 빨라집니다.

* 이제 Cloud Manager API 설명서에는 로그인한 사용자가 브라우저에서 API를 실험할 수 있도록 해주는 대화형 필드가 포함되어 있습니다. 자세한 내용은 [Cloud Manager API 놀이터](https://www.adobe.io/experience-cloud/cloud-manager/reference/playground/)를 참조하십시오.

* &#39;탐색 대상&#39; 아래의 선택 옵션이 비활성화되어 있으면 프로그램 카드의 도구 설명이 더 설명적입니다. 이제 &quot;프로덕션 환경은 존재하지 않습니다.&quot;라고 표시됩니다.


## 버그 수정 {#bug-fixes}

* 내부 시스템에서 읽은 데이터가 올바르게 입력되지 않으면 CSE에서 제공한 관련 없는 데이터가 Cloud Manager에 제대로 반영되지 않을 수 있습니다.

* 특정 고객 상황에서 빌드 단계에서 다운로드한 잘못된 가공물이 빌드 오류를 일으켰어야 하는 경우 무시됩니다.
