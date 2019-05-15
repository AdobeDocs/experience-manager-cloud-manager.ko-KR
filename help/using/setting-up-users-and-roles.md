---
title: 사용자 및 역할 추가
seo-title: 사용자 및 역할 추가
description: 'null'
seo-description: Admin Console에서 Cloud Manager 제품 프로필에 사용자를 추가하여 특정 역할 멤버십을 할당할 수 있습니다. 자세한 내용은 이 섹션을 참조하십시오.
uuid: fa 204 c 28-83 df -48 bb -8360-e 158 f 080 dee 7
contentOwner: Jsyal
products: sg_ Experiencemanager/Cloudmanager
topic-tags: 요구 사항
discoiquuid: 1 b 421993-22 c 3-4 de 0-ba 64-c 1080 d 07 ad 5 e
translation-type: tm+mt
source-git-commit: 1dfb065c09569f811e5a006d3d74825d3bd7cc8d

---


# 사용자 및 역할 추가{#add-users-and-roles}

의 [!UICONTROL Cloud Manager] 많은 기능을 사용하려면 특정 권한이 필요합니다. 예를 들어 특정 사용자만 프로그램에 대한 KPI (Key Performance Indicator) 를 설정할 수 있습니다. 이러한 권한은 논리적으로 역할로 그룹화됩니다.

[!UICONTROL Cloud Manager] 는 현재 특정 기능의 가용성을 제어하는 사용자의 네 가지 역할을 정의합니다.

* 비즈니스 담당자
* 프로그램 관리자
* 배포 관리자
* 개발자

>[!CAUTION]
>
>사용하려면 [!UICONTROL Cloud Manager]Adobe ID와 Adobe Managed Services 제품 컨텍스트가 있어야 합니다.

## 역할 정의 {#role-definitions}

>[!NOTE]
>
>관리 콘솔의 개발자 성향은의 개발자 역할과 관련이 [!UICONTROL Cloud Manager]없습니다.

다음 표에는 역할이 요약되어 있습니다.

| [!UICONTROL Cloud Manager] 역할 | 설명 |
|--- |--- |
| 비즈니스 담당자 | KPI 정의, 프로덕션 배포 승인, 중요한 3 계층 오류 무시를 책임지고 있습니다. |
| 프로그램 관리자 | 팀 설정 수행, 상태 검토 및 KPI 보기를 [!UICONTROL Cloud Manager] 수행하는 데 사용합니다. 중요한 3 계층 오류를 승인할 수 있습니다. |
| 배포 관리자 | 배포 작업을 관리합니다. 단계/프로덕션 배포를 실행하는 [!UICONTROL Cloud Manager] 데 사용합니다. CI/CD 파이프라인을 편집할 수 있습니다. 중요한 3 계층 오류를 승인할 수 있습니다. Git 리포지토리에 액세스할 수 있습니다. 요청하려면 CSE/AMS 담당자에게 문의하십시오. |
| 개발자 | 사용자 지정 애플리케이션 코드를 개발하고 테스트합니다. 상태를 확인하는 데 주로 사용됩니다 [!UICONTROL Cloud Manager] . 코드 실행을 위해 Git 리포지토리에 액세스해야 합니다. Git 리포지토리에 대한 액세스 권한을 부여하려면 이 역할로 사용자를 추가할 때 CSE/AMS 담당자에게 문의하십시오. |
| Customer Success Engineer | 일반적으로 AMS 고객을 위한 고객 성공을 지원합니다. CSE 관리자가 [!UICONTROL Cloud Manager] 필요한 배포를 실행하기 위한 목적으로 상호 작용합니다. |
| 컨텐츠 작성자 | 는 일반적으로 상호 작용하지 [!UICONTROL Cloud Manager]않습니다. 프로그램 전환기 (탐색) 를 사용하여 [!UICONTROL Cloud Manager] AEM에 액세스할 [!UICONTROL Experience Cloud]수 있습니다. |

>[!NOTE]
>
>[!UICONTROL Cloud Manager] Git 리포지토리는 CSE에서 관리합니다. 사용자를 추가 및 제거하려면 해당 담당자에게 문의하십시오.
>
>새로 추가된 사용자에게 Git 리포지토리에 대한 액세스 권한이 필요한 경우 CSE/AMS 담당자에게 문의하여 액세스 권한을 부여해야 합니다. 이러한 역할은 Git 리포지토리에 대한 자동 액세스를 제공하지 않습니다. Git 리포지토리 액세스 권한이 있는 최대 3 명의 사용자만 가질 수 있습니다.

