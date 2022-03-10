---
title: 2022.3.0 릴리스 정보
description: 다음은 Cloud Manager 릴리스 2022.3.0의 릴리스 노트입니다.
feature: Release Information
exl-id: 2d38abb1-cfc7-44a9-b303-b555e2827eea
source-git-commit: 0d14adda454889eebbb0a875978ceeaa5ee4f7ea
workflow-type: tm+mt
source-wordcount: '197'
ht-degree: 4%

---


# Cloud Manager 릴리스 2022.3.0의 릴리스 노트 {#release-notes}

이 페이지에서는 다음에 대한 릴리스 노트를 문서화합니다 [!UICONTROL Cloud Manager] 릴리스 2022.3.0.

>[!NOTE]
>
>AEM as a Cloud Service의 Cloud Manager 최신 릴리스 노트는 을 참조하십시오 [AEM as a Cloud Service의 현재 릴리스 노트에 있는 Cloud Manager.](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/release-notes-cloud-manager/release-notes-cm-current.html)

## 릴리스 날짜 {#release-date}

에 대한 릴리스 날짜 [!UICONTROL Cloud Manager] 릴리스 2022.3.0은 2022년 3월 10일입니다. 다음 릴리스는 2022년 4월 7일에 예정되어 있습니다.

## 새로운 기능 {#what-is-new}

* (Cloud Service 전용) AEM 환경 로그에 액세스하는 작업은 개발자 역할을 사용하여 수행할 수 있습니다.
* 다음 [`reliability_rating` 중요 지표](understand-your-test-results.md) 이 비활성화되었습니다.


## 버그 수정 {#bug-fixes}

* [다음 **로드 밸런서 변경 건너뛰기** 옵션](configuring-production-pipelines.md#adding-production-pipeline) 이제 을(를) 제대로 사용하지 않도록 설정할 수 있습니다.
* [다음 **로드 밸런서 변경 건너뛰기** 옵션](configuring-production-pipelines.md#adding-production-pipeline) 이제 배포 파이프라인 편집 워크플로우에 대해 표시됩니다.
* 수동으로 만든 Git 리포지토리의 하위 집합에 영향을 받는 잘못된 이름 값이 있습니다 [빌드 아티팩트 재사용 기능입니다.](setting-up-project.md#build-artifact-reuse) 이러한 리포지토리의 이름이 변경되었으며 사용자는 Cloud Manager API/UI에서 수정된 이름을 볼 수 있습니다.
* [코드 품질 파이프라인을 추가하거나 편집할 때](configuring-non-production-pipelines.md) 지표 실패를 처리하는 옵션이 더 이상 표시되지 않습니다.
* 예기치 않은 파이프라인 변수 구성으로 인해 빌드 단계에서 오류가 발생하지 않습니다.
