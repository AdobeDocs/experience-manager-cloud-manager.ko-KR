---
title: 고객 여정
seo-title: Adobe AEM Cloud Manager 고객 여정
description: Cloud Manager를 시작하기 위한 고객으로서 여정에 대해 알려면 이 페이지를 따르십시오.
seo-description: AEM Cloud Manager를 시작하려면 고객으로서 여정에 대해 알려면 이 페이지를 따르십시오.
uuid: d4468eb6-5bde-48dd-b96e-0cc61e046f96
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: introduction
discoiquuid: bc9a0d63-ae6b-4fe9-81e5-bf9844f04e54
feature: 시작하기
level: Beginner
exl-id: deb3429c-dfcf-4e52-9aba-d9368aa240e6
source-git-commit: 43bb3c477ef9c1ce178509b8180479d7616edc66
workflow-type: tm+mt
source-wordcount: '543'
ht-degree: 2%

---

# 고객 여정 {#customer-journey}

고객은 현재 AEM 6.4를 사용하고 있는 AEM(Adobe Experience Manager)을 처음 사용하거나 [!UICONTROL Cloud Manager] 을 사용하기 위해 AEM 6.4 릴리스로 업그레이드해야 할 수도 있습니다. 다음 시나리오에서는 여정을 [!UICONTROL Cloud Manager] 사용을 시작할 신규 또는 기존 고객으로 설명합니다.

>[!NOTE]
>
>[!UICONTROL Cloud Manager] AEM 6.4 이상을 사용하는 Adobe Managed Services 고객에게만 제공됩니다.

## [!UICONTROL Cloud Manager]{#on-boarding-to-cloud-manager}에 온보딩

1. **Adobe Managed Services에 대한 새로운 AEM 고객**

   새 고객은 Adobe Managed Services에 대한 온보딩 프로세스의 일부로 [!UICONTROL Cloud Manager]에 온보딩됩니다.

   [!UICONTROL Cloud Manager]에 액세스하는 URL은 [!UICONTROL Experience Cloud]에 로그인하는 지침과 함께 시작 전자 메일에 포함되며, [!UICONTROL Cloud Manager]에 액세스해야 하는 사용자를 위해 Adobe Admin Console을 사용하여 사용자 및 해당 권한을 관리합니다.

1. **Adobe Managed Services의 기존 AEM 고객**

   기존 고객은 먼저 기존 프로덕션 및 비프로덕션 환경을 AEM 6.4 릴리스로 업그레이드해야 합니다. 업그레이드를 수행하는 동시에, 온보드 URL이 제공되어 [!UICONTROL Cloud Manager]에 액세스할 수 있습니다. 또한 [!UICONTROL Cloud Manager]에 액세스해야 하는 사용자를 위해 Adobe Admin Console을 사용하여 사용자와 각각의 권한을 관리해야 합니다.

   AEM 환경에 새 코드 변경 사항을 배포하기 위해 [!UICONTROL Cloud Manager] 사용을 시작하기 때문에 기존 AEM 프로젝트가 권장 우수 사례를 따라야 합니다.

   AEM 6.4로 업그레이드하는 장점에 대한 추가 정보를 보려면 [AEM 6.4로 업그레이드](https://helpx.adobe.com/experience-manager/6-4/sites/deploying/using/upgrade.html)를 참조하십시오.

## [!UICONTROL Cloud Manager] {#accessing-cloud-manager}에 액세스

[!UICONTROL Cloud Manager] 랜딩 페이지에 로그인하고 Adobe Identity Management 자격 증명을 사용하고 솔루션 전환기 인터페이스에서 AEM을 선택하면 해당 환경에 액세스할 수 있습니다.[!UICONTROL Experience Cloud]

처음 [!UICONTROL Cloud Manager]에 로그인한 후 [!UICONTROL Cloud Manager] UI에서 직접 AEM 환경에 액세스할 수 있습니다. 이 시점에서 스테이지 및 프로덕션 환경에 배포할 첫 번째 코드 분기가 준비되면 [!UICONTROL Cloud Manager]의 모든 가능성을 탐색할 수 있습니다.

[!UICONTROL Cloud Manager]을(를) 탐색하고 시작하려면 [처음 로그인](first-time-login.md)을 참조하십시오. AEM에 대한 자세한 내용은 [AEM 6.4 시작하기](https://helpx.adobe.com/experience-manager/6-4/sites/deploying/using/deploy.html)를 참조하십시오. 추가 정보는 [AEM 리소스](https://www.adobe.com/marketing-cloud/experience-manager/resources.html?promoid=759X6WV8&amp;mv=other)를 참조하십시오.

## [!UICONTROL Cloud Manager] {#getting-started-with-cloud-manager} 시작하기

[!UICONTROL Cloud Manager]에 로그인하면 맨 먼저 코드 저장소 환경을 설정한 다음 팀과 역할을 설정해야 합니다. 특히, 역할 멤버십은 Admin Console UI를 사용하여 [!UICONTROL Cloud Manager] 프로필에 사용자를 추가하여 할당됩니다.

그런 다음 **Git 리포지토리**&#x200B;에서 소스 코드 분기를 설정하고, 로드 및 성능 KPI에 대한 목표를 정의하고, 모든 품질 검사가 성공적으로 수행되면 코드를 스테이지 및 프로덕션 환경에 성공적으로 배포하도록 테스트 시나리오를 정의해야 합니다.

## 종료 여정 {#end-to-end-journey}

다음 다이어그램은 스테이지 및 프로덕션 환경에 코드 변경 사항을 배포하기 위해 [!UICONTROL Cloud Manager] CI/CD 파이프라인을 사용할 때 높은 수준에서 고객 여정을 보여줍니다.

![](assets/screen_shot_2018-05-15at124004pm.png)