## Admin Console를 사용하여 프로필 만들기 {#using-admin-console-to-create-a-profile}

역할은 Adobe Admin [!UICONTROL Cloud Manager] Console에서 관리됩니다. 관리 콘솔에서 [!UICONTROL Cloud Manager] 제품 프로필에 사용자를 추가하면 특정 역할 멤버십이 제공됩니다.

조직 전체에서 Adobe 이용 권한을 중앙에서 관리할 수 있는 Adobe Admin Console의 [!UICONTROL Cloud Manager]**제품 프로필에** 사용자를 추가하여 특정 역할 멤버십을 할당할 수 있습니다. Adobe Admin Console에 대한 자세한 내용은 [관리 콘솔 설명서를](https://helpx.adobe.com/enterprise/using/admin-console.html)참조하십시오.

>[!NOTE]
>
>Admin Console를 강조하고 팀을 설정하려면 (사용자 및 역할) 브라우저를 열고 [https://adminconsole.adobe.com를 방문하십시오](https://adminconsole.adobe.com/enterprise).

사용자 조직의 관리자가 적절한 역할 기반 [!UICONTROL Cloud Manager] 권한을 제공하려면 ****[!UICONTROL AEM Managed Services] 제품 컨텍스트에서 새 제품 프로필을 만들어야 합니다.

[!UICONTROL Cloud Manager] 사용자에게 적절한 역할 기반 권한을 제공하려면, 관리자가 네 [!UICONTROL AEM Managed Services][!UICONTROL Cloud Manager] 가지 역할 각각에 해당하는 제품 컨텍스트에서 4 개의 새 제품 프로필을 만들어야 합니다.

* 비즈니스 담당자
* 배포 관리자
* 개발자
* 프로그램 관리자

아래 그림에서와 같이 [, Admin Console](https://adminconsole.adobe.com/) 를 사용하여 이러한 제품 프로필에 사용자/그룹을 [!UICONTROL Cloud Manager]만들거나 추가할 수 있습니다.

1. Admin Console에 로그인하고 **새 프로필을** 클릭하여 새 프로필을 추가합니다.

   ![](assets/admin_console_roles-1.png)

1. 필드를 채워 새 역할을 [!UICONTROL Cloud Manager]설정합니다.

   **프로필 이름**, **표시 이름을** 입력하여 새 프로필을 만듭니다. 또한 프로필에 **대한 권한 그룹을** 선택할 수 있습니다.

   **완료를** 클릭하여 프로필 작성 단계를 완료합니다.

   >[!NOTE]
   >
   >이러한 제품 프로필을 만들 때 **표시 이름은** 에서 [!UICONTROL Cloud Manager] 정의한 기술 값이어야 합니다 (아래 표 참조). **프로필 이름은** 아무 것도 될 수 있지만 혼동을 방지하기 위해 아래의 *권장 프로필 이름* 열에 값을 사용하는 것이 좋습니다. 이렇게 하려면 제품 프로필을 만들 때 프로필 이름과 **동일한** 이름을 선택 취소하고 해당 값을 **표시 이름으로 지정합니다**.

   | **역할** | **표시 이름 (필수)** | **권장 프로필 이름** |
   |---|---|---|
   | 비즈니스 담당자 | cm_ business_ owner_ role_ profile | [!UICONTROL Cloud Manager] - 비즈니스 소유자 역할 |
   | 배포 관리자 | CM_ DEPLOYMENT_ MANAGER_ ROLE_ PROFILE | [!UICONTROL Cloud Manager] - 배포 관리자 역할 |
   | 개발자 | cm_ developer_ role_ profile | [!UICONTROL Cloud Manager] - 개발자 역할 |
   | 프로그램 관리자 | cm_ program_ manager_ role_ profile | [!UICONTROL Cloud Manager] - 프로그램 관리자 역할 |

   ![](assets/screen_shot_2018-05-04at171819.png)

1. 제품 프로필을 만들었으면 이러한 제품 프로필에 사용자 (또는 그룹) 를 추가할 수 있습니다.

   ![](assets/image2018-4-9_15-19-26.png)

   ![](assets/image2018-4-9_15-16-47.png)

