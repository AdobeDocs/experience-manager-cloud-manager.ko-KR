---
title: 사용자 여정
description: 다양한 온보딩 시나리오와 Cloud Manager를 시작하는 방법에 대해 알아보십시오.
exl-id: deb3429c-dfcf-4e52-9aba-d9368aa240e6
source-git-commit: 984269e5fe70913644d26e759fa21ccea0536bf4
workflow-type: tm+mt
source-wordcount: '532'
ht-degree: 95%

---


# 사용자 여정 {#user-journey}

AEM(Adobe Experience Manager) 사용자라면 다음 시나리오 중 하나에 해당할 수 있습니다.

* AEM 처음 사용자입니다.
* 현재 AEM 6.x를 사용 중입니다.
* [!UICONTROL Cloud Manager]를 사용하려면 AEM 6.5로 업그레이드해야 합니다.

이 문서에서는 세 개의 시나리오를 설명하고 [!UICONTROL Cloud Manager]를 시작하기 위한 여정에 대해 설명합니다.

>[!NOTE]
>
>[!UICONTROL Cloud Manager]는 AEM 6.4 이상을 사용하는 Adobe Managed Services(AMS) 고객만 사용할 수 있습니다.

## 온보딩 {#onboarding}

온보딩 프로세스는 AMS를 처음 사용하는 고객인지 기존 AMS 고객인지에 따라 다릅니다.

### Adobe Managed Services 처음 사용 {#new-to-ams}

새로운 고객은 Adobe Managed Services에 대한 온보딩 프로세스의 일환으로 [!UICONTROL Cloud Manager]에 온보딩됩니다.

온보딩 프로세스의 일환으로 다음과 같은 내용이 포함된 환영 이메일을 받게 됩니다.

* [!UICONTROL Cloud Manager]에 액세스할 URL.
* [!UICONTROL Experience Cloud] 로그인 지침.
* 필요한 경우 [!UICONTROL Cloud Manager]에 액세스할 수 있도록 사용자와 해당 권한을 관리하기 위해 Admin Console을 사용하는 방법.

### 현재 Adobe Managed Services 고객 {#existing-customer}

기존 AMS 고객인 경우 먼저 기존 프로덕션 및 비프로덕션 환경을 AEM 6.4 이상으로 업그레이드해야 합니다.

업그레이드 중 Cloud Manager에 온보딩되고 [!UICONTROL Cloud Manager]에 액세스할 수 있는 URL이 제공됩니다. 또한 [!UICONTROL Cloud Manager]에 액세스해야 하는 사용자는 Admin Console을 사용하여 사용자와 해당 권한을 관리해야 합니다.

AEM 환경에 새 코드 변경 사항을 배포하기 위해 [!UICONTROL Cloud Manager]를 사용하기 시작하므로 기존 AEM 프로젝트도 권장 모범 사례를 준수해야 합니다.

AEM 6.5로 업그레이드할 경우의 이점에 대한 자세한 내용은 [AEM 6.5로 업그레이드](https://experienceleague.adobe.com/ko/docs/ experience-manager-65/content/implementing/deploying/upgrading/upgrade)를 참조하십시오.

## [!UICONTROL Cloud Manager] 액세스 {#accessing-cloud-manager}

Adobe Identity Management 자격 증명을 사용하여 [!UICONTROL Experience Cloud] 랜딩 페이지에 로그인합니다. 여기서 접속할 수 있는 솔루션 전환기에서 AEM을 선택하여 [!UICONTROL Cloud Manager] 및 AEM 환경에 액세스합니다.

[!UICONTROL Cloud Manager]에 처음 로그인하면 [!UICONTROL Cloud Manager] UI에서 직접 AEM 환경에 액세스할 수 있습니다. 이 시점에 [!UICONTROL Cloud Manager]의 모든 가능성을 알아보고 스테이징 및 프로덕션 환경에 배포할 첫 번째 코드 분기가 준비됩니다.

[!UICONTROL Cloud Manager]를 시작하려면 [최초 로그인](/help/getting-started/first-time-login.md)을 참조하십시오.

AEM에 대한 자세한 내용은 [배포 및 유지 관리](https://experienceleague.adobe.com/ko/docs/experience-manager-65/content/implementing/deploying/deploying/deploy)를 참조하십시오.

## [!UICONTROL Cloud Manager] 시작 {#getting-started-with-cloud-manager}

[!UICONTROL Cloud Manager]에 로그인한 후 다음 작업을 수행하여 AEM 프로젝트를 시작할 수 있습니다.

1. 코드 저장소 환경 설정.
1. 내 팀과 역할 설정. 역할 멤버십은 Admin Console을 사용하여 [!UICONTROL Cloud Manager] 프로필에 사용자를 추가하여 할당됩니다.
1. Git 저장소에서 소스 코드 분기 설정.
1. 부하 및 성능 KPI(주요 성과 지표)를 기준으로 목표를 정의합니다.
1. 모든 품질 검사를 성공적으로 통과한 후 코드를 스테이징 및 프로덕션 환경에 성공적으로 배포하기 위한 테스트 시나리오 정의.

## 전체 여정 {#end-to-end-journey}

이 다이어그램은 [!UICONTROL Cloud Manager] CI/CD 파이프라인을 사용하여 코드 변경을 스테이징 및 프로덕션 환경에 배포하는 경우의 고객 여정을 개략적으로 보여 줍니다.

![전체 여정](/help/assets/screen_shot_2018-05-15at124004pm.png)
