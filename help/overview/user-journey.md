---
title: 사용자 여정
description: 이 문서는 다른 온보딩 시나리오를 설명하고 Cloud Manager로 시작하는 여정에 대해 설명합니다.
exl-id: deb3429c-dfcf-4e52-9aba-d9368aa240e6
source-git-commit: b0dbb602253939464ff034941ffbad84b7df77df
workflow-type: tm+mt
source-wordcount: '504'
ht-degree: 0%

---


# 사용자 여정 {#user-journey}

Adobe Experience Manager 사용자는

* AEM을 처음 사용합니다.
* 현재 AEM 6.x를 사용 중입니다.
* 를 사용하려면 AEM 6.5 릴리스로 업그레이드해야 함 [!UICONTROL Cloud Manager].

이 문서는 다음 시나리오를 설명하고 여정을 설명합니다 [!UICONTROL Cloud Manager].

>[!NOTE]
>
>[!UICONTROL Cloud Manager] AEM 6.4 이상을 사용하는 AMS(Adobe Managed Services) 고객에게만 제공됩니다.

## 온보딩 {#onboarding}

온보딩 프로세스는 AMS를 처음 사용하는지 또는 기존 AMS 고객인지 여부에 따라 다릅니다.

### Adobe Managed Services의 새로운 기능 {#new-to-ams}

새 고객은 다음 위치에 온보딩됩니다. [!UICONTROL Cloud Manager] adobe Managed Services에 대한 온보딩 프로세스의 일부로 사용됩니다.

온보딩 프로세스의 일부로, 다음을 포함하는 환영 이메일을 받게 됩니다.

* 액세스할 URL [!UICONTROL Cloud Manager]
* 로그인하는 지침 [!UICONTROL Experience Cloud]
* Admin Console이 액세스할 수 있도록 사용자 및 해당 권한을 관리하는 데 사용하는 지침입니다 [!UICONTROL Cloud Manager] 필요한 경우.

### 기존 Adobe Managed Services 고객 {#existing-customer}

기존 AMS 고객은 먼저 기존 프로덕션 및 비프로덕션 환경을 AEM 6.4 이상으로 업그레이드해야 합니다.

업그레이드를 수행할 때 Cloud Manager에 온보딩되고 액세스할 수 있는 URL이 제공됩니다 [!UICONTROL Cloud Manager]. 또한 [!UICONTROL Cloud Manager]를 채울 때는 Admin Console을 사용하여 해당 사용자와 각각의 권한을 관리해야 합니다.

사용을 시작할 때 기존 AEM 프로젝트에서도 권장 우수 사례를 따라야 합니다 [!UICONTROL Cloud Manager] AEM 환경에 새 코드 변경 사항을 배포하기 위한 것입니다.

AEM 6.5로 업그레이드하는 장점에 대한 추가 정보를 보려면 문서를 참조하십시오 [AEM 6.5로 업그레이드](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/upgrading/upgrade.html)

## 액세스 [!UICONTROL Cloud Manager] {#accessing-cloud-manager}

에 액세스할 수 있습니다. [!UICONTROL Cloud Manager] 및에 로그인하면 AEM 환경이 활성화됩니다 [!UICONTROL Experience Cloud] Adobe Identity Management 자격 증명을 사용하고 솔루션 전환기 인터페이스에서 AEM을 선택하여 랜딩 페이지로 이동합니다.

로그인 후 [!UICONTROL Cloud Manager] 처음으로, [!UICONTROL Cloud Manager] UI. 이 시점에서, 여러분은 모든 가능성을 탐색할 준비가 되었습니다 [!UICONTROL Cloud Manager] 첫 번째 코드 분기를 준비하여 스테이지 및 프로덕션 환경에 배포할 수 있습니다.

시작하려면 [!UICONTROL Cloud Manager]를 참조하고 문서를 참조하십시오 [처음 로그인](/help/getting-started/first-time-login.md).

AEM에 대한 자세한 내용은 문서를 참조하십시오 [배포 및 유지 관리.](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/deploying/deploy.html)

## 시작하기 [!UICONTROL Cloud Manager] {#getting-started-with-cloud-manager}

로그인하면 [!UICONTROL Cloud Manager] 다음을 통해 AEM 프로젝트를 시작할 수 있습니다.

1. 코드 저장소 환경 설정.
1. 팀 및 역할을 설정합니다.
   * 역할 멤버십은 사용자를 [!UICONTROL Cloud Manager] Admin Console을 사용한 프로필.
1. Git 리포지토리에서 소스 코드 분기를 설정합니다.
1. 로드 및 성능 KPI와 관련하여 목표 정의
1. 모든 품질 검사가 성공적으로 수행되면 코드를 스테이지 및 프로덕션 환경에 성공적으로 배포하는 테스트 시나리오를 정의합니다.

## 종단 간 여정 {#end-to-end-journey}

이 다이어그램은 를 사용할 때 높은 수준에서 고객 여정을 보여줍니다 [!UICONTROL Cloud Manager] 스테이징 및 프로덕션 환경에 코드 변경 사항을 배포하기 위한 CI/CD 파이프라인입니다.

![종단 간 여정](/help/assets/screen_shot_2018-05-15at124004pm.png)
