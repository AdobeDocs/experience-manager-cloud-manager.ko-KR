---
title: 사용자 및 역할 추가
seo-title: 사용자 및 역할 추가
description: 'null'
seo-description: 관리 콘솔에서 Cloud Manager 제품 프로필에 사용자를 추가하여 특정 역할 멤버십을 할당할 수 있습니다. 자세한 내용은 이 섹션을 참조하십시오.
uuid: fa204c28-83df-48bb-8360-e158f080dee7
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: requirements
discoiquuid: 1b421993-22c3-4de0-ba64-c1080d07ad5e
translation-type: tm+mt
source-git-commit: a96500b57c980d31d3a70341d8be7b92ae73a1c5

---


# 사용자 및 역할 추가 {#add-users-and-roles}

의 많은 기능을 사용하려면 특정 권한이 [!UICONTROL Cloud Manager] 필요합니다. 예를 들어 특정 사용자만 프로그램에 대한 주요 성과 지표(KPI)를 설정할 수 있습니다. 이러한 권한은 논리적으로 역할로 그룹화됩니다.

[!UICONTROL Cloud Manager] 현재 특정 기능의 가용성을 제어하는 사용자의 4가지 역할을 정의합니다.

* 비즈니스 소유자
* 프로그램 관리자
* 배포 관리자
* 개발자

>[!CAUTION]
>
>사용하려면 [!UICONTROL Cloud Manager]Adobe ID와 Adobe Managed Services 제품 컨텍스트가 있어야 합니다.

## 역할 정의 {#role-definitions}

>[!NOTE]
>
>관리 콘솔의 개발자 페르소나는 의 개발자 역할과 관련이 [!UICONTROL Cloud Manager]없습니다.

다음 표에는 역할이 요약되어 있습니다.

| [!UICONTROL Cloud Manager] 역할 | 설명 |
|--- |--- |
| 비즈니스 소유자 | KPI 정의, 프로덕션 배포 승인, 중요한 3단계 장애 무시 등의 책임입니다. |
| 프로그램 관리자 | 팀 설정을 [!UICONTROL Cloud Manager] 수행하고 상태를 검토하고 KPI를 보는 데 사용합니다. 중요한 3단계 오류를 승인할 수 있습니다. |
| 배포 관리자 | 배포 작업을 관리합니다. 스테이지/프로덕션 배포를 실행하는 [!UICONTROL Cloud Manager] 데 사용됩니다. CI/CD 파이프라인을 편집할 수 있습니다. 중요한 3단계 오류를 승인할 수 있습니다. Git 리포지토리에 액세스할 수 있습니다. |
| 개발자 | 사용자 정의 애플리케이션 코드를 개발하고 테스트합니다. 주로 상태를 보는 [!UICONTROL Cloud Manager] 데 사용됩니다. 코드 커밋을 위해 Git 리포지토리에 액세스할 수 있습니다. |
| 고객 성공 엔지니어 | 일반적으로 AMS 고객의 성공을 지원합니다. CSE 감독이 필요한 배포 실행을 [!UICONTROL Cloud Manager] 위해 상호 작용합니다. |
| 컨텐츠 작성자 | 일반적으로 상호 작용하지 않습니다 [!UICONTROL Cloud Manager]. 프로그램 [!UICONTROL Cloud Manager] 전환기(이동 중)를 사용하여 AEM에 액세스할 [!UICONTROL Experience Cloud]수 있습니다. |

## 관리 콘솔을 사용하여 프로필 만들기 {#using-admin-console-to-create-a-profile}

역할은 Adobe Admin Console [!UICONTROL Cloud Manager] 에서 관리합니다. 관리 콘솔에서 사용자를 제품 프로필에 추가하여 특정 역할 [!UICONTROL Cloud Manager] 멤버십이 제공됩니다.

사용자를 조직 전체의 Adobe 권한 관리를 위한 중앙 위치인 [!UICONTROL Cloud Manager] Adobe **Admin Console에서 제품 프로필에** 추가하여 특정 역할 멤버십을 할당할 수 있습니다. Adobe Admin Console에 대한 자세한 내용은 Admin Console 설명서를 [참조하십시오](https://helpx.adobe.com/enterprise/using/admin-console.html).

>[!NOTE]
>
>관리 콘솔에 액세스하고 팀(사용자 및 역할)을 설정하려면 브라우저를 열고 https://adminconsole.adobe.com을 [방문하십시오](https://adminconsole.adobe.com/enterprise).

사용자에게 적절한 역할 기반 권한을 제공하려면 고객 조직의 관리자가 제품 [!UICONTROL Cloud Manager] 컨텍스트에서 **새 제품**&#x200B;프로필을 만들어야 [!UICONTROL AEM Managed Services] 합니다.

사용자에게 적절한 역할 기반 권한을 제공하려면 [!UICONTROL Cloud Manager] 관리자로서 다음 네 가지 [!UICONTROL AEM Managed Services] [!UICONTROL Cloud Manager] 역할 각각에 해당하는 제품 컨텍스트 아래에 4개의 새 제품 프로필을 생성해야 합니다.

* 비즈니스 소유자
* 배포 관리자
* 개발자
* 프로그램 관리자

아래 그림과 같이 관리 콘솔을 사용하여 이러한 제품 프로필에 사용자/ [그룹을](https://adminconsole.adobe.com/) 만들거나 추가할 수 [!UICONTROL Cloud Manager]있습니다.

1. 관리 콘솔에 로그인하고 새 **프로필을** 클릭하여 새 프로필을 추가합니다.

   ![](assets/admin_console_roles-1.png)

1. 필드를 채워 새 역할을 [!UICONTROL Cloud Manager]설정합니다.

   프로필 **이름**, 표시 **이름을** 입력하여 새 프로필을 만듭니다. 또한 프로필에 대한 권한 **그룹을** 선택할 수 있습니다.

   완료를 **클릭하여** 프로필 작성 단계를 완료합니다.

   >[!NOTE]
   >
   >이러한 제품 프로필을 만들 때 **표시** 이름은 에서 정의한 기술 [!UICONTROL Cloud Manager] 값이어야 합니다(아래 표 참조). 프로필 **이름은** 어떤 것이든 될 수 있지만, 혼란을 방지하려면 아래의 권장 프로필 이름 *열에서 값을 사용하는 것이* 좋습니다. 이렇게 하려면 제품 프로필을 만들 때 프로필 이름과 **동일** 옵션의 선택을 취소하고 해당 값을 표시 이름으로 **지정합니다**.

   | **역할** | **표시 이름(필수)** | **권장 프로필 이름** |
   |---|---|---|
   | 비즈니스 소유자 | CM_BUSINESS_OWNER_ROLE_PROFILE | [!UICONTROL Cloud Manager] - 사업주 역할 |
   | 배포 관리자 | CM_DEPLOYMENT_MANAGER_ROLE_PROFILE | [!UICONTROL Cloud Manager] - 배포 관리자 역할 |
   | 개발자 | CM_DEVELOPER_ROLE_PROFILE | [!UICONTROL Cloud Manager] - 개발자 역할 |
   | 프로그램 관리자 | CM_PROGRAM_MANAGER_ROLE_PROFILE | [!UICONTROL Cloud Manager] - 프로그램 관리자 역할 |

   ![](assets/screen_shot_2018-05-04at171819.png)

1. 제품 프로필을 만들고 나면 이 제품 프로필에 사용자(또는 그룹)를 추가할 수 있습니다.

   ![](assets/image2018-4-9_15-19-26.png)

   ![](assets/image2018-4-9_15-16-47.png)

