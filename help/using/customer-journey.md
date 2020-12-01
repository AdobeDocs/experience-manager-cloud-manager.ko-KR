---
title: 고객 여정
seo-title: Adobe AEM Cloud Manager 고객 여정
description: Cloud Manager를 시작하기 위한 고객으로서의 여정에 대해 알려면 이 페이지를 따르십시오.
seo-description: Adobe AEM Cloud Manager를 시작하기 위한 고객으로서의 여정에 대해 알려면 이 페이지를 따르십시오.
uuid: d4468eb6-5bde-48dd-b96e-0cc61e046f96
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: introduction
discoiquuid: bc9a0d63-ae6b-4fe9-81e5-bf9844f04e54
translation-type: tm+mt
source-git-commit: ace032fbb26235d87d61552a11996ec2bb42abce
workflow-type: tm+mt
source-wordcount: '541'
ht-degree: 2%

---


# 고객 여정 {#customer-journey}

고객인 경우 현재 AEM 6.4를 사용하고 있는 Adobe Experience Manager(AEM)을 처음 사용하거나 [!UICONTROL Cloud Manager]을(를) 사용하려면 AEM 6.4 릴리스로 업그레이드해야 할 수 있습니다. 다음 시나리오에서는 [!UICONTROL Cloud Manager]으로 시작하기 위한 신규 또는 기존 고객으로서 여정을 설명합니다.

>[!NOTE]
>
>[!UICONTROL Cloud Manager] 은 AEM 6.4 이상을 사용하는 Adobe Managed Services 고객에게만 제공됩니다.

## [!UICONTROL Cloud Manager]{#on-boarding-to-cloud-manager} 온보딩

1. **Adobe Managed Services의 신규 AEM 고객**

   신규 고객은 Adobe Managed Services의 온보딩 과정의 일부로 [!UICONTROL Cloud Manager]에 온보드 환경을 사용할 수 있습니다.

   [!UICONTROL Cloud Manager]에 액세스하기 위한 URL은 [!UICONTROL Experience Cloud]에 로그인하기 위한 지침과 함께 시작 이메일에 포함되며, [!UICONTROL Cloud Manager]에 액세스해야 하는 사용자에 대해 사용자 및 해당 권한을 관리하는 데 Adobe Admin Console을 사용합니다.

1. **Adobe Managed Services의 기존 AEM 고객**

   기존 고객은 먼저 기존 프로덕션 및 비프로덕션 환경을 AEM 6.4 릴리스로 업그레이드해야 합니다. 업그레이드를 수행하는 동시에 [!UICONTROL Cloud Manager]에 액세스할 수 있는 URL이 포함된 온보드 방식으로 제공됩니다. 또한, [!UICONTROL Cloud Manager]에 액세스해야 하는 사용자에 대해 사용자 및 해당 권한을 관리하기 위해 Adobe Admin Console을 사용해야 합니다.

   AEM 환경에 새 코드 변경 사항을 배포하는 데 [!UICONTROL Cloud Manager]을(를) 사용하기 시작하면 기존 AEM 프로젝트도 권장 우수 사례를 따라야 합니다.

   AEM 6.4로 업그레이드하는 데 따른 이점에 대한 자세한 내용은 [AEM 6.4로 업그레이드](https://helpx.adobe.com/experience-manager/6-4/sites/deploying/using/upgrade.html)를 참조하십시오.

## [!UICONTROL Cloud Manager] {#accessing-cloud-manager} 액세스

[!UICONTROL Cloud Manager] 랜딩 페이지에 로그인하여 Adobe Identity Management 자격 증명을 사용하고 솔루션 전환기 인터페이스에서 AEM을 선택하면 AEM 환경에 액세스할 수 있습니다.[!UICONTROL Experience Cloud]

처음으로 [!UICONTROL Cloud Manager]에 로그인한 후에는 [!UICONTROL Cloud Manager] UI에서 직접 AEM 환경에 액세스할 수 있습니다. 이때 스테이지와 프로덕션 환경에 배포할 첫 번째 코드 분기가 준비되면 [!UICONTROL Cloud Manager]의 모든 가능성을 살펴볼 수 있습니다.

[!UICONTROL Cloud Manager]을(를) 살펴보고 시작하려면 [첫 번째 로그인](first-time-login.md)을 참조하십시오. AEM에 대한 자세한 내용은 [AEM 6.4 시작하기](https://helpx.adobe.com/kr/experience-manager/6-4/sites/deploying/using/deploy.html)를 참조하십시오. 또한 자세한 내용은 [AEM 리소스](https://www.adobe.com/marketing-cloud/experience-manager/resources.html?promoid=759X6WV8&amp;mv=other)를 참조하십시오.

## [!UICONTROL Cloud Manager] {#getting-started-with-cloud-manager} 시작하기

[!UICONTROL Cloud Manager]에 로그인한 후에는 먼저 코드 저장소 환경을 설정한 다음 팀과 역할을 설정해야 합니다. 특히 Admin Console UI를 사용하여 사용자를 [!UICONTROL Cloud Manager] 프로필에 추가하여 역할 멤버십이 할당됩니다.

다음으로, 소스 코드 분기를 **Git 리포지토리**&#x200B;에 설정하고, 로드 및 성능 KPI에 대한 목표를 정의하며, 모든 품질 검사가 성공적으로 통과되면 코드를 스테이지와 프로덕션 환경에 성공적으로 배포하기 위해 테스트 시나리오를 설정해야 합니다.

## 종료 경로 {#end-to-end-journey}

다음 다이어그램은 코드 변경 사항을 스테이지와 프로덕션 환경에 배포하기 위해 [!UICONTROL Cloud Manager] CI/CD 파이프라인을 사용하는 경우 고객 여정을 높은 수준에서 보여 줍니다.

![](assets/screen_shot_2018-05-15at124004pm.png)

