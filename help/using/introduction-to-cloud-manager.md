---
title: Cloud Manager 소개
seo-title: Cloud Manager 소개
description: '이 페이지는 클라우드 관리자에 대한 학습을 위한 시작점으로 사용됩니다. '
seo-description: '이 페이지는 Adobe AEM 클라우드 관리자에 대한 학습을 위한 시작점으로 사용되고 이점과 주요 기능을 강조합니다. '
uuid: 62 d 68 E 79-C 2 BA -4 D 8 B-BA 7 D -33709014 D 5 B 6
contentOwner: Jsyal
products: sg_ Experiencemanager/Cloudmanager
topic-tags: 소개
discoiquuid: Ebcc 91 a 5-BE 9 E -4684-8146-D 88 F 4013 D 4 D 1
translation-type: tm+mt
source-git-commit: 1dfb065c09569f811e5a006d3d74825d3bd7cc8d

---


# 소개 [!UICONTROL Cloud Manager]{#introduction-to-cloud-manager}

## 소개 {#introduction}

[!UICONTROL Cloud Manager]Adobe Managed Cloud 서비스의 일부인 조직은 클라우드를 통해 Experience Manager를 자체 관리할 수 있습니다. 이 프레임워크에는 지속적인 통합과 지속적인 전달 (CI/CD) 프레임워크가 포함되어 있어 IT 팀 및 구현 파트너가 성능이나 보안을 훼손하지 않고도 사용자 정의 또는 업데이트를 신속하게 전달할 수 있습니다.

조직은 [!UICONTROL Cloud Manager] 셀프 서비스 고객 포털을 **사용하여** 다음을 수행할 수 있습니다.

* **지속적인 통합/지속적인 코드 전달** - 시장 출시 시간을 수 개월에서 몇 시간으로 단축합니다.
* **프로덕션 중단을 최소화하기 위해 프로덕션으로 푸시하기 전에 모범 사례를 기반으로 테스트, 성능 테스트 및 보안 유효성 검사를** 수행합니다.
* **업무 시간 외에 자동, 예약 또는 수동 배포를** 통해 최대한 유연하게 제어할 수 있습니다.
* **자동 크기 조절** 기능은 용량을 향상시켜야 하는 필요성을 지능적으로 감지하고 온라인 추가 디스패처/게시 세그먼트를 자동으로 가져옵니다.

다음 이미지는에서 사용되는 CI/CD 프로세스 흐름을 보여줍니다 [!UICONTROL Cloud Manager].

![](assets/screen_shot_2018-05-12at73843pm.png)

## 주요 기능 [!UICONTROL Cloud Manager]{#key-features-in-cloud-manager}

조직은 다음과 같은 기능을 활용할 [!UICONTROL Cloud Manager]수 있습니다.

### 셀프 서비스 인터페이스 {#self-service-interface}

고객을 위한 [!UICONTROL Cloud Manager] 유저 인터페이스 (UI) 를 사용하면 Experience Manager 애플리케이션에서 클라우드 환경과 CI/CD 파이프라인을 손쉽게 이용하고 관리할 수 있습니다.

고객은 애플리케이션 특정 주요 성과 지표 (KPI) - 분당 최대 페이지 뷰 수 및 페이지 로드에 대한 예상 응답 시간을 정의하여 성공적인 배포를 측정하는 데 기초가 됩니다. 여러 팀원의 역할과 권한은 쉽게 정의할 수 있습니다. 새로운 셀프 서비스 인터페이스를 통해 제어할 수 있지만 필요한 지침을 제공할 수 있는 Adobe 내의 전문가와 모범 사례에 대한 링크를 제공합니다.

의 UI를 알아보고 시작하려면 [!UICONTROL Cloud Manager]처음 로그인을 참조하십시오 [](https://helpx.adobe.com/experience-manager/cloud-manager/using/first-time-login.html).

### CI/CD 파이프라인 {#ci-cd-pipeline}

의 [!UICONTROL Cloud Manager] 주요 기능 중 하나는 최적화된 CI/CD 파이프라인을 실행하여 웹 사이트에서 새로운 구성 요소 추가와 같은 사용자 정의 코드 또는 업데이트 제공을 가속화하는 기능입니다.

고객은 [!UICONTROL Cloud Manager] UI를 통해 CI/CD 파이프라인을 구성하고 시작할 수 있습니다. 이 파이프라인은 고품질 애플리케이션만 프로덕션 환경에 전달되도록 철저한 코드 스캔을 실행합니다.

&#39; s UI에서 파이프라인을 구성하는 방법에 대한 자세한 내용은 [!UICONTROL Cloud Manager]CI/CD 파이프라인 [구성을](https://helpx.adobe.com/experience-manager/cloud-manager/using/configuring-pipeline.html)참조하십시오.

### 유연한 배포 모드 {#flexible-deployment-modes}

[!UICONTROL Cloud Manager] 유연하고 구성 가능한 배포 모드를 제공하여 변화하는 비즈니스 요구 사항에 따라 경험을 제공할 수 있습니다.

자동 트리거 모드에서는 코드가 코드 실행과 같은 특정 이벤트를 기반으로 환경에 자동으로 배포됩니다. 또한 지정된 기간 동안 업무 시간 밖에서 코드를 배포할 수 있습니다.

배포 트리거와는 별개로, 품질 검사는 배포가 트리거될 때마다 CI/CD 파이프라인 실행의 일부로 항상 수행됩니다. 품질 검사는 고객 또는 파트너가 아무런 노력을 하지 않고 즉시 제공되는 코드 검사, 보안 테스트 및 성능 테스트를 포함합니다.

코드 및 품질 검사 배포에 대한 자세한 내용은 코드 [배포를 참조하십시오.](deploying-code.md)

### 자동 크기 조절 {#autoscaling}

[!UICONTROL Cloud Manager] 프로덕션 환경이 비정상적으로 높은 부하를 받고 자동 크기 조절 기능을 통해 온라인에서 추가 용량을 자동으로 가져올 때 추가 용량을 필요로 합니다.

자동 크기 조절 이벤트 중에 [!UICONTROL Cloud Manager] 자동 크기 조절 제공 프로세스가 자동으로 실행되고, 자동 크기 조절 이벤트에 대한 알림을 보내고, 분 내에 추가 용량을 가져옵니다. 추가 용량은 동일한 지역의 프로덕션 환경에서 프로비저닝되며, 실행 중인 디스패처/게시 노드와 동일한 시스템 사양을 일치시킵니다.

자동 크기 조절 기능은 디스패처/게시 계층에만 적용되며, 최소 한 개의 Dispatcher/게시 쌍 추가 세그먼트와 최대 10 개의 세그먼트가 있는 가로 크기 조절 방법을 사용하여 항상 실행됩니다. 프로비저닝된 추가 용량은 CSE (Customer Success Engineer) 에 의해 결정된 영업일 기준 10 일 내에 수동으로 조정됩니다.
