---
title: Cloud Manager 2024.10.0 릴리스 정보
description: Cloud Manager 2024.10.0 릴리스 정보에 대해 알아봅니다.
feature: Release Information
source-git-commit: 94d5f3487408f9d8908bb15221c48ef768390527
workflow-type: tm+mt
source-wordcount: '371'
ht-degree: 23%

---

# Cloud Manager 2024.10.0 릴리스 정보 {#release-notes}

이 페이지는 [!UICONTROL Cloud Manager] 2024.10.0에 대한 릴리스 정보를 설명합니다.

>[!NOTE]
>
>AEM as a Cloud Service에서 Cloud Manager에 대한 최신 릴리스 정보는 [AEM as a Cloud Service의 Cloud Manager 현재 릴리스 정보](https://experienceleague.adobe.com/ko/docs/experience-manager-cloud-service/content/release-notes/cloud-manager/current)를 참조하십시오.



## 릴리스 일자 {#release-date}

<!-- SAVE FOR FUTURE POSSIBLE USE No notable bugs or features for the September release of Cloud Manager. -->

[!UICONTROL Cloud Manager] 2024.10.0의 릴리스 날짜는 2024년 10월 3일입니다.

다음 릴리스는 2024년 11월 14일 금요일에 예정되어 있습니다.



## 새로운 기능 {#what-is-new}

* <!-- BOTH CS & AMS --> Cloud Manager에 사용된 AEM Archetype 버전이 이제 버전 26으로 업데이트되었습니다. [https://github.com/adobe/aem-project-archetype/releases](https://github.com/adobe/aem-project-archetype/releases) 보기
<!-- (CMGR-59817) -->



## 얼리 어답터 프로그램 {#early-adoption}

Cloud Manager의 초기 채택 프로그램의 일부가 되어 향후 출시될 기능을 테스트할 수 있습니다.

### 자신만의 Git을 가져와 - 이제 GitLab 및 Bitbucket에 대한 지원 {#gitlab-bitbucket}

<!-- BOTH CS & AMS -->

**고유한 Git 가져오기** 기능이 GitLab 및 Bitbucket과 같은 외부 저장소에 대한 지원을 포함하도록 확장되었습니다. 이 새로운 지원은 개인 및 엔터프라이즈 GitHub 저장소에 대한 기존 지원에 추가됩니다. 이러한 새 저장소를 추가할 때 파이프라인에 직접 연결할 수도 있습니다. 이러한 저장소를 공용 클라우드 플랫폼 또는 개인 클라우드 또는 인프라 내에서 호스팅할 수 있습니다. 또한 이 통합은 Adobe 저장소와 상수 코드 동기화를 필요로 하지 않고 가져오기 요청을 주 분기로 병합하기 전에 유효성을 검사하는 기능을 제공합니다.

[Cloud Manager에 외부 저장소 추가](/help/managing-code/external-repositories.md)를 참조하십시오.

![저장소 추가 대화 상자](/help/release-notes/assets/repositories-add-release-notes.png)

>[!NOTE]
>
>현재 기본 가져오기 요청 코드 품질 검사는 GitHub 호스팅 저장소에 대해서만 적용되지만 이 기능을 다른 Git 공급업체에 확장하는 업데이트가 진행 중입니다.

이 새로운 기능을 테스트하고 피드백을 공유하려면 Adobe ID과 연결된 전자 메일 주소에서 [Grp-CloudManager_BYOG@adobe.com](mailto:Grp-CloudManager_BYOG@adobe.com)(으)로 전자 메일을 보내세요. 사용할 Git 플랫폼과 개인/공용 또는 기업 저장소 구조를 포함해야 합니다.

### 스테이징 전용 및 프로덕션 전용 파이프라인 {#staging-production-only-pipelines}

Adobe은 [스테이징 전용 및 프로덕션 전용 파이프라인](/help/using/stage-prod-only.md)에 대한 지원 도입을 발표합니다. 이 새로운 기능을 사용하면 전체 스택 프로덕션 배포 파이프라인을 보다 소규모의 전문화된 배포로 나눌 수 있습니다.

이 기능을 테스트하고 피드백을 제공하려면 Adobe ID과 연결된 전자 메일 주소로 [Grp-cloudmanager_splitpipelines@adobe.com](mailto:Grp-cloudmanager_splitpipelines@adobe.com)에 전자 메일을 보내십시오.

<!-- ## Bug fixes

* text
-->

## 알려진 문제 {#known-issues}

{{content-copy-known-issues}}
