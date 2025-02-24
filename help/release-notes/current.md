---
title: Cloud Manager 2025.2.0 릴리스 정보
description: Adobe Managed Services용 Cloud Manager 2025.2.0 릴리스에 대해 알아봅니다.
feature: Release Information
exlid: 669b1f2d8fc68526eb091e0f93f70ab93033d193
exl-id: cc1dc94b-129d-4de7-8e57-8fc5dcba7d9f
source-git-commit: 51dd060ec9b922ace9ce537cac669c61154284e8
workflow-type: ht
source-wordcount: '241'
ht-degree: 100%

---

# Adobe Managed Services용 Cloud Manager 2025.2.0 릴리스 정보 {#release-notes}

<!-- RELEASE WIKI  https://wiki.corp.adobe.com/display/DMSArchitecture/Cloud+Manager+2025.02.0+Release -->

Adobe Managed Services용 [!UICONTROL Cloud Manager] 2025.2.0 릴리스에 대해 알아봅니다.

또한 [최신 Adobe Experience Manager as a Cloud Service 릴리스 정보](https://experienceleague.adobe.com/ko/docs/experience-manager-cloud-service/content/release-notes/home)도 살펴보십시오.

## 릴리스 일자 {#release-date}

[!UICONTROL Cloud Manager] 릴리스 2025.2.0의 릴리스 일자는 2025년 2월 13일 목요일입니다.

다음 릴리스는 2025년 3월 13일 목요일에 예정되어 있습니다.

## 새로운 기능 {#what-is-new}

<!-- * The AEM Code Quality step now uses SonarQube 9.9 Server, replacing the older 7.4 version. This upgrade brings additional security, performance, and code quality checks, offering more comprehensive analysis and coverage for your projects. --> <!-- CMGR-45683 -->

* **업그레이드된 SonarQube**

  2025년 2월 13일 목요일부터 Cloud Manager 코드 품질 단계는 SonarQube 9.9.5.90363을 사용합니다.

  [이 링크](/help/using/code-quality-testing.md#code-quality-testing-step)에서 AMS에 대해 사용할 수 있는 업데이트된 규칙은 Cloud Manager 파이프라인의 보안 점수와 코드 품질을 결정합니다.

* SonarQube 9.9는 이제 모든 고객을 위한 기본 코드 품질 스캐닝 엔진입니다.

* **Java 17 및 Java 21 빌드 환경 지원**

  이제 고객은 선택적으로 Java 17 또는 Java 21을 사용하여 빌드할 수 있으며, 이를 통해 성능 개선과 새로운 언어 기능의 이점을 누릴 수 있습니다. Maven 프로젝트 설명 및 특정 라이브러리 버전 업데이트를 포함한 구성 단계에 대해 [빌드 환경](/help/getting-started/build-environment.md)을 참조하십시오.

  >[!NOTE]
  >클라우드 서비스 환경에서 빌드 버전이 Java 17 또는 Java 21로 설정된 경우 런타임은 기본적으로 Java 21로 설정됩니다.

* **콘텐츠 사본 유효성 검사 확장됨**

  콘텐츠 사본 유효성 검사 규칙이 업데이트되었습니다. 이번 릴리스에서는 소스 또는 대상 환경에서 활성 파이프라인 실행이 있는 경우 사용자는 더 이상 콘텐츠 복사를 트리거할 수 없습니다. 사용자는 콘텐츠 복사를 시작하기 전에 진행 중인 모든 파이프라인 실행이 완료될 때까지 기다려야 합니다.

<!-- 
## Early adoption program {#early-adoption}

Be a part of Cloud Manager's early adoption program and have a chance to test upcoming features.

### Bring Your Own Git - now with support for GitLab and Bitbucket {#gitlab-bitbucket}

The **Bring Your Own Git** feature has been expanded to include support for external repositories, such as GitLab and Bitbucket. This new support is in addition to the already existing support for private and enterprise GitHub repositories. When you add these new repos, you can also link them directly to your pipelines. You can host these repositories on public cloud platforms or within your private cloud or infrastructure. This integration also removes the need for constant code synchronization with the Adobe repository and provides the ability to validate pull requests before merging them into a main branch.

Pipelines using external repositories (excluding GitHub-hosted ones) and the **Deployment Trigger** set to **On Git Changes** now start automatically.

See [Add external repositories in Cloud Manager](/help/managing-code/external-repositories.md).

![Add Repository dialog box](/help/release-notes/assets/repositories-add-release-notes.png)

>[!NOTE]
>
>Currently, the out-of-the-box pull request code quality checks are exclusive to GitHub-hosted repositories, but an update to extend this functionality to other Git vendors is in the works.

If you are interested in testing this new feature and sharing your feedback, send an email to [Grp-CloudManager_BYOG@adobe.com](mailto:Grp-CloudManager_BYOG@adobe.com) from your email address associated with your Adobe ID. Be sure to include which Git platform you want to use and whether you are on a private/public or enterprise repository structure. -->


<!-- ## Bug fixes {#bug-fixes}

* A

Known Issues {#known-issues}

* A -->
