---
title: 2024.7.0 릴리스 정보
description: Cloud Manager 릴리스 2024.7.0의 릴리스 정보입니다.
feature: Release Information
exl-id: 2d38abb1-cfc7-44a9-b303-b555e2827eea
source-git-commit: d536cd96d135e48039f94fd01142a63305b6eeae
workflow-type: tm+mt
source-wordcount: '226'
ht-degree: 48%

---


# Cloud Manager 릴리스 2024.7.0의 릴리스 노트 {#release-notes}

이 페이지는 [!UICONTROL Cloud Manager] 릴리스 2024.7.0에 대한 릴리스 정보를 설명합니다.

>[!NOTE]
>
>AEM as a Cloud Service에서 Cloud Manager에 대한 최신 릴리스 정보는 [AEM as a Cloud Service의 Cloud Manager 현재 릴리스 정보](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/release-notes-cloud-manager/release-notes-cm-current.html?lang=ko-KR)를 참조하십시오.

## 릴리스 일자 {#release-date}

[!UICONTROL Cloud Manager] 릴리스 2024.7.0의 릴리스 날짜는 2024년 7월 18일입니다. 다음 릴리스는 2024년 8월 8일에 예정되어 있습니다.

## 새로운 기능 {#what-is-new}

* 커밋에서 파이프라인을 시작하기 위한 [프로덕션 파이프라인](/help/using/production-pipelines.md#adding-production-pipeline) 및 [비프로덕션 파이프라인](/help/using/non-production-pipelines.md#adding-non-production-pipeline) 트리거 **Git 변경 시**&#x200B;를 이제 [개인 저장소에서 사용할 수 있습니다.](/help/managing-code/private-repositories.md)
* 사전 프로덕션 파이프라인은 수동으로만 트리거할 수 있으며 **Git 변경 시**(으)로 구성할 수 없습니다.
* 프로덕션 전용 파이프라인의 경우 프로모션 가능한 실행 목록에는 프로덕션 환경에 배포된 아티팩트 버전보다 큰 아티팩트 버전이 있는 실행이 포함됩니다.

## 얼리 어답터 프로그램 {#early-adoption}

얼리 어답터 프로그램에 참여하여 향후 기능을 테스트할 기회를 얻으십시오.

### 스테이징 전용 및 프로덕션 전용 파이프라인 {#staging-production-only-pipelines}

[스테이징 전용 및 프로덕션 전용 파이프라인](/help/using/stage-prod-only.md)에 대한 지원이 도입되어 전체 스택 프로덕션 배포 파이프라인을 더 작고 전문적인 배포로 분할할 수 있습니다.

이러한 새 기능을 테스트하고 피드백을 공유하는 데 관심이 있으시면 Adobe ID와 연결된 이메일 주소로 `Grp-cloudmanager_splitpipelines@adobe.com`에 이메일을 보내주십시오.
