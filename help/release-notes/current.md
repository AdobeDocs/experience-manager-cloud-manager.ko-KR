---
title: 2024.7.0 릴리스 정보
description: Cloud Manager 2024.7.0의 릴리스 정보에 대해 알아봅니다.
feature: Release Information
exl-id: 2d38abb1-cfc7-44a9-b303-b555e2827eea
source-git-commit: 200366e5db92b7ffc79b7a47ce8e7825b29b7969
workflow-type: tm+mt
source-wordcount: '226'
ht-degree: 4%

---


# Cloud Manager 2024.7.0 릴리스 노트 {#release-notes}

이 페이지는 [!UICONTROL Cloud Manager] 2024.7.0에 대한 릴리스 정보를 설명합니다.

>[!NOTE]
>
>AEM as a Cloud Service의 Cloud Manager에 대한 최신 릴리스 정보는 AEM as a Cloud Service의 현재 릴리스 정보의 [Cloud Manager](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/release-notes/cloud-manager/current)을(를) 참조하십시오.

## 릴리스 날짜 {#release-date}

[!UICONTROL Cloud Manager] 2024.7.0의 릴리스 날짜는 2024년 7월 18일입니다. 다음 릴리스는 2024년 8월 13일에 예정되어 있습니다.

## 새로운 기능 {#what-is-new}

* 커밋에서 파이프라인을 시작하기 위한 [프로덕션 파이프라인](/help/using/production-pipelines.md#adding-production-pipeline) 및 [비프로덕션 파이프라인](/help/using/non-production-pipelines.md#adding-non-production-pipeline) 트리거 **Git 변경 시**&#x200B;를 이제 [개인 저장소](/help/managing-code/private-repositories.md)에 사용할 수 있습니다.
* 사전 프로덕션 파이프라인은 수동으로만 트리거할 수 있으며 **Git 변경 시**(으)로 구성할 수 없습니다.
* 프로덕션 전용 파이프라인의 경우 프로모션 가능한 실행 목록에는 프로덕션 환경에 배포된 아티팩트 버전보다 큰 아티팩트 버전을 사용하는 실행이 포함됩니다.
* [AEM Project Archetype](https://experienceleague.adobe.com/ko/docs/experience-manager-core-components/using/developing/archetype/overview)이(가) [버전 49](https://github.com/adobe/aem-project-archetype/tree/aem-project-archetype-49)(으)로 업데이트되었습니다.

## 조기 채택 프로그램 {#early-adoption}

Cloud Manager의 초기 채택 프로그램의 일부가 되어 예정된 기능을 테스트할 수 있습니다

### 스테이징 전용 및 프로덕션 전용 파이프라인 {#staging-production-only-pipelines}

[스테이징 전용 및 프로덕션 전용 파이프라인](/help/using/stage-prod-only.md)에 대한 지원이 도입되어 전체 스택 프로덕션 배포 파이프라인을 더 작고 전문화된 배포로 분할할 수 있습니다.

이 새로운 기능을 테스트하고 피드백을 공유하려면 Adobe ID과 연결된 전자 메일 주소에서 `Grp-cloudmanager_splitpipelines@adobe.com`(으)로 전자 메일을 보내세요.
