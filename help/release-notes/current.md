---
title: Cloud Manager 2026.3.0 릴리스 노트
description: Adobe Managed Services의 Cloud Manager 2026.3.0 릴리스에 대해 알아봅니다.
feature: Release Information
exl-id: cc1dc94b-129d-4de7-8e57-8fc5dcba7d9f
source-git-commit: b7e651b72d1943aef69c1c69915d4752a6163931
workflow-type: tm+mt
source-wordcount: '461'
ht-degree: 16%

---

# Adobe Managed Services의 Cloud Manager 2026.3.0 릴리스 노트 {#release-notes}

<!-- RELEASE WIKI  https://wiki.corp.adobe.com/display/DMSArchitecture/Cloud+Manager+2025.04.0+Release -->

Adobe Managed Services의 [!UICONTROL Cloud Manager] 2026.3.0 릴리스에 대해 알아봅니다.

또한 [최신 Adobe Experience Manager as a Cloud Service 릴리스 정보](https://experienceleague.adobe.com/ko/docs/experience-manager-cloud-service/content/release-notes/home)도 살펴보십시오.

## 릴리스 일자 {#release-date}

[!UICONTROL Cloud Manager] 2026.3.0의 릴리스 날짜는 2026년 3월 5일 목요일입니다.
<!-- There are no significant new features or bug fixes in the May Cloud Manager release. -->

다음 예정 릴리스는 2026년 4월 2일 목요일입니다.

<!-- SAVE FOR FUTURE POSSIBLE USE There are no significant new features or bug fixes in the May Cloud Manager release. -->

## 새로운 기능 {#what-is-new}

* **AEM Experience Hub에서 UI 확장성 지원**
이제 [AEM Experience Hub](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/experience-hub/experience-hub)의 UI 확장 지원이 활성화되었으므로 개발자는 Adobe App Builder을 사용하여 빌드된 사용자 지정 기능 및 위젯으로 인터페이스를 확장할 수 있습니다.

  자세한 내용은 [AEM Experience Hub](https://developer.adobe.com/uix/docs/services/aem-experience-hub/)를 참조하세요.

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

<!--
### Experience Hub Extensibility and Customization {#exp-hub-extensibility}

[Experience Hub](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/experience-hub/experience-hub) serves as your entry point to AEM, customized for your organization's needs. Tell Adobe about your existing AEM UI extensions so they can help you enable them in Experience Hub with minimal effort.

![Diagram of Experience Hub extensibility and customization workflow](/help/release-notes/assets/experience-hub-extensibility-customization.png)

Embed custom experiences in Experience Hub to extend and personalize your organization's dashboard. In addition to Adobe's built-in widgets, add your own using the [UI Extensibility](https://developer.adobe.com/uix/docs/) framework. Build JavaScript-based UI apps and surface them to your users to meet business-specific requirements and workflows. 

Interested in the beta? Email [beta_exphubextensibility@adobe.com](mailto:beta_exphubextensibility@adobe.com) with your Adobe OrgID and a short description of the customization you intend to create.
-->

### 모듈 캐싱을 통한 빌드 속도 향상 {#quick-build-cm-pipelines}

새 빌드 모델은 모듈 수준 캐싱을 사용하여 전체 저장소가 아닌 변경된 모듈만 컴파일함으로써 빌드 시간을 단축합니다. 코드 품질 및 전체 스택 파이프라인에 적용됩니다.

![두 가지 빌드 전략 옵션(전체 빌드 및 스마트 빌드)을 표시하는 비프로덕션 파이프라인 편집 대화 상자](/help/release-notes/assets/non-production-pipeline-edit.png)
*두 가지 빌드 전략 옵션(전체 빌드 및 스마트 빌드)을 표시하는 비프로덕션 파이프라인 편집 대화 상자*

**파이프라인 추가/편집** 대화 상자의 **Source 코드** 탭에서 새 **빌드 전략** 섹션을 통해 다음 빌드 옵션 중 하나를 선택할 수 있습니다.

* **전체 빌드** — 실행할 때마다 저장소의 모든 모듈을 빌드합니다.
* **스마트 빌드** — 마지막 커밋 이후에 변경된 모듈만 빌드하므로 전체 빌드 시간이 단축됩니다.

[비프로덕션 파이프라인 추가](/help/using/non-production-pipelines.md#add-non-production-pipeline) 및 [비프로덕션 파이프라인에서의 스마트 빌드 사용 정보](/help/using/non-production-pipelines.md#about-smart-build)를 참조하십시오.

**스마트 빌드**&#x200B;를 사용하는 파이프라인을 제어합니다. Beta를 실행하는 동안 이 옵션은 **코드 품질** 및 **개발 전체 스택 코드 배포** 파이프라인에만 나타납니다.

관심이 있으신가요? Adobe OrgID 및 프로그램 ID를 첨부한 이메일을 [beta_quickbuild_cmpipelines@adobe.com](mailto:beta_quickbuild_cmpipelines@adobe.com)으로 보내 주시기 바랍니다.

<!-- You can deactivate incremental builds at the pipeline level by setting the property `CM_BUILD_DISABLE_MODULE_CACHING` to `true` (effective during the `BUILD` step). For how to add pipeline variables, see [Pipeline variables](/help/getting-started/build-environment.md#pipeline-variables). -->

## 버그 수정 {#bug-fixes}

AMS 릴리스의 2026년 3월 Cloud Manager에는 중요한 버그 수정이 없습니다.

<!--
Known Issues {#known-issues}

* A 
-->
