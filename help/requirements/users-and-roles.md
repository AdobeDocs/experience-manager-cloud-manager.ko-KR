---
title: 사용자 및 역할 추가
description: Admin Console을 사용하여 사용자 및 역할을 추가하고 프로필을 만드는 방법에 대해 알아봅니다.
exl-id: 40086cf0-a1c4-4dde-9dbf-84ea5fa53b84
source-git-commit: b0dbb602253939464ff034941ffbad84b7df77df
workflow-type: ht
source-wordcount: '536'
ht-degree: 100%

---


# 사용자 및 역할 추가 {#add-users-and-roles}

[!UICONTROL Cloud Manager]의 많은 기능을 사용하려면 특정 권한이 필요합니다. 예를 들어 특정 사용자만 프로그램에 대한 KPI(주요 성과 지표)를 설정할 수 있습니다. 이러한 권한은 논리적으로 역할로 그룹화됩니다.

[!UICONTROL Cloud Manager]는 현재 특정 기능의 가용성을 제어하는 네 가지 역할을 정의합니다.

* 비즈니스 소유자
* 프로그램 관리자
* 배포 관리자
* 개발자

>[!NOTE]
>
>[!UICONTROL Cloud Manager]를 사용하려면 Adobe ID와 Adobe 관리 서비스 제품 컨텍스트가 있어야 합니다.

## 역할 정의 {#role-definitions}

이 표에는 역할이 요약되어 있습니다.

| [!UICONTROL Cloud Manager] 역할 | 설명 |
|--- |--- |
| 비즈니스 소유자 | 이 사용자는 KPI를 정의하고, 프로덕션 구축을 승인하며, 필요한 경우 중요한 3계층 오류를 재정의할 책임이 있습니다. |
| 프로그램 관리자 | 이 사용자는 [!UICONTROL Cloud Manager]를 사용하여 팀 설정, 상태 검토, KPI 보기 및 필요한 경우 중요한 3계층 오류를 승인할 수 있습니다. |
| 배포 관리자 | 이 사용자는 배포 작업을 관리하고 [!UICONTROL Cloud Manager]를 사용하여 스테이징/프로덕션 배포를 실행하고, CI/CD 파이프라인을 편집하고, 필요한 경우 중요한 3계층 오류를 승인하며, git 저장소에 액세스할 수 있습니다. |
| 개발자 | 이 사용자는 사용자 정의 애플리케이션 코드를 개발 및 테스트하고 주로 [!UICONTROL Cloud Manager]를 사용하여 배포 상태를 보고 코드 커밋을 위해 git 저장소에 액세스할 수 있습니다. |
| 고객 성공 엔지니어 | 이 사용자는 일반적으로 AMS 고객을 위해 고객의 성공을 지원하고 CSE 감독이 필요한 배포 실행을 위해 [!UICONTROL Cloud Manager]와 상호 작용합니다. |
| 콘텐츠 작성자 | 이 사용자는 일반적으로 [!UICONTROL Cloud Manager]와 상호 작용하지 않지만 [!UICONTROL Cloud Manager] 프로그램 스위처를 사용하여 AEM에 액세스할 수 있습니다. |

>[!NOTE]
>
>Admin Console의 개발자는 [!UICONTROL Cloud Manager]의 개발자 역할과 관련이 없습니다.

## Admin Console을 사용하여 프로필 만들기 {#using-admin-console-to-create-a-profile}

[!UICONTROL Cloud Manager] 역할은 Admin Console에서 관리합니다. [!UICONTROL Cloud Manager] 제품 프로필에 사용자를 추가하여 특정 역할 멤버십을 제공합니다.

Adobe Admin Console을 통해 조직 전체에 대한 Adobe 권한을 한 곳에서 관리할 수 있습니다. Adobe Admin Console에 대한 자세한 내용은 [Admin Console](https://helpx.adobe.com/kr/enterprise/using/admin-console.html) 설명서를 참조하십시오.

>[!NOTE]
>
>Admin Console에 액세스하고 팀(사용자 및 역할)을 설정하려면 [`https://adminconsole.adobe.com`](https://adminconsole.adobe.com)를 방문하십시오.

[!UICONTROL Cloud Manager] 사용자에게 적절한 역할 기반 권한을 제공하기 위해 고객 조직의 관리자는 4개의 [!UICONTROL Cloud Manager] 역할에 해당하는 [!UICONTROL AEM Managed Services] 제품 컨텍스트에서 새 제품 프로필을 만들어야 합니다.

* 비즈니스 소유자
* 배포 관리자
* 개발자
* 프로그램 관리자

Admin Console을 사용하여 이러한 제품 프로필에 사용자/그룹을 만들거나 추가할 수 있습니다.

1. Admin Console에 로그인한 후 **새 프로필**&#x200B;을 클릭하여 새 프로필을 추가합니다.

   ![새 프로필](/help/assets/admin_console_roles-1.png)

1. [!UICONTROL Cloud Manager]에 대한 새 역할을 설정하는 데 필요한 정보를 제공합니다.

   * **프로필 이름**
   * **표시 이름**
   * **권한 그룹**

1. **완료**&#x200B;를 클릭하여 프로필 생성 단계를 완료합니다.

제품 프로필을 만들 때 **표시 이름**&#x200B;은 [!UICONTROL Cloud Manager]에서 정의한 기술 값이어야 합니다(다음 표 참조). **프로필 이름**&#x200B;은 어떤 것이든 사용할 수 있지만 혼동을 피하기 위해 **권장 프로필** 이름 열의 값을 사용하는 것이 좋습니다. 이렇게 하려면 제품 프로필을 만들 때 **프로필 이름과 동일** 선택을 취소하고 해당 값을 **표시 이름**&#x200B;으로 지정합니다.

| **역할** | **표시 이름(필수)** | **권장 프로필 이름** |
|---|---|---|
| 비즈니스 소유자 | `CM_BUSINESS_OWNER_ROLE_PROFILE` | [!UICONTROL Cloud Manager] - 비즈니스 소유자 역할 |
| 배포 관리자 | `CM_DEPLOYMENT_MANAGER_ROLE_PROFILE` | [!UICONTROL Cloud Manager] - 배포 관리자 역할 |
| 개발자 | `CM_DEVELOPER_ROLE_PROFILE` | [!UICONTROL Cloud Manager] - 개발자 역할 |
| 프로그램 관리자 | `CM_PROGRAM_MANAGER_ROLE_PROFILE` | [!UICONTROL Cloud Manager] - 프로그램 관리자 역할 |

![새 프로필 만들기](/help/assets/screen_shot_2018-05-04at171819.png)

제품 프로필을 만든 후에는 이러한 제품 프로필에 사용자(또는 그룹)를 추가할 수 있습니다.

![사용자 편집](/help/assets/image2018-4-9_15-19-26.png)

![사용자 그룹](/help/assets/image2018-4-9_15-16-47.png)
