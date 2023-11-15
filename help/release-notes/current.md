---
title: 2023.11.0 릴리스 정보
description: 다음은 Cloud Manager 릴리스 2023.11.0의 릴리스 정보입니다.
feature: Release Information
exl-id: 2d38abb1-cfc7-44a9-b303-b555e2827eea
source-git-commit: 264c7ffcbc9e10903880a511a4ca605be666f7e8
workflow-type: tm+mt
source-wordcount: '386'
ht-degree: 30%

---


# Cloud Manager 릴리스 2023.11.0의 릴리스 정보 {#release-notes}

이 페이지는 [!UICONTROL Cloud Manager] 릴리스 2023.11.0에 대한 릴리스 정보를 설명합니다.

>[!NOTE]
>
>AEM as a Cloud Service에서 Cloud Manager에 대한 최신 릴리스 정보는 [AEM as a Cloud Service의 Cloud Manager 현재 릴리스 정보](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/release-notes-cloud-manager/release-notes-cm-current.html)를 참조하십시오.

## 릴리스 일자 {#release-date}

의 릴리스 날짜 [!UICONTROL Cloud Manager] 릴리스 2023.11.0은 2023년 11월 14일입니다. 다음 릴리스는 2023년 12월 7일에 예정되어 있습니다.

## 새로운 기능 {#what-is-new}

* [파이프라인 실행 세부 정보 페이지](/help/using/managing-pipelines.md#view-details) 이제 아직 시작하지 않은 단계가 회색으로 표시된 파이프라인 실행의 모든 단계를 표시합니다.
* 둘 다에서 **[활동](/help/using/managing-pipelines.md#activity)** 및 **[파이프라인](/help/using/managing-pipelines.md#pipelines)** 페이지 에서는 이제 실행 중인 상태의 파이프라인을 클릭하면 파이프라인 실행 요약을 사용할 수 있습니다.
* 새 항목 **기간** 섹션이 [파이프라인 세부 정보 페이지](/help/using/managing-pipelines.md#view-details) 여기에는 해당 프로그램의 기록 트렌드를 기반으로 파이프라인 단계의 평균 기간이 포함됩니다.
* 다음에서 [파이프라인 실행 페이지,](/help/using/managing-pipelines.md#activity-window) 이제 완료된 단계에 기간이 표시됩니다.
* Cloud Manager [콘텐츠 복사 도구](/help/using/content-copy.md) 를 사용하면 사용자가 AMS가 호스팅하는 AEM 6.x 프로덕션 환경에서 테스트 목적으로 변경 가능한 콘텐츠를 하위 환경으로 복사할 수 있습니다.
* 실행 [빌드 아티팩트 재사용](/help/getting-started/project-setup.md#build-artifact-reuse) 이제 해당 아티팩트를 처음 빌드한 실행에 대한 링크가 표시됩니다.
* 선택할 옵션 **중요한 지표 실패** 이제 을(를) 구성할 수 있습니다. [코드 품질 파이프라인](/help/using/non-production-pipelines.md) 또한.

## 조기 채택 프로그램 {#early-adoption}

조기 채택 프로그램에 참여하여 향후 기능을 테스트할 기회를 얻으십시오

### GitHub 가져오기 {#byo-github}

GitHub를 사용하여 저장소를 관리하는 경우 [이제 Cloud Manager를 통해 GitHub 저장소 내에서 직접 코드의 유효성을 검사할 수 있습니다.](/help/managing-code/byo-github.md) 이 통합을 사용하면 코드를 Adobe 저장소와 일관되게 동기화할 필요가 없으며, 가져오기 요청을 주 분기로 병합하기 전에 이를 확인할 수 있습니다.

이 새로운 기능을 테스트하고 피드백을 공유하려면 (으)로 이메일을 보내십시오. `Grp-CloudManager_BYOG@adobe.com` (Adobe ID과 연계된 이메일 주소).

### 사용자 정의 권한 {#custom-permissions}

[Cloud Manager 사용자 정의 권한](/help/using/custom-permissions.md)을 사용하여 Cloud Manager 사용자의 프로그램, 파이프라인 및 환경에 대한 액세스를 제한하는 구성 가능한 권한으로 새 사용자 정의 권한 프로필을 생성할 수 있습니다.

이 새로운 기능을 테스트하고 피드백을 공유하려면 전자 메일을 보내십시오 `Grp-CloudManager_ams_custompermissions@adobe.com` (Adobe ID과 연계된 이메일 주소).
