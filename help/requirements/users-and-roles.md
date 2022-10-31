---
title: 사용자 및 역할 추가
description: Admin Console을 사용하여 사용자 및 역할을 추가하고 프로필을 만드는 방법에 대해 알아봅니다.
exl-id: 40086cf0-a1c4-4dde-9dbf-84ea5fa53b84
source-git-commit: dd96d773ea3e6b9c45886fe41b28d3dd70cb8a61
workflow-type: tm+mt
source-wordcount: '780'
ht-degree: 22%

---


# 사용자 및 역할 추가 {#add-users-and-roles}

의 많은 기능 [!UICONTROL Cloud Manager] 사용하려면 특정 권한이 필요합니다. 예를 들어 특정 사용자만 프로그램에 대한 KPI(주요 성과 지표)를 설정할 수 있습니다. 이러한 권한은 논리적으로 역할로 그룹화됩니다.

[!UICONTROL Cloud Manager] 현재 은 특정 기능의 가용성을 제어하는 4가지 역할을 정의합니다.

* 비즈니스 소유자
* 프로그램 관리자
* 배포 관리자
* 개발자

>[!NOTE]
>
>를 사용하려면 [!UICONTROL Cloud Manager]에는 Adobe ID과 Adobe Managed Services 제품 컨텍스트가 있어야 합니다.

## 역할 정의 {#role-definitions}

이 표에는 역할이 요약되어 있습니다.

| [!UICONTROL Cloud Manager] 역할 | 설명 |
|--- |--- |
| 비즈니스 소유자 | 이 사용자는 KPI를 정의하고, 프로덕션 구축을 승인하며, 필요한 경우 중요한 3계층 오류를 재정의할 책임이 있습니다. |
| 프로그램 관리자 | 이 사용자는 [!UICONTROL Cloud Manager] 팀 설정을 수행하려면 상태를 검토하고 KPI를 확인하고 필요한 경우 중요한 3계층 오류를 승인할 수 있습니다. |
| 배포 관리자 | 이 사용자는 배포 작업을 관리하고 [!UICONTROL Cloud Manager] 스테이징/프로덕션 배포를 실행하려면 CI/CD 파이프라인을 편집하고, 필요한 경우 중요한 3계층 오류를 승인하고, git 리포지토리에 액세스할 수 있습니다. |
| 개발자 | 이 사용자는 사용자 지정 애플리케이션 코드를 개발하고 테스트하며 주로 를 사용합니다 [!UICONTROL Cloud Manager] 배포 상태를 보고 코드 커밋에 대한 git 리포지토리에 액세스할 수 있습니다. |
| 고객 성공 엔지니어 | 이 사용자는 일반적으로 AMS 고객에 대한 고객 성공을 지원하고 [!UICONTROL Cloud Manager] 를 사용하도록 선택할 수 있습니다. |
| 콘텐츠 작성자 | 일반적으로 이 사용자는 [!UICONTROL Cloud Manager] 하지만 [!UICONTROL Cloud Manager] 프로그램 전환기를 사용하여 AEM에 액세스합니다. |

>[!NOTE]
>
>Admin Console의 개발자 모습은 의 개발자 역할과 관련이 없습니다 [!UICONTROL Cloud Manager].

## Admin Console을 사용하여 프로필 만들기 {#using-admin-console-to-create-a-profile}

[!UICONTROL Cloud Manager] 역할은 Admin Console에서 관리됩니다. 특정 역할 멤버십은 사용자를 [!UICONTROL Cloud Manager] 제품 프로필 .

