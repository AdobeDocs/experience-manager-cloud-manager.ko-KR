---
title: AMS용 Cloud Manager 소개
description: 먼저 Adobe Managed Services(AMS)용 Cloud Manager와 조직에서 Adobe Experience Manager을 자체 관리할 수 있는 방법을 확인하십시오.
exl-id: 58344d8a-b869-4177-a9cf-6a8b7dfe9588
source-git-commit: b0dbb602253939464ff034941ffbad84b7df77df
workflow-type: tm+mt
source-wordcount: '854'
ht-degree: 14%

---


# 소개 [!UICONTROL Cloud Manager] AMS용 {#introduction-to-cloud-manager}

먼저 AMS(Adobe 관리 서비스)를 위한 Cloud Manager와 조직에서 Adobe Experience Manager을 클라우드에서 자체 관리할 수 있는 방법을 확인하십시오.

>[!CONTEXTUALHELP]
>id="aemcloud_cloudmanager_introduction"
>title="AMS용 Cloud Manager 소개"
>abstract="조직에서 클라우드에서 Adobe Experience Manager을 자체 관리할 수 있습니다. 여기에는 IT팀 및 구현 파트너가 성능 또는 보안을 손상하지 않고 맞춤화 또는 업데이트를 신속하게 전달할 수 있는 CI/CD(지속적 통합 및 지속적 배포) 프레임워크가 포함되어 있습니다."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/cloud-manager/programs.html?lang=en#cloud-manager" text="프로그램 만들기"
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/cloud-manager/environments.html?lang=en#cloud-manager" text="환경 만들기"

## 소개 {#introduction}

[!UICONTROL Cloud Manager] Adobe Experience Manager용 는 Adobe Experience Manager 우수 사례를 기반으로 구축된 간소화된 워크플로우를 통해 개발자에게 효과적인 고객 경험을 만들 수 있는 기능을 제공합니다. Adobe Experience Manager에 맞게 최적화된 CI/CD 파이프라인을 사용하면 코드를 체크 인하면 프로덕션 준비가 된 상태로 이동할 수 있으므로 개발 워크플로우를 쉽게 병합할 수 있습니다. 빌드 단계 동안 사용자 지정 코드 업데이트는 모범 사례에 따라 철저하게 테스트되어 고객을 위한 안정적인 애플리케이션을 제공합니다. Cloud Manager는 개방형 API 접근 방식을 사용하여 기존 프로세스 및 도구를 중단하지 않고 시스템과 통합할 수 있습니다.

>[!NOTE]
>
>이 설명서는 AMS(Adobe Managed Services)용 Cloud Manager의 기능과 특징을 구체적으로 설명합니다.
>
>AEM as a Cloud Service에 대한 동등한 설명서는 [AEM as a Cloud Service 설명서입니다.](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/home.html)

Cloud Manager를 사용하면 개발 팀이 다음과 같은 기능을 활용할 수 있습니다.

* 출시 시기를 월/주 단위에서 일/시간 단위로 단축하는 코드 지속적 통합/지속적 배포(CI/CD)

* 프로덕션에 투입하기 전에 프로덕션 중단을 최소화하기 위한 우수 사례 기반 코드 검사, 성능 테스트 및 보안 유효성 검사

* 기존 DevOps 프로세스를 보완하기 위한 API 연결

* 용량 증가 필요성을 지능적으로 탐지하고 추가 디스패처/게시 세그먼트를 자동으로 온라인 상태로 전환하는 자동 크기 조정

이 이미지는에서 사용되는 CI/CD 프로세스 플로우를 보여줍니다. [!UICONTROL Cloud Manager]:

![CI/CD 흐름](/help/assets/screen_shot_2018-05-12at73843pm.png)

## [!UICONTROL Cloud Manager]의 주요 기능  {#key-features-in-cloud-manager}

다음은 Cloud Manager에서 선택한 주요 기능을 자세히 살펴보는 것입니다.

### 셀프서비스 인터페이스 {#self-service-interface}

용 사용자 인터페이스(UI) [!UICONTROL Cloud Manager] Adobe Experience Manager 애플리케이션의 클라우드 환경과 CI/CD 파이프라인을 쉽게 액세스하고 관리할 수 있습니다.

