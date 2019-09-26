---
title: 고객 여정
seo-title: Adobe AEM Cloud Manager 고객 여정
description: Cloud Manager를 시작하기 위한 고객으로서의 여정에 대해 알려면 이 페이지를 따르십시오.
seo-description: 이 페이지에서 Adobe AEM Cloud Manager를 시작하기 위한 고객으로서의 여정에 대해 살펴보십시오.
uuid: d4468eb6-5bde-48dd-b96e-0cc61e046f96
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: 소개
discoiquuid: bc9a0d63-ae6b-4fe9-81e5-bf9844f04e54
translation-type: tm+mt
source-git-commit: 15f75ca67c3d52ae511357c5b564daaa3d9def6b

---


# 고객 여정 {#customer-journey}

고객인 경우 현재 AEM 6.4를 사용하고 있는 Adobe Experience Manager(AEM)를 처음 사용하거나 사용하려면 AEM 6.4 릴리스로 업그레이드해야 할 수도 [!UICONTROL Cloud Manager]있습니다. 다음 시나리오에서는 신규 고객이나 기존 고객으로 시작한 여행에 대해 설명합니다 [!UICONTROL Cloud Manager].

>[!NOTE]
>
>[!UICONTROL Cloud Manager] 는 AEM 6.4 이상을 사용하는 Adobe Managed Services 고객에게만 제공됩니다.

## 온보딩 대상 [!UICONTROL Cloud Manager]{#on-boarding-to-cloud-manager}

1. **Adobe Managed Services의 새 AEM 고객**

   신규 고객은 Adobe Managed Cloud 서비스에 대한 온보딩 프로세스의 [!UICONTROL Cloud Manager] 일부로 온라인을 통해 이용할 수 있습니다.

   액세스할 URL은 로그인 지침과 함께 환영 이메일에 [!UICONTROL Cloud Manager] 포함되어 [!UICONTROL Experience Cloud]있으며, Adobe Admin Console을 사용하여 액세스 권한이 필요한 사용자를 관리할 수 있습니다 [!UICONTROL Cloud Manager].

1. **Adobe Managed Services의 기존 AEM 고객**

   기존 고객은 먼저 기존 프로덕션 및 비프로덕션 환경을 AEM 6.4 릴리스로 업그레이드해야 합니다. 동시에 업그레이드를 수행하면 액세스할 수 있는 URL이 제공되므로 온보드 방식으로 제공됩니다 [!UICONTROL Cloud Manager]. 또한 액세스 권한이 필요한 사용자를 위해 Adobe Admin Console을 사용하여 사용자와 해당 권한을 관리해야 [!UICONTROL Cloud Manager]합니다.

   또한 AEM 환경에 새 코드 변경 사항을 배포하는 [!UICONTROL Cloud Manager] 데 사용할 것이므로 기존 AEM 프로젝트가 권장되는 우수 사례를 준수해야 합니다.

   AEM 6.4로 업그레이드하여 얻을 수 있는 이점에 대한 자세한 내용은 AEM [6.4로 업그레이드를 참조하십시오](https://helpx.adobe.com/experience-manager/6-4/sites/deploying/using/upgrade.html).

## 액세스 [!UICONTROL Cloud Manager] 중 {#accessing-cloud-manager}

랜딩 페이지에 로그인하고 Adobe ID [!UICONTROL Cloud Manager] [!UICONTROL Experience Cloud] 관리 자격 증명을 사용하여 AEM 환경을 액세스하고, 솔루션 전환기 인터페이스에서 AEM을 선택하면 AEM 환경에 액세스할 수 있습니다.

처음 로그인한 [!UICONTROL Cloud Manager] 후 UI에서 직접 AEM 환경에 액세스할 수 [!UICONTROL Cloud Manager] 있습니다. 이제 스테이지와 프로덕션 환경에 배포할 첫 번째 코드 분기를 준비하면 모든 가능성을 [!UICONTROL Cloud Manager]살펴볼 수 있습니다.

처음 로그인을 [!UICONTROL Cloud Manager]참조하십시오 [](first-time-login.md). AEM에 대한 자세한 내용은 AEM [6.4 시작을 참조하십시오](https://helpx.adobe.com/experience-manager/6-4/sites/deploying/using/deploy.html). 또한 자세한 내용은 AEM [리소스를](https://www.adobe.com/marketing-cloud/experience-manager/resources.html?promoid=759X6WV8&mv=other) 참조하십시오.

## Getting Started with [!UICONTROL Cloud Manager] {#getting-started-with-cloud-manager}

로그인하면 [!UICONTROL Cloud Manager]먼저 코드 저장소 환경을 설정한 다음 팀과 역할을 설정해야 합니다. 특히, 역할 멤버십은 관리 콘솔 UI를 사용하여 사용자를 [!UICONTROL Cloud Manager] 프로필에 추가하여 할당됩니다.

그런 다음 Git 리포지토리에 소스 코드 분기를 설정하고, 로드 **및 성능** KPI에 대한 목표를 정의하고, 모든 품질 검사가 성공적으로 수행되면 코드를 스테이지와 프로덕션 환경에 성공적으로 배포하기 위한 테스트 시나리오를 설정해야 합니다.

## 고객 여정 {#end-to-end-journey}

다음 다이어그램은 CI/CD [!UICONTROL Cloud Manager] 파이프라인을 사용하여 스테이지와 프로덕션 환경에 코드 변경 사항을 배포할 때 고객 경로를 한 차원 높은 수준으로 보여줍니다.

![](assets/screen_shot_2018-05-15at124004pm.png)

