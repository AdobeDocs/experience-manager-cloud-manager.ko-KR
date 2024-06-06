---
title: 2024.6.0 릴리스 정보
description: 다음은 Cloud Manager 릴리스 2024.6.0의 릴리스 정보입니다.
feature: Release Information
exl-id: 2d38abb1-cfc7-44a9-b303-b555e2827eea
source-git-commit: a41ea35cb685d4e88e016bc887eb2465963747e1
workflow-type: tm+mt
source-wordcount: '291'
ht-degree: 37%

---


# Cloud Manager 릴리스 2024.6.0의 릴리스 정보 {#release-notes}

이 페이지는 다음에 대한 릴리스 정보를 설명합니다. [!UICONTROL Cloud Manager] 릴리스 2024.6.0.

>[!NOTE]
>
>AEM as a Cloud Service에서 Cloud Manager에 대한 최신 릴리스 정보는 [AEM as a Cloud Service의 Cloud Manager 현재 릴리스 정보](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/release-notes-cloud-manager/release-notes-cm-current.html?lang=ko-KR)를 참조하십시오.

## 릴리스 일자 {#release-date}

의 릴리스 날짜 [!UICONTROL Cloud Manager] 릴리스 2024.6.0은 2024년 6월 6일입니다. 다음 릴리스는 2024년 7월 11일에 예정되어 있습니다.

## 새로운 기능 {#what-is-new}

* 이제 다음을 수행할 수 있습니다. [고유한 GitHub 저장소 사용](/help/managing-code/private-repositories.md) 전체 스택 및 프론트엔드 파이프라인 모두의 소스로 사용됩니다.
   * 또한 다음을 통해 GitHub 저장소를 활용할 수 있습니다. [git 하위 모듈,](/help/managing-code/git-submodules.md) 가져오기 요청 유효성 검사에 사용되는 자동 생성 파이프라인에 대한 향상된 제어 기능을 제공하고 코드 스캔 단계 동안 중요한 지표에 대한 비헤이비어를 정의할 수 있도록 합니다.
   * [또한 다음을 선택할 수 있습니다.](/help/managing-code/github-check-config.md) gitHub에서 보고서 기록을 보존하려면 파이프라인 이름을 지정하고 필요에 맞게 파이프라인 변수를 설정합니다.
* 새 OakPal 규칙이 [Cloud Manager 코드 품질 검사.](/help/using/custom-code-quality-rules.md#oakpal-ui-content-package)
   * 2024년 6월 현재 추가된 모든 새 규칙은 변경되지 않는 변경 사항입니다.
   * 이러한 새로운 규칙은 Cloud Manager 2024년 8월 릴리스부터 파이프라인이 실패하게 되므로 가능한 한 빨리 이러한 문제를 해결해야 합니다.

## 얼리 어답터 프로그램 {#early-adoption}

얼리 어답터 프로그램에 참여하여 향후 기능을 테스트할 기회를 얻으십시오.

### 스테이징 전용 및 프로덕션 전용 파이프라인 {#staging-production-only-pipelines}

[스테이징 전용 및 프로덕션 전용 파이프라인](/help/using/stage-prod-only.md)에 대한 지원이 도입되어 전체 스택 프로덕션 배포 파이프라인을 더 작고 전문적인 배포로 분할할 수 있습니다.

이러한 새 기능을 테스트하고 피드백을 공유하는 데 관심이 있으시면 Adobe ID와 연결된 이메일 주소로 `Grp-cloudmanager_splitpipelines@adobe.com`에 이메일을 보내주십시오.