성공적인 배포를 측정하는 기준을 형성하는 애플리케이션별 KPI(주요 성능 지표)를 정의합니다(예: 분당 최대 페이지 보기 횟수 및 페이지 로드 예상 응답 시간). 여러 팀 구성원의 역할과 권한을 쉽게 정의할 수 있습니다. 셀프서비스 인터페이스를 통해 고객이 직접 제어하게 되지만, 우수 사례 리소스에 대한 링크와 필요한 지침을 제공할 수 있는 Adobe 내 전문가 액세스도 제공됩니다.

탐색 및 시작하기 [!UICONTROL Cloud Manager]의 UI에서 문서를 참조하십시오 [처음 로그인.](/help/getting-started/first-time-login.md)

### CI/CD 파이프라인 {#ci-cd-pipeline}

[!UICONTROL Cloud Manager]의 주요 기능 중 하나는 최적화된 CI/CD 파이프라인을 이용하여 사용자 지정 코드 또는 업데이트(예: 웹사이트에 새 구성 요소 추가)의 게재 속도를 단축하는 기능입니다.

사용 [!UICONTROL Cloud Manager] UI, CI/CD 파이프라인을 구성하고 시작할 수 있습니다. 이 파이프라인의 일부로 고품질 애플리케이션만 프로덕션 환경에 전달되도록 철저한 코드 검사가 실행됩니다.

파이프라인 구성에 대한 자세한 내용은 [!UICONTROL Cloud Manager]의 UI에서 문서를 참조하십시오 [프로덕션 파이프라인 구성](/help/using/production-pipelines.md) 및 [비프로덕션 파이프라인 구성.](/help/using/non-production-pipelines.md)

### 유연한 배포 모드 {#flexible-deployment-modes}

[!UICONTROL Cloud Manager] 에서는 변화하는 비즈니스 수요에 따라 경험을 게재할 수 있도록 유연하고 구성 가능한 배포 모드를 제공합니다.

자동 트리거 모드에서는 코드 커밋과 같은 특정 이벤트에 따라 코드가 환경에 자동으로 배포됩니다. 또한, 영업시간 외에도 기간을 지정하여 코드 배포를 예약할 수 있습니다.

배포 트리거와 관계없이, 배포가 트리거될 때마다 품질 검사가 CI/CD 파이프라인 실행의 일부로 항상 수행됩니다. 품질 검사에는 사용자 또는 파트너의 노력 없이 즉시 제공되는 코드 검사, 보안 테스트 및 성능 테스트가 포함되어 있습니다.

코드 배포 및 품질 검사에 대한 자세한 내용은 문서를 참조하십시오 [코드 배포.](/help/using/code-deployment.md)

### 자동 크기 조정 {#autoscaling}

프로덕션 환경에서 로드가 비정상적으로 많을 경우 [!UICONTROL Cloud Manager] 에서는 추가 용량의 필요성을 탐지하여 자동 크기 조정 기능을 사용하여 자동으로 추가 용량을 온라인 상태로 전환합니다.

이런 경우에는 [!UICONTROL Cloud Manager] 자동 크기 조정 제공 프로세스를 트리거하고, 자동 크기 조정 이벤트 알림을 보내고, 몇 분 안에 추가 용량을 온라인 상태로 전환합니다. 추가 용량은 영역이 같고 실행 중인 디스패처/게시 노드와 시스템 사양이 일치하는 프로덕션 환경에서 제공됩니다.

자동 크기 조정 기능은 디스패처/게시 계층에만 적용되며, 가로 크기 조정 방법을 사용하여 실행되며, 최대 10개의 세그먼트까지 디스패처/게시 페어의 추가 세그먼트가 최소 1개 더 있습니다. 제공된 추가 용량은 CSE(Customer Success Engineer)가 결정하는 10일 이내 기간에 수동으로 조정됩니다.

>[!NOTE]
>
>자동 크기 조절이 애플리케이션에 적합한지 여부에 관심이 있는 고객은 CSE 또는 Adobe 담당자에게 문의해야 합니다.
