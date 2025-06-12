---
title: Cloud Manager 2025.6.0 릴리스 정보
description: Adobe Managed Services용 Cloud Manager 2025.5.0 릴리스에 대해 알아봅니다.
feature: Release Information
exl-id: cc1dc94b-129d-4de7-8e57-8fc5dcba7d9f
source-git-commit: 38d398caf2323b603afd293aa9152308fefd323f
workflow-type: tm+mt
source-wordcount: '560'
ht-degree: 68%

---

# Adobe Managed Services용 Cloud Manager 2025.6.0 릴리스 정보 {#release-notes}

<!-- RELEASE WIKI  https://wiki.corp.adobe.com/display/DMSArchitecture/Cloud+Manager+2025.04.0+Release -->

Adobe Managed Services용 [!UICONTROL Cloud Manager] 2025.6.0 릴리스에 대해 알아봅니다.

또한 [최신 Adobe Experience Manager as a Cloud Service 릴리스 정보](https://experienceleague.adobe.com/ko/docs/experience-manager-cloud-service/content/release-notes/home)도 살펴보십시오.

## 릴리스 일자 {#release-date}

[!UICONTROL Cloud Manager] 2025.6.0의 릴리스 날짜는 2025년 6월 5일 목요일입니다.

<!-- There are no significant new features or bug fixes in the May Cloud Manager release. -->

다음 릴리스는 2025년 7월 10일 목요일에 예정되어 있습니다.

<!-- SAVE FOR FUTURE POSSIBLE USE There are no significant new features or bug fixes in the May Cloud Manager release. -->


## 새로운 기능 {#what-is-new}

* **스테이징 전용 및 프로덕션 전용 파이프라인**

  Cloud Manager은 이제 스테이징 전용 및 프로덕션 전용 파이프라인을 지원합니다. 이 기능을 사용하면 전체 스택 프로덕션 배포를 더 작은 용도별 파이프라인으로 분할할 수 있습니다. <!-- This feature went into GA from Private beta in the June 5, 2025 CM release -->

  ![전체 스택 코드 라디오 단추가 선택되고 스테이징 환경이 선택된 비프로덕션 파이프라인 추가 대화 상자](/help/release-notes/assets/add-non-production-pipeline.png)

  [스테이지 전용 및 프로덕션 전용 파이프라인](/help/using/stage-prod-only.md)을 참조하십시오.

* **파이프라인 즐겨찾기**

  이번 릴리스에서는 Cloud Manager에서 즐겨찾는 파이프라인을 고정할 수 있는 기능을 도입하여 특정 파이프라인을 즐겨찾기로 표시하여 **파이프라인** 페이지의 목록 맨 위에 나타나도록 할 수 있습니다. 이 향상된 기능 덕분에 자주 접근하는 파이프라인을 더 쉽게 찾고 실행할 수 있습니다. <!-- CMGR-68293 -->

  ![즐겨찾기로 표시된 파이프라인](/help/release-notes/assets/pipeline-favorites.png) *즐겨찾기로 표시된 두 개의 파이프라인.*

  [파이프라인 즐겨찾기 표시](/help/using/managing-pipelines.md#pipeline-favorites)를 참조하십시오.


## 비공개 베타 프로그램 {#beta-program}

Cloud Manager의 비공개 베타 프로그램에 참여하여 일반 릴리스 전에 예정된 기능에 독점적으로 액세스할 수 있습니다.

현재 다음과 같은 비공개 베타 기회를 사용할 수 있습니다.


### 자체 Git 가져오기 - GitLab 및 Bitbucket 지원 포함 {#gitlab-bitbucket}

**BYOG(Bring Your Own Git**) 기능이 GitLab 및 Bitbucket과 같은 외부 저장소에 대한 지원을 포함하도록 확장되었습니다. 이 새로운 지원은 기존에 제공되던 개인 및 기업용 GitHub 저장소에 대한 지원에 추가됩니다. 이러한 새로운 저장소를 추가하면 이를 파이프라인에 직접 연결할 수도 있습니다. 이러한 저장소를 공개 클라우드 플랫폼이나 비공개 클라우드 또는 인프라 내에 호스팅할 수 있습니다. 또한 이 통합을 통해 Adobe 저장소와 지속적으로 코드를 동기화할 필요가 없으며 가져오기 요청을 메인 분기로 병합하기 전에 유효성 검사를 수행할 수 있는 기능이 제공됩니다.

이제 외부 저장소(GitHub 호스팅된 저장소 제외)와 **배포 트리거**&#x200B;를 **Git 변경 시**&#x200B;로 설정한 파이프라인이 자동으로 시작됩니다.

[Cloud Manager에서 외부 저장소 추가](/help/managing-code/external-repositories.md)를 참조하십시오.

![저장소 추가 대화 상자](/help/release-notes/assets/repositories-add-release-notes.png)

>[!NOTE]
>
>현재 기본 제공 가져오기 요청 코드 품질 검사는 GitHub 호스팅 저장소에만 적용되지만 이 기능을 다른 Git 공급업체로 확장하기 위한 업데이트가 진행 중입니다.

이 새로운 기능을 테스트하고 피드백을 공유하는 데 관심이 있으시면 Adobe ID와 연결된 이메일 주소로 [Grp-CloudManager_BYOG@adobe.com](mailto:Grp-CloudManager_BYOG@adobe.com)에 이메일을 보내 주십시오. 사용하려는 Git 플랫폼과 비공개/공개 또는 기업 저장소 구조인지 여부를 반드시 포함해야 합니다.

#### 액세스 토큰 관리{#access-tokens}

GitHub Enterprise, GitLab, Bitbucket 및 Azure DevOps와 같은 외부 Bring Your Own Git 저장소와 연결된 액세스 토큰을 보고, 이름을 바꾸고, 삭제하려면 BYOG와 함께 **액세스 토큰 관리** 기능을 사용하십시오.

[액세스 토큰 관리](/help/managing-code/manage-access-tokens.md)를 참조하세요.

이 새로운 기능을 테스트하고 피드백을 공유하는 데 관심이 있다면 Adobe ID와 연결된 이메일 주소로 [Grp-CloudManager_BYOG@adobe.com](mailto:Grp-CloudManager_BYOG@adobe.com)에 이메일을 보내 주십시오. 사용하려는 Git 플랫폼과 비공개/공개 또는 기업 저장소 구조인지 여부를 반드시 포함해야 합니다.


## 버그 수정 {#bug-fixes}

* 이제 AEM Cloud Manager는 고객 아티팩트를 가져올 때 409 오류(충돌)로 인해 발생하는 Maven 빌드 실패를 고객이 일으킨 실패로 올바르게 매핑합니다. 이 변경 사항은 고객 환경 설정과 관련된 문제를 내부 오류와 구분하여 오류 메시지를 개선합니다. <!-- CMGR-66673 -->

<!--
Known Issues {#known-issues}

* A -->
