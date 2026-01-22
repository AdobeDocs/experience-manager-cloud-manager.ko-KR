---
title: Cloud Manager 2026.1.0 릴리스 정보
description: Adobe Managed Services용 Cloud Manager 2026.1.0 릴리스에 대해 알아봅니다.
feature: Release Information
exl-id: cc1dc94b-129d-4de7-8e57-8fc5dcba7d9f
source-git-commit: 6279792f05ec04c82634d255dad7264f6d0cef64
workflow-type: tm+mt
source-wordcount: '660'
ht-degree: 63%

---

# Adobe Managed Services용 Cloud Manager 2026.1.0 릴리스 정보 {#release-notes}

<!-- RELEASE WIKI  https://wiki.corp.adobe.com/display/DMSArchitecture/Cloud+Manager+2025.04.0+Release -->

Adobe Managed Services용 [!UICONTROL Cloud Manager] 2026.1.0 릴리스에 대해 알아봅니다.

또한 [최신 Adobe Experience Manager as a Cloud Service 릴리스 정보](https://experienceleague.adobe.com/ko/docs/experience-manager-cloud-service/content/release-notes/home)도 살펴보십시오.

## 릴리스 일자 {#release-date}

[!UICONTROL Cloud Manager] 2026.1.0의 릴리스 날짜는 2026년 1월 22일 목요일입니다.

<!-- There are no significant new features or bug fixes in the May Cloud Manager release. -->

다음 릴리스는 2026년 2월 5일 금요일에 예정되어 있습니다.

<!-- SAVE FOR FUTURE POSSIBLE USE There are no significant new features or bug fixes in the May Cloud Manager release. -->

## 새로운 기능 {#what-is-new}

* **이제 구성 파이프라인이 관리 암호를 지원합니다**

  이제 사용자는 Cloud Manager 구성 파이프라인에서 직접 비밀을 추가하고 관리할 수 있습니다. 이러한 비밀은 파이프라인 구성 사양의 값을 안전하게 재정의하고 유연한 환경별 배포를 지원합니다.

  ![선택한 파이프라인에 대한 드롭다운 메뉴의 변수 보기/편집 옵션](/help/release-notes/assets/view-edit-variables-option.png)
  *선택한 파이프라인에 대한 드롭다운 메뉴의 변수 보기/편집 옵션*

  ![변수 구성 대화 상자&#x200B;](/help/release-notes/assets/view-edit-variables-variablesconfig-dialogbox.png)*변수 구성 대화 상자*

* **안정성, 성능 및 안정성 향상**

  이 릴리스에는 Cloud Manager의 안정성, 성능 및 안정성을 개선한 최적화 및 유지 관리 업데이트가 포함됩니다.


## Beta 프로그램 {#beta-program}

Cloud Manager의 Beta 프로그램에 참여하여 일반 릴리스 전에 예정된 기능에 독점적으로 액세스할 수 있습니다.

현재 제공되는 기회는 다음과 같습니다.

### Experience Hub 확장성 및 사용자 정의 {#exp-hub-extensibility}

[Experience Hub](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/experience-hub/experience-hub)는 조직의 요구 사항에 맞게 사용자 정의된 AEM에 대한 진입점 역할을 합니다. Experience Hub에서 손쉽게 활성화할 수 있도록 기존 AEM UI 확장 기능에 대해 Adobe에 알려 주십시오.

![Experience Hub 확장성 및 사용자 정의 워크플로의 다이어그램](/help/release-notes/assets/experience-hub-extensibility-customization.png)

조직의 대시보드를 확장하고 개인화할 수 있도록 Experience Hub에 사용자 정의 경험을 임베드합니다. Adobe의 기본 제공 위젯 외에 [UI 확장성](https://developer.adobe.com/uix/docs/) 프레임워크를 사용하여 나만의 위젯을 추가합니다. JavaScript 기반 UI 앱을 빌드하고 이를 사용자에게 제공하여 비즈니스별 요구 사항 및 워크플로를 충족합니다.

Beta에 관심이 있으신가요? Adobe OrgID 및 만들고자 하는 사용자 정의에 대한 간단한 설명을 첨부한 이메일을 [beta_exphubextensibility@adobe.com](mailto:beta_exphubextensibility@adobe.com)으로 보내 주시기 바랍니다.

### 모듈 캐싱을 통한 빌드 속도 향상 {#quick-build-cm-pipelines}

새 빌드 모델은 모듈 수준 캐싱을 사용하여 전체 저장소가 아닌 변경된 모듈만 컴파일함으로써 빌드 시간을 단축합니다. 코드 품질, 전체 스택 및 스테이지 전용 파이프라인에 적용됩니다.

![두 가지 빌드 전략 옵션(전체 빌드 및 스마트 빌드)을 표시하는 비프로덕션 파이프라인 편집 대화 상자](/help/release-notes/assets/non-production-pipeline-edit.png)
*두 가지 빌드 전략 옵션(전체 빌드 및 스마트 빌드)을 표시하는 비프로덕션 파이프라인 편집 대화 상자*

**파이프라인 추가/편집** 대화 상자의 **Source 코드** 탭에서 새 **빌드 전략** 섹션을 통해 다음 빌드 옵션 중 하나를 선택할 수 있습니다.

* **전체 빌드** — 실행할 때마다 저장소의 모든 모듈을 빌드합니다.
* **스마트 빌드** — 마지막 커밋 이후에 변경된 모듈만 빌드하므로 전체 빌드 시간이 단축됩니다.

**스마트 빌드**&#x200B;를 사용하는 파이프라인을 제어합니다. Beta를 실행하는 동안 이 옵션은 **코드 품질** 및 **개발 배포** 파이프라인에만 나타납니다.

관심이 있으신가요? Adobe OrgID 및 프로그램 ID를 첨부한 이메일을 [beta_quickbuild_cmpipelines@adobe.com](mailto:beta_quickbuild_cmpipelines@adobe.com)으로 보내 주시기 바랍니다.

<!-- You can deactivate incremental builds at the pipeline level by setting the property `CM_BUILD_DISABLE_MODULE_CACHING` to `true` (effective during the `BUILD` step). For how to add pipeline variables, see [Pipeline variables](/help/getting-started/build-environment.md#pipeline-variables). -->


### Git(BYOG) 가져오기 {#gitlab-bitbucket-azure-vsts}

<!-- BOTH CS & AMS -->

이제 고객은 Azure DevOps Git 저장소를 Cloud Manager에 온보딩할 수 있으며, 최신 Azure DevOps와 이전 VSTS(Visual Studio Team Services) 저장소가 모두 지원됩니다.

* Edge Delivery Services 사용자의 경우 온보딩된 저장소를 사용하여 사이트 코드를 동기화하고 배포할 수 있습니다.
* AEM as a Cloud Service와 Adobe Managed Services(AMS) 사용자의 경우 저장소를 전체 스택 파이프라인과 프론트엔드 파이프라인 모두에 연결할 수 있습니다.

추가 파이프라인 유형과 코드 품질 파이프라인을 통한 가져오기 요청 유효성 검사도 곧 지원할 예정입니다.

[Cloud Manager에서 외부 저장소 추가](/help/managing-code/external-repositories.md)를 참조하십시오.

![저장소 추가 대화 상자](/help/release-notes/assets/azure-repo.png)

이 새로운 기능을 테스트하고 피드백을 공유하는 데 관심이 있으시면 Adobe ID와 연결된 이메일 주소로 [Grp-CloudManager_BYOG@adobe.com](mailto:grp-cloudmanager_byog@adobe.com)에 이메일을 보내 주십시오. 사용하려는 Git 플랫폼과 비공개/공개 또는 기업 저장소 구조인지 여부를 반드시 포함해야 합니다.

#### 액세스 토큰 관리{#manage-access-tokens}

Cloud Manager에서 **액세스 토큰 관리**&#x200B;를 사용하여 GitHub Enterprise, GitLab, Bitbucket, Azure DevOps와 같은 외부 BYOG 저장소와 관련된 액세스 토큰을 보고, 이름을 변경하고, 삭제할 수 있습니다.

[액세스 토큰 관리](/help/managing-code/manage-access-tokens.md)를 참조하십시오.

<!-- If you are interested in testing this new feature and sharing your feedback, send an email to [Grp-CloudManager_BYOG@adobe.com](mailto:grp-cloudmanager_byog@adobe.com) from your email address associated with your Adobe ID. -->

## 버그 수정 {#bug-fixes}

AMS 릴리스의 2026년 1월 Cloud Manager에는 중요한 버그 수정이 없습니다.

<!--
Known Issues {#known-issues}

* A -->
