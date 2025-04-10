---
title: Cloud Manager 2025.4.0 릴리스 정보
description: Adobe Managed Services용 Cloud Manager 2025.4.0 릴리스에 대해 알아봅니다.
feature: Release Information
exl-id: cc1dc94b-129d-4de7-8e57-8fc5dcba7d9f
source-git-commit: 40d093ce7d6839fff4ba16f790c61b96cb88dda5
workflow-type: tm+mt
source-wordcount: '380'
ht-degree: 90%

---

# Adobe Managed Services용 Cloud Manager 2025.4.0 릴리스 정보 {#release-notes}

<!-- RELEASE WIKI  https://wiki.corp.adobe.com/display/DMSArchitecture/Cloud+Manager+2025.04.0+Release -->

Adobe Managed Services용 [!UICONTROL Cloud Manager] 2025.4.0 릴리스에 대해 알아봅니다.

또한 [최신 Adobe Experience Manager as a Cloud Service 릴리스 정보](https://experienceleague.adobe.com/ko/docs/experience-manager-cloud-service/content/release-notes/home)도 살펴보십시오.

## 릴리스 일자 {#release-date}

[!UICONTROL Cloud Manager] 2025.4.0의 릴리스 날짜는 2025년 4월 10일 목요일입니다.

다음 릴리스는 2025년 5월 8일 금요일에 예정되어 있습니다.

<!--
## What's new {#what-is-new}

* 
-->


## 얼리 어답터 프로그램 {#early-adoption}

Cloud Manager의 조기 채택 프로그램에 참여하여 일반 릴리스 전에 예정된 기능에 독점적으로 액세스할 수 있습니다.

현재 다음 조기 채택 기회를 사용할 수 있습니다.

### 자체 Git 가져오기 - GitLab 및 Bitbucket 지원 포함 {#gitlab-bitbucket}

**자체 Git 가져오기** 기능이 확장되어 GitLab 및 Bitbucket과 같은 외부 저장소에 대한 지원이 포함되었습니다. 이 새로운 지원은 기존에 제공되던 개인 및 기업용 GitHub 저장소에 대한 지원에 추가됩니다. 이러한 새로운 저장소를 추가하면 이를 파이프라인에 직접 연결할 수도 있습니다. 이러한 저장소를 공개 클라우드 플랫폼이나 비공개 클라우드 또는 인프라 내에 호스팅할 수 있습니다. 또한 이 통합을 통해 Adobe 저장소와 지속적으로 코드를 동기화할 필요가 없으며 가져오기 요청을 메인 분기로 병합하기 전에 유효성 검사를 수행할 수 있는 기능이 제공됩니다.

이제 외부 저장소(GitHub 호스팅된 저장소 제외)와 **배포 트리거**&#x200B;를 **Git 변경 시**&#x200B;로 설정한 파이프라인이 자동으로 시작됩니다.

[Cloud Manager에서 외부 저장소 추가](/help/managing-code/external-repositories.md)를 참조하십시오.

![저장소 추가 대화 상자](/help/release-notes/assets/repositories-add-release-notes.png)

>[!NOTE]
>
>현재 기본 제공 가져오기 요청 코드 품질 검사는 GitHub 호스팅 저장소에만 적용되지만, 이 기능을 다른 Git 공급업체로 확장하기 위한 업데이트가 진행 중입니다.

이 새로운 기능을 테스트하고 피드백을 공유하는 데 관심이 있으시면 Adobe ID와 연결된 이메일 주소로 [Grp-CloudManager_BYOG@adobe.com](mailto:Grp-CloudManager_BYOG@adobe.com)에 이메일을 보내 주십시오. 사용하려는 Git 플랫폼과 비공개/공개 또는 기업 저장소 구조인지 여부를 반드시 포함해야 합니다.

### 스테이징 전용 및 프로덕션 전용 파이프라인 {#staging-production-only-pipelines}

Adobe는 [스테이징 전용 및 프로덕션 전용 파이프라인](/help/using/stage-prod-only.md)에 대한 지원을 시작합니다. 이 새로운 기능을 사용하면 전체 스택 프로덕션 배포 파이프라인을 보다 소규모의 전문화된 배포로 나눌 수 있습니다.

이 기능을 테스트하고 피드백을 제공하려면 Adobe ID와 연결된 이메일 주소로 [Grp-cloudmanager_splitpipelines@adobe.com](mailto:Grp-cloudmanager_splitpipelines@adobe.com)에 이메일을 보내 주십시오.



<!--
### Self-service Service Pack updates for AMS Cloud Manager customers 

As part of the early adopters program, Adobe Managed Services Cloud Manager customers can now perform self-service service pack updates through the **Cloud Manager** user interface. This feature is currently available *only for development environments* and includes limited error reporting for failures.  

Customers can check for service pack updates on the **Program Overview** page under the **Environments** section (**three-dot menu**).

![Check for updates menu option](/help/release-notes/assets/check-for-updates-1.png)

![Update Service Pack dialog box](/help/release-notes/assets/check-for-updates-2.png)

The installation and upgrade process can be tracked on the **Activity** page. 

Once the process is complete, customers must **approve the execution** for the service pack upgrade to finalize successfully.

![Approve service page update](/help/release-notes/assets/check-for-updates-3.png)

If you are interested in testing this new feature and sharing your feedback, contact your Adobe Customer Success Engineer.

See also [Service Pack Updates for Development Environments - Early Adopter](/help/using/service-packs-environments.md).
-->



## 버그 수정 {#bug-fixes}

* A

알려진 문제 {#known-issues}

* A —>