Adobe Admin Console을 통해 조직 전체에 대한 Adobe 권한을 한 곳에서 관리할 수 있습니다. Adobe Admin Console에 대한 자세한 내용은 [Admin Console](https://helpx.adobe.com/kr/enterprise/using/admin-console.html) 설명서를 참조하십시오.

에 적절한 역할 기반 권한을 제공하기 위해 [!UICONTROL Cloud Manager] 사용자, 고객 조직의 관리자는 [!UICONTROL AEM Managed Services] 네 개 모두에 해당하는 제품 컨텍스트 [!UICONTROL Cloud Manager] 역할:

* 비즈니스 소유자
* 배포 관리자
* 개발자
* 프로그램 관리자

Admin Console을 사용하여 이러한 제품 프로필에 사용자/그룹을 만들거나 추가할 수 있습니다.

1. Admin Console에 로그인합니다. [`https://adminconsole.adobe.com`.](https://adminconsole.adobe.com)

1. 을(를) 클릭합니다. **개요** 탭에서 수정할 제품을 클릭합니다 **제품 및 서비스** 카드. 목록에 없으면 **제품** 탭을 사용하여 제품을 찾아 클릭합니다.

   ![Admin Console 개요 탭](/help/assets/admin-console-overview.png)

1. 설정 **제품** 탭에서 제품 프로필에 사용자/그룹을 추가할 환경을 클릭합니다.

   ![Admin Console 제품 탭](/help/assets/admin-console-product.png)

1. 설정 **제품 프로필** 제품의 탭에서 **새 프로필** 새 프로필을 추가하려면

   ![새 프로필](/help/assets/admin-console-product-profiles.png)

1. 새 역할을 설정할 정보를 제공합니다. [!UICONTROL Cloud Manager].

   * **프로필 이름** - **프로필 이름** 혼동을 방지하기 위해서는 **권장 프로필 이름** 열.
   * **표시 이름** - **표시 이름** 에 정의된 기술 값이어야 합니다. [!UICONTROL Cloud Manager] (다음 표를 참조하십시오.)
   * **권한 그룹** - 프로필에 대한 권한 그룹을 선택할 수 있습니다(항상 사용할 수는 없음).

   ![새 프로필 만들기](/help/assets/screen_shot_2018-05-04at171819.png)

   | 역할 | 표시 이름(필수) | 권장 프로필 이름 |
   |---|---|---|
   | 비즈니스 소유자 | `CM_BUSINESS_OWNER_ROLE_PROFILE` | [!UICONTROL Cloud Manager] - 비즈니스 소유자 역할 |
   | 배포 관리자 | `CM_DEPLOYMENT_MANAGER_ROLE_PROFILE` | [!UICONTROL Cloud Manager] - 배포 관리자 역할 |
   | 개발자 | `CM_DEVELOPER_ROLE_PROFILE` | [!UICONTROL Cloud Manager] - 개발자 역할 |
   | 프로그램 관리자 | `CM_PROGRAM_MANAGER_ROLE_PROFILE` | [!UICONTROL Cloud Manager] - 프로그램 관리자 역할 |


1. 클릭 **완료** 새 프로필을 저장하려면 을 클릭합니다.

## 사용자 또는 사용자 그룹에 프로필 할당 {#assign-profiles}

제품 프로필을 만들면 사용자 또는 사용자 그룹을 지정할 수 있습니다.

1. Admin Console에 로그인합니다. [`https://adminconsole.adobe.com`.](https://adminconsole.adobe.com)

1. Admin Console에서 **사용자** 탭.

   ![사용자 탭](/help/assets/admin-console-users.png)

1. 클릭 **사용자** 왼쪽 탐색 패널에서 사용자를 클릭하여 수정합니다.

1. 에서 줄임표 단추를 클릭합니다. **제품** 섹션을 선택하고 **편집**.

   ![사용자 편집](/help/assets/admin-console-edit-user.png)

1. 에서 **제품 및 사용자 그룹 편집** 대화 상자에서 더하기 단추를 클릭하고 사용자에게 할당할 프로필을 선택합니다.

   * 사용자가 이미 역할에 할당되어 있는 경우 더하기 단추는 편집 단추(연필)이지만 동일한 방식으로 작동합니다.

   ![제품 및 사용자 그룹 편집](/help/assets/admin-console-edit-products-and-user-groups.png)

1. 클릭 **저장** 프로필을 사용자에게 저장하려면 을 클릭합니다.

동일한 단계를 반복하여 사용자 그룹에 프로필을 할당하지만 **사용자 그룹** 의 왼쪽 탐색 패널에서 **사용자** 탭. 사용자 그룹을 클릭하고 **지정된 제품 프로필** 탭을 클릭하고 **제품 프로필 할당** 프로필을 할당하려면 다음과 같이 하십시오.

![그룹에 프로필 할당](/help/assets/admin-console-edit-user-groups.png)
