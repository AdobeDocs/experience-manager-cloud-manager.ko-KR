---
title: 2021.6.0 릴리스 노트
description: Cloud Manager 릴리스 2021.6.0에 대한 정보를 보려면 이 페이지를 따르십시오
feature: 릴리스 정보
source-git-commit: c39390f34cf4ab6c9b2d5957b169c3c2cb43e6d3
workflow-type: tm+mt
source-wordcount: '285'
ht-degree: 4%

---

# 2021.6.0 릴리스 노트 {#release-notes-for}

다음 섹션에서는 [!UICONTROL Cloud Manager] 릴리스 2021.6.0에 대한 일반 릴리스 노트를 간략하게 설명합니다.

>[!NOTE]
>AEM as a Cloud Service에서 Cloud Manager에 대한 최신 릴리스 노트를 보려면 [현재 릴리스 노트](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/getting-access/release-notes-cloud-manager/release-notes-cm-current.html?lang=en#getting-access)를 참조하십시오.

## 릴리스 날짜 {#release-date}

[!UICONTROL Cloud Manager] 버전 2021.6.0의 출시일은 2021년 6월 10일입니다.
다음 릴리스는 2021년 7월 15일에 예정되어 있습니다.

## 새로운 기능 {#whats-new}

* 이제 자산 및 사이트 테스트가 병렬(해당되는 경우)로 실행되므로 총 파이프라인 실행 시간이 줄어듭니다. 이 기능은 다음 몇 주 동안 고객에 대해 활성화됩니다.

* 이제 빌드 단계 중에 다운로드한 Maven 종속성이 파이프라인 실행 간에 캐시됩니다. 이 기능은 다음 몇 주 동안 고객에 대해 활성화됩니다.

* 프로젝트를 만드는 동안 및 git 워크플로우 관리를 통한 기본 푸시 명령에 사용된 기본 분기 이름이 `main`(으)로 변경되었습니다.

* UI에서 프로그램 편집 환경을 새로 고쳤습니다. 자세한 내용은 [프로그램 편집](/help/using/setting-up-program.md#editing-program)을 참조하십시오.

* `/oak:index` 노드를 변경할 수 없는 것으로 분류하도록 품질 규칙 `ImmutableMutableMixCheck`이 업데이트되었습니다.

* 품질 규칙 `CQBP-84` 및 `CQBP-84--dependencies`이(가) 단일 규칙으로 통합되었습니다.

* 경우에 따라 건너뛴 테스트 지표를 계산하지 않으면 파이프라인 실행이 실패합니다.

## 버그 수정 {#bug-fixes}

* 루트 요소 이름을 올바르게 구문 분석한 후 새 행을 포함하는 JCR 노드 정의가 있습니다.

* 목록 저장소 API는 삭제된 저장소를 필터링하지 않습니다.

* 예약 단계에 잘못된 값을 제공한 경우 잘못된 오류 메시지가 표시되었습니다.

* 경우에 따라 파이프라인 실행이 프로덕션 단계에 배포되고 사용자가 실행을 중지하는 경우 UI의 배포 상태 메시지가 실제로 발생하는 사항을 올바르게 반영하지 못했습니다.
