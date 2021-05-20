---
title: 사용자 및 역할 추가
seo-title: 사용자 및 역할 추가
description: 사용자 및 역할과 Admin Console을 사용하여 프로필을 만드는 방법에 대해 알아봅니다
seo-description: 사용자를 Admin Console의 Cloud Manager 제품 프로필에 추가하여 특정 역할 멤버십을 할당할 수 있습니다. 자세한 내용은 이 섹션을 참조하십시오.
uuid: fa204c28-83df-48bb-8360-e158f080dee7
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: requirements
discoiquuid: 1b421993-22c3-4de0-ba64-c1080d07ad5e
feature: 사용자 역할
exl-id: 40086cf0-a1c4-4dde-9dbf-84ea5fa53b84
source-git-commit: 43bb3c477ef9c1ce178509b8180479d7616edc66
workflow-type: tm+mt
source-wordcount: '632'
ht-degree: 4%

---

# 사용자 및 역할 추가 {#add-users-and-roles}

[!UICONTROL Cloud Manager]의 많은 기능을 사용하려면 특정 권한이 필요합니다. 예를 들어 특정 사용자만 프로그램에 대한 주요 성과 지표(KPI)를 설정할 수 있습니다. 이러한 권한은 논리적으로 역할로 그룹화됩니다.

[!UICONTROL Cloud Manager] 현재 은 특정 기능의 가용성을 제어하는 4가지 역할을 정의합니다.

* 비즈니스 소유자
* 프로그램 관리자
* 배포 관리자
* 개발자

>[!CAUTION]
>
>[!UICONTROL Cloud Manager]을 사용하려면 Adobe ID과 Adobe Managed Services 제품 컨텍스트가 있어야 합니다.

## 역할 정의 {#role-definitions}

>[!NOTE]
>
>Admin Console의 개발자 모습은 [!UICONTROL Cloud Manager]의 개발자 역할과 관련이 없습니다.

다음 표에는 역할이 요약되어 있습니다.

| [!UICONTROL Cloud Manager] 역할 | 설명 |
|--- |--- |
| 비즈니스 소유자 | KPI 정의, 프로덕션 배포 승인 및 중요한 3계층 실패 재정의에 책임이 있습니다. |
| 프로그램 관리자 | [!UICONTROL Cloud Manager] 을 사용하여 팀 설정, 상태 검토 및 KPI 보기를 수행합니다. 중요한 3계층 오류를 승인할 수 있습니다. |
| 배포 관리자 | 배포 작업을 관리합니다. [!UICONTROL Cloud Manager] 을 사용하여 스테이지/프로덕션 배포를 실행합니다. CI/CD 파이프라인을 편집할 수 있습니다. 중요한 3계층 오류를 승인할 수 있습니다. Git 리포지토리에 액세스할 수 있습니다. |
| 개발자 | 사용자 지정 응용 프로그램 코드를 개발하고 테스트합니다. 주로 [!UICONTROL Cloud Manager]을 사용하여 상태를 봅니다. 코드 커밋을 위해 Git 리포지토리에 액세스할 수 있습니다. |
| 고객 성공 엔지니어 | 일반적으로 AMS 고객에 대한 고객 성공을 지원합니다. CSE 감독이 필요한 배포를 실행할 목적으로 [!UICONTROL Cloud Manager]과 상호 작용합니다. |
| 컨텐츠 작성자 | 일반적으로 는 [!UICONTROL Cloud Manager]과 상호 작용하지 않습니다. [!UICONTROL Cloud Manager] 프로그램 전환기([!UICONTROL Experience Cloud]에서 탐색)를 사용하여 AEM에 액세스할 수 있습니다. |

## Admin Console을 사용하여 프로필 만들기 {#using-admin-console-to-create-a-profile}

역할은 Adobe Admin Console에서 [!UICONTROL Cloud Manager]에 대해 관리됩니다. 특정 역할 멤버십은 사용자를 Admin Console의 [!UICONTROL Cloud Manager] 제품 프로필에 추가하여 제공합니다.

