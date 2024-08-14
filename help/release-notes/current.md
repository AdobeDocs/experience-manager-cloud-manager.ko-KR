---
title: Cloud Manager 2024.8.0 릴리스 노트
description: Cloud Manager 2024.8.0의 릴리스 정보에 대해 알아봅니다.
feature: Release Information
source-git-commit: 34f15aff7478a6a0884f88f534a7dff996a8570e
workflow-type: tm+mt
source-wordcount: '265'
ht-degree: 3%

---


# Cloud Manager 2024.8.0 릴리스 노트 {#release-notes}

이 페이지는 [!UICONTROL Cloud Manager] 2024.8.0에 대한 릴리스 정보를 설명합니다.

>[!NOTE]
>
>AEM as a Cloud Service의 Cloud Manager에 대한 최신 릴리스 정보는 AEM as a Cloud Service의 현재 릴리스 정보의 [Cloud Manager](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/release-notes/cloud-manager/current)을(를) 참조하십시오.

## 릴리스 날짜 {#release-date}

[!UICONTROL Cloud Manager] 2024.8.0의 릴리스 날짜는 2024년 8월 13일입니다. 다음 릴리스는 2024년 9월 14일에 예정되어 있습니다.

## 새로운 기능 {#what-is-new}

* 단계 전용 및 프로덕션 전용 파이프라인([얼리어답터 프로그램](#staging-production-only-pipelines)의 일부로 사용 가능)의 경우 이제 [긴급 모드](/help/using/stage-prod-only.md#emergency-mode)에서 실행할 수 있습니다. 단계 테스트를 건너뜁니다.

## 조기 채택 프로그램 {#early-adoption}

Adobe의 초기 채택 프로그램의 일부가 되어 예정된 기능을 테스트할 수 있습니다.

### 스테이징 전용 및 프로덕션 전용 파이프라인 {#staging-production-only-pipelines}

Adobe이 [스테이징 전용 및 프로덕션 전용 파이프라인](/help/using/stage-prod-only.md)에 대한 지원 도입을 발표하게 되었습니다. 이 새로운 기능을 사용하면 전체 스택 프로덕션 배포 파이프라인을 더 작고 더 특수화된 배포로 나눌 수 있습니다.

이 기능을 테스트하고 피드백을 제공하려면 Adobe ID과 연결된 전자 메일 주소를 사용하여 `Grp-cloudmanager_splitpipelines@adobe.com`에 전자 메일을 보내십시오.

## 버그 수정

* 파이프라인이 삭제된 후 파이프라인 단계가 실행되는 드문 문제가 수정되었습니다.
* 이제 파이프라인을 다시 실행하면 첫 번째 시도에서 작동하므로 재실행을 여러 번 시작해야 하는 드문 문제가 해결되었습니다.
* 전체 스택 파이프라인에 대해 예약된 배포 단계가 이제 선택한 예약된 날짜를 준수하며 **지금**(으)로 되돌려지지 않습니다.
* 실패한 콘텐츠 복사 작업의 상태가 이제 제대로 반영되었으며 드물게 `In Progress` 상태를 더 이상 잘못 표시하지 않습니다.

## 알려진 문제 {#known-issues}

{{content-copy-known-issues}}
