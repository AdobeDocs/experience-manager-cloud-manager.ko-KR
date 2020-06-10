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
source-git-commit: 77b7e2fc81880a7f1878fa9553ce2ae8078d1b78
workflow-type: tm+mt
source-wordcount: '542'
ht-degree: 2%

---


# 고객 여정 {#customer-journey}

고객은 현재 AEM 6.4를 사용하고 있는 AEM(Adobe Experience Manager)을 처음 사용하거나 사용하려면 AEM 6.4 릴리스로 업그레이드해야 할 수 있습니다 [!UICONTROL Cloud Manager]. 다음 시나리오에서는 신규 고객이나 기존 고객으로 고객 여정을 설명합니다 [!UICONTROL Cloud Manager].

>[!NOTE]
>
>[!UICONTROL Cloud Manager] 은 AEM 6.4 이상을 사용하는 Adobe Managed Services 고객에게만 제공됩니다.

## 온보딩 대상 [!UICONTROL Cloud Manager]{#on-boarding-to-cloud-manager}

1. **Adobe Managed Services의 새 AEM 고객**

   신규 고객은 Adobe Managed Cloud 서비스의 온보딩 과정의 [!UICONTROL Cloud Manager] 일부로 온보딩을 받게 됩니다.

   액세스할 URL은 로그인 지침 [!UICONTROL Cloud Manager] 과 함께 시작 이메일에 포함되며, Adobe Admin Console을 사용하여 액세스 [!UICONTROL Experience Cloud]가 필요한 사용자를 위해 사용자와 해당 권한을 관리합니다 [!UICONTROL Cloud Manager].

1. **Adobe Managed Services의 기존 AEM 고객**

   기존 고객은 먼저 기존 프로덕션 및 비프로덕션 환경을 AEM 6.4 릴리스로 업그레이드해야 합니다. 업그레이드를 수행하는 동시에 액세스할 수 있는 URL과 함께 온보드 및 제공됩니다 [!UICONTROL Cloud Manager]. 또한 Adobe Admin Console을 사용하여 액세스 권한이 필요한 사용자와 해당 권한을 관리해야 합니다 [!UICONTROL Cloud Manager].

   또한 AEM 환경에 새 코드 변경 사항을 배포하는 데 사용하기 [!UICONTROL Cloud Manager] 를 시작하기 때문에 기존 AEM 프로젝트에서도 권장 우수 사례를 준수해야 합니다.

   AEM 6.4로 업그레이드하여 얻을 수 있는 이점에 대한 자세한 내용은 AEM [6.4로 업그레이드를 참조하십시오](https://helpx.adobe.com/experience-manager/6-4/sites/deploying/using/upgrade.html).

## 액세스 [!UICONTROL Cloud Manager] {#accessing-cloud-manager}

AEM 환경 [!UICONTROL Cloud Manager] [!UICONTROL Experience Cloud] 에 액세스하려면, 랜딩 페이지에 로그인하고 Adobe ID 관리 자격 증명을 사용하고 솔루션 전환기 인터페이스에서 AEM을 선택하면 됩니다.

처음 로그인 [!UICONTROL Cloud Manager] 을 한 후 UI에서 직접 AEM 환경에 액세스할 수 [!UICONTROL Cloud Manager] 있습니다. 이제 스테이지와 프로덕션 환경에 배포할 첫 번째 코드 분기를 준비하면 모든 가능성을 [!UICONTROL Cloud Manager]살펴볼 수 있습니다.

처음 로그인 [!UICONTROL Cloud Manager]을 [참조하십시오](first-time-login.md). AEM에 대한 자세한 내용은 [AEM 6.4 시작하기를 참조하십시오](https://helpx.adobe.com/kr/experience-manager/6-4/sites/deploying/using/deploy.html). 또한 자세한 내용은 [AEM 리소스를](https://www.adobe.com/marketing-cloud/experience-manager/resources.html?promoid=759X6WV8&amp;mv=other) 참조하십시오.

## Getting Started with [!UICONTROL Cloud Manager] {#getting-started-with-cloud-manager}

로그인하면 먼저 코드 저장소 환경 [!UICONTROL Cloud Manager]을 설정한 다음 팀과 역할을 설정해야 합니다. 특히, 역할 멤버십은 관리 콘솔 UI를 사용하여 사용자를 [!UICONTROL Cloud Manager] 프로필에 추가하여 할당됩니다.

그런 다음 Git 리포지토리에서 소스 코드 분기를 설정하고, 로드 및 성능 KPI에 ****&#x200B;대한 목표를 정의하고, 모든 품질 검사가 성공적으로 완료된 후 코드를 스테이지와 프로덕션 환경에 성공적으로 배포하도록 테스트 시나리오를 테스트해야 합니다.

## 고객 여정 {#end-to-end-journey}

다음 다이어그램은 코드 변경 사항을 스테이지와 프로덕션 환경에 배포하기 위해 [!UICONTROL Cloud Manager] CI/CD 파이프라인을 사용하는 경우 고객 여정을 한 차원 높은 수준으로 보여줍니다.

![](assets/screen_shot_2018-05-15at124004pm.png)