사용자를 전체 조직에서 Adobe 권한을 관리하기 위한 중앙 위치인 Adobe Admin Console의 [!UICONTROL Cloud Manager] **제품 프로필**&#x200B;에 추가하여 특정 역할 멤버십을 할당할 수 있습니다. Adobe Admin Console에 대한 자세한 내용은 [Admin Console](https://helpx.adobe.com/kr/enterprise/using/admin-console.html)에 대한 설명서를 참조하십시오.

>[!NOTE]
>
>Admin Console에 액세스하여 팀(사용자 및 역할)을 설정하려면 브라우저를 열고 [https://adminconsole.adobe.com](https://adminconsole.adobe.com/enterprise)을 방문하십시오.

[!UICONTROL Cloud Manager] 사용자에게 적절한 역할 기반 권한을 제공하려면 고객의 **조직**&#x200B;에 있는 관리자가 [!UICONTROL AEM Managed Services] 제품 컨텍스트 아래에 새 제품 프로필을 만들어야 합니다.

[!UICONTROL Cloud Manager] 사용자에게 적절한 역할 기반 권한을 제공하려면 관리자로서 4개의 [!UICONTROL Cloud Manager] 역할 각각에 해당하는 [!UICONTROL AEM Managed Services] 제품 컨텍스트 아래에 4개의 새 제품 프로필을 만들어야 합니다.

* 비즈니스 소유자
* 배포 관리자
* 개발자
* 프로그램 관리자

아래 그림과 같이 [Admin Console](https://adminconsole.adobe.com/)을 사용하여 이러한 제품 프로필에 사용자/그룹을 만들거나 추가할 수 있습니다. [!UICONTROL Cloud Manager]

1. Admin Console에 로그인하고 **새 프로필**&#x200B;을 클릭하여 새 프로필을 추가합니다.

   ![](assets/admin_console_roles-1.png)

1. [!UICONTROL Cloud Manager]에 대한 새 역할을 설정하려면 필드를 입력합니다.

   새 프로필을 만들려면 **프로필 이름**, **표시 이름**&#x200B;을 입력합니다. 또한 프로필에 대한 **권한 그룹**&#x200B;을 선택할 수 있습니다.

   **완료**&#x200B;를 클릭하여 프로필 작성 단계를 완료합니다.

   >[!NOTE]
   >
   >이러한 제품 프로필을 만들 때 **표시 이름**&#x200B;은 [!UICONTROL Cloud Manager]에 정의된 기술 값이어야 합니다(아래 표 참조). 혼동을 방지하기 위해 아래의 *권장 프로필 이름* 열에 있는 값을 사용하는 것이 좋습니다. 그러나 **프로필 이름** 은 어떤 것이든 될 수 있습니다. 이렇게 하려면 제품 프로필을 만들 때 **프로필 이름**&#x200B;과 동일 을 선택하고 해당 값을 **표시 이름**&#x200B;으로 지정합니다.

   | **역할** | **표시 이름(필수)** | **권장 프로필 이름** |
   |---|---|---|
   | 비즈니스 소유자 | CM_BUSINESS_OWNER_ROLE_PROFILE | [!UICONTROL Cloud Manager] - 비즈니스 소유자 역할 |
   | 배포 관리자 | CM_DEPLOYMENT_MANAGER_ROLE_PROFILE | [!UICONTROL Cloud Manager] - 배포 관리자 역할 |
   | 개발자 | CM_DEVELOPER_ROLE_PROFILE | [!UICONTROL Cloud Manager] - 개발자 역할 |
   | 프로그램 관리자 | CM_PROGRAM_MANAGER_ROLE_PROFILE | [!UICONTROL Cloud Manager] - 프로그램 관리자 역할 |

   ![](assets/screen_shot_2018-05-04at171819.png)

1. 제품 프로필을 만들면 이러한 제품 프로필에 사용자(또는 그룹)를 추가할 수 있습니다.

   ![](assets/image2018-4-9_15-19-26.png)

   ![](assets/image2018-4-9_15-16-47.png)
