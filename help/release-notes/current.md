---
title: Cloud Manager 2025.1.0 릴리스 정보
description: Adobe Managed Services용 Cloud Manager 2025.1.0 릴리스에 대해 알아봅니다.
feature: Release Information
source-git-commit: c25508b24f00b8f8cfa7bae3cc4b0d6ecf684db3
workflow-type: tm+mt
source-wordcount: '193'
ht-degree: 35%

---

# Adobe Managed Services용 Cloud Manager 2025.1.0 릴리스 정보 {#release-notes}

<!-- RELEASE WIKI  https://wiki.corp.adobe.com/display/DMSArchitecture/Cloud+Manager+2024.12.0+Release -->

Adobe Managed Services용 [!UICONTROL Cloud Manager] 2025.1.0 릴리스에 대해 알아봅니다.

>[!NOTE]
>
>[최신 Adobe Experience Manager as a Cloud Service 릴리스 정보](https://experienceleague.adobe.com/ko/docs/experience-manager-cloud-service/content/release-notes/home)를 참조하십시오.

## 릴리스 일자 {#release-date}

<!-- SAVE FOR FUTURE POSSIBLE USE No notable bugs or features for the September release of Cloud Manager. -->

[!UICONTROL Cloud Manager] 2025.1.0의 릴리스 날짜는 2024년 1월 22일 수요일입니다.

다음 릴리스는 2025년 2월 13일 금요일에 예정되어 있습니다.

## 새로운 기능 {#what-is-new}

**코드 품질 규칙:** Cloud Manager 코드 품질 단계는 2025년 2월 13일 목요일에 예정된 Cloud Manager 2025.2.0 릴리스에서 SonarQube Server 9.9를 사용하여 시작됩니다.

준비를 위해 업데이트된 SonarQube 규칙을 [코드 품질 규칙](/help/using/code-quality-testing.md#code-quality-testing-step)에서 사용할 수 있습니다.

다음 파이프라인 텍스트 변수(아래 스크린샷 참조)를 설정하여 새 규칙을 &quot;조기 확인&quot;할 수 있습니다.

`CM_BUILD_IMAGE_OVERRIDE` = `self-service-build:sonar-99-upgrade-java17or21`

또한 다음 변수를 설정하여 동일한 커밋에 대해 코드 품질 단계가 실행되도록 합니다(일반적으로 동일한 `commitId`에 대해 건너뜀).

`CM_DISABLE_BUILD_REUSE` = `true`

![변수 구성 페이지](/help/release-notes/assets/variables-config.png)

>[!NOTE]
>
>Adobe은 기본 프로덕션 파이프라인과 동일한 분기로 구성된 새 CI/CD 코드 품질 파이프라인을 만들 것을 권장합니다. 2025년 2월 13일 릴리스에서 적절한 변수를 *이전*&#x200B;으로 설정하여 새로 적용된 규칙이 차단기를 도입하지 않는지 확인하십시오.

<!-- ## Early adoption program {#early-adoption}

Be a part of Cloud Manager's early adoption program and have a chance to test upcoming features. -->


<!-- ## Bug fixes {#bug-fixes}

* A

Known Issues {#known-issues}

* A -->
