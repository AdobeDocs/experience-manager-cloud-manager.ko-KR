---
title: Cloud Manager 2024.8.0 릴리스 정보
description: Cloud Manager 2024.8.0 릴리스 정보에 대해 알아봅니다.
feature: Release Information
source-git-commit: 5ced643fabe0a670e456cbea72f9da8196ac774a
workflow-type: ht
source-wordcount: '266'
ht-degree: 100%

---


# Cloud Manager 2024.8.0 릴리스 정보 {#release-notes}

이 페이지는 [!UICONTROL Cloud Manager] 2024.8.0에 대한 릴리스 정보를 설명합니다.

>[!NOTE]
>
>AEM as a Cloud Service에서 Cloud Manager에 대한 최신 릴리스 정보는 [AEM as a Cloud Service의 Cloud Manager 현재 릴리스 정보](https://experienceleague.adobe.com/ko/docs/ experience-manager-cloud-service/content/release-notes/cloud-manager/current)를 참조하십시오.

## 릴리스 일자 {#release-date}

[!UICONTROL Cloud Manager] 2024.8.0의 릴리스 일자는 2024년 8월 14일입니다. 다음 릴리스는 2024년 9월 14일에 예정되어 있습니다.

## 새로운 기능 {#what-is-new}

* ([얼리 어답터 프로그램](#staging-production-only-pipelines)의 일부로 사용 가능한) 스테이징 전용 및 프로덕션 전용 파이프라인의 경우 이제 스테이지 테스트를 건너뛰고 [긴급 모드](/help/using/stage-prod-only.md#emergency-mode)로 실행할 수 있습니다.

## 얼리 어답터 프로그램 {#early-adoption}

Cloud Manager의 얼리 어답터 프로그램에 참여하여 향후 기능을 테스트할 기회를 얻으십시오.

### 스테이징 전용 및 프로덕션 전용 파이프라인 {#staging-production-only-pipelines}

Adobe는 [스테이징 전용 및 프로덕션 전용 파이프라인](/help/using/stage-prod-only.md)에 대한 지원 출시를 발표하게 되어 기쁩니다. 이 새로운 기능을 사용하면 전체 스택 프로덕션 배포 파이프라인을 보다 소규모의 전문화된 배포로 나눌 수 있습니다.

이 새로운 기능을 테스트하고 피드백을 제공하려면 Adobe ID에 연결된 이메일 주소를 사용하여 `Grp-cloudmanager_splitpipelines@adobe.com`으로 이메일을 보내 주십시오.

## 버그 수정

* 파이프라인이 삭제된 후에도 파이프라인 단계가 드물게 실행되는 문제가 수정되었습니다.
* 이제 파이프라인을 다시 실행하면 첫 번째 시도에서 작동하여 여러 번 다시 실행을 시작해야 하는 드문 문제를 수정되었습니다.
* 전체 스택 파이프라인에 대해 예약된 배포 단계는 이제 선택한 예약 날짜를 따르며 **지금**&#x200B;으로 되돌아가지 않습니다.
* 이제 실패한 콘텐츠 복사 작업의 상태가 제대로 반영되어 더 이상 `In Progress` 상태를 잘못 표시하지 않습니다.

## 알려진 문제 {#known-issues}

{{content-copy-known-issues}}
