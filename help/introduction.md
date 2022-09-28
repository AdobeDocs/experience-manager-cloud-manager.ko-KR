---
title: AMS용 Cloud Manager 소개
description: 여기에서 Adobe Managed Services(AMS)용 Cloud Manager에 대해 알아보고 조직이 클라우드에서 Adobe Experience Manager를 자체 관리하는 방법을 알아보십시오.
exl-id: 58344d8a-b869-4177-a9cf-6a8b7dfe9588
source-git-commit: 14e35882765783b234ca35da14257279af5130a0
workflow-type: ht
source-wordcount: '1287'
ht-degree: 100%

---


# AMS용 [!UICONTROL Cloud Manager] 소개 {#introduction-to-cloud-manager}

여기에서 Adobe Manage Services(AMS)용 Cloud Manager에 대해 알아보고 조직이 클라우드에서 Adobe Experience Manager를 자체 관리하는 방법을 알아보십시오.

>[!CONTEXTUALHELP]
>id="aemcloud_cloudmanager_introduction"
>title="AMS용 Cloud Manager 소개"
>abstract="조직은 클라우드에서 Adobe Experience Manager를 자체 관리할 수 있습니다. 여기에는 IT팀 및 구현 파트너가 성능 또는 보안을 손상하지 않고 맞춤화 또는 업데이트를 신속하게 전달할 수 있는 CI/CD(지속적 통합 및 지속적 배포) 프레임워크가 포함되어 있습니다."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/cloud-manager/programs.html?lang=ko#cloud-manager" text="프로그램 제작"
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/cloud-manager/environments.html?lang=ko#cloud-manager" text="환경 만들기"

## 소개 {#introduction}

Adobe Experience Manager용 [!UICONTROL Cloud Manager]를 사용하면 개발자는 Adobe Experience Manager 모범 사례를 기반으로 구축된 간소화된 워크플로를 통해 효과적인 고객 경험을 만들 수 있습니다. Adobe Experience Manager에 최적화된 CI/CD 파이프라인을 사용하면 코드를 체크인하기만 하면 개발 워크플로를 쉽게 병합할 수 있으며, 이를 통해 제작 준비가 완료된 상태로 전환할 수 있습니다. 빌드 단계에서는 고객에게 안정적인 애플리케이션을 제공하기 위해 사용자 정의 코드 업데이트가 모범 사례와 비교하여 철저히 테스트됩니다. Cloud Manager는 개방형 API 접근 방식을 사용하여 기존 프로세스 및 도구를 중단하지 않고 시스템과 통합할 수 있도록 지원합니다.

>[!NOTE]
>
>이 설명서에서는 Adobe Managed Services(AMS)용 Cloud Manager의 특징 및 기능에 대해 자세히 설명합니다.
>
>AEM as a Cloud Service에 대한 동등한 문서는 [AEM as a Cloud Service 설명서](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/home.html)에서 찾을 수 있습니다.

Cloud Manager를 사용하면 개발 팀이 다음과 같은 기능을 활용할 수 있습니다.

* 출시 시기를 월/주 단위에서 일/시간 단위로 단축하는 코드 지속적 통합/지속적 배포(CI/CD)

* 프로덕션에 투입하기 전에 프로덕션 중단을 최소화하기 위한 모범 사례 기반 코드 검사, 성능 테스트 및 보안 유효성 검사

* 기존 DevOps 프로세스를 보완하는 API 연결

* 용량 증가 필요성을 지능적으로 탐지하고 추가 Dispatcher/게시 세그먼트를 자동으로 온라인 상태로 전환하는 자동 크기 조정

이 이미지는 [!UICONTROL Cloud Manager]에서 사용되는 CI/CD 프로세스 플로우를 보여 주는 이미지입니다.

![CI/CD 플로우](/help/assets/screen_shot_2018-05-12at73843pm.png)

## [!UICONTROL Cloud Manager]의 주요 기능 {#key-features-in-cloud-manager}

다음은 Cloud Manager의 선택된 주요 기능에 대해 자세히 살펴봅니다.

### 셀프서비스 인터페이스 {#self-service-interface}

[!UICONTROL Cloud Manager]의 UI(사용자 인터페이스)를 통해 사용자가 Adobe Experience Manager 애플리케이션의 클라우드 환경과 CI/CD 파이프라인을 쉽게 액세스하고 관리할 수 있습니다.

성공적인 배포를 측정하는 기준을 형성하는 애플리케이션별 KPI(주요 성능 지표)(분당 최대 페이지 보기 횟수 및 페이지 로드 예상 응답 시간)를 사용자가 정의합니다. 여러 팀원의 역할과 권한을 쉽게 정의할 수 있습니다. 셀프서비스 인터페이스를 통해 고객이 다시 제어하게 되었지만 모범 사례 리소스 링크와 필요할 때 필요한 지침을 제공할 수 있는 Adobe 내 전문가 액세스도 제공됩니다.

[!UICONTROL Cloud Manager]의 UI를 탐색하고 시작하려면 [최초 로그인](/help/getting-started/first-time-login.md) 문서를 참조하십시오.

### CI/CD 파이프라인 {#ci-cd-pipeline}

[!UICONTROL Cloud Manager]의 주요 기능 중 하나는 최적화된 CI/CD 파이프라인을 이용하여 사용자 정의 코드 또는 업데이트(예: 웹 사이트에 새 구성 요소 추가)의 게재 속도를 단축하는 기능입니다.

[!UICONTROL Cloud Manager] UI를 통해 고객이 CI/CD 파이프라인을 구성하고 시작할 수 있습니다. 이 파이프라인의 일부로, 고품질 애플리케이션만 프로덕션 환경에 전달되도록 철저한 코드 검사가 실행됩니다.

[!UICONTROL Cloud Manager]의 UI에서 파이프라인 구성에 대한 자세한 내용은 [프로덕션 파이프라인 구성](/help/using/production-pipelines.md) 및 [비프로덕션 파이프라인 구성](/help/using/non-production-pipelines.md)을 참조하십시오.

### 유연한 배포 모드 {#flexible-deployment-modes}

[!UICONTROL Cloud Manager]에서는 변화하는 비즈니스 수요에 따라 경험을 게재할 수 있도록 유연하고 구성 가능한 배포 모드를 제공합니다.

자동 트리거 모드에서는 코드 커밋과 같은 특정 이벤트에 따라 코드가 환경에 자동으로 배포됩니다. 또한, 영업시간 외에도 기간을 지정하여 코드 배포를 예약할 수 있습니다.

배포 트리거와 관계없이, 배포가 트리거될 때마다 품질 검사가 CI/CD 파이프라인 실행의 일부로 항상 수행됩니다. 품질 검사에는 그야말로 사용자 또는 파트너의 노력 없이 즉시 제공되는 코드 검사, 보안 테스트 및 성능 테스트가 포함되어 있습니다.

코드 배포 및 품질 검사에 대한 자세한 내용은 [코드 배포](/help/using/code-deployment.md) 문서를 참조하십시오.

## Cloud Manager의 옵션 기능 {#optional-features-in-cloud-manager}

Cloud Manager는 특정 환경 설정 및 필요에 따라 프로젝트에 도움이 될 수 있는 추가 고급 기능을 제공합니다. 이러한 기능에 관심이 있는 경우 CSE(Customer Success Engineer) 또는 Adobe 담당자에게 연락하여 자세한 내용을 문의하십시오.

### 자동 크기 조정 {#autoscaling}

프로덕션 환경에 비정상적으로 높은 부하가 걸리면 [!UICONTROL Cloud Manager]는 추가 용량의 필요성을 감지하고 자동 크기 조정 기능을 사용하여 자동으로 추가 용량을 온라인으로 전환합니다.

이런 이벤트 동안 자동으로 [!UICONTROL Cloud Manager]에서 자동 크기 조정 제공 프로세스를 트리거하고, 자동 크기 조정 이벤트 알림을 보내고, 몇 분 안에 추가 용량을 온라인 상태로 전환합니다. 추가 용량은 영역이 같고 실행 중인 Dispatcher/게시 노드와 시스템 사양이 일치하는 프로덕션 환경에서 제공됩니다.

자동 크기 조정 기능은 Dispatcher/게시 계층에만 적용되고, 항상 가로 크기 조정 방법을 사용하여 실행되며, 추가 Dispatcher/게시 쌍 세그먼트가 1~10개 있습니다. 제공된 추가 용량은 CSE(Customer Success Engineer)가 결정하는 10일 이내 기간에 수동으로 조정됩니다.

>[!NOTE]
>
>자동 크기 조정 기능이 애플리케이션에 적합한지 여부를 알아보려면 CSE 또는 Adobe 담당자에게 문의하십시오.

### 파란색/녹색 배포 {#blue-green}

파란색/녹색 배포는 파란색과 녹색이라는 두 개의 동일한 프로덕션 환경을 실행함으로써 가동 중단과 위험을 줄이는 기법입니다.

항상 하나의 환경만 활성 상태이며, 활성 환경은 모든 프로덕션 트래픽 서비스에 사용됩니다. 일반적으로 파란색은 현재 라이브 환경이고 녹색은 유휴 상태입니다.

* 파란색/녹색 배포는 Cloud Manager CI/CD 파이프라인의 추가 기능으로, 두 번째 게시 및 Dispatcher 인스턴스 집합(녹색)이 생성되어 배포에 사용됩니다. 그런 다음 녹색 인스턴스가 프로덕션 로드 밸런서에 연결되고 이전 인스턴스(파란색)가 제거되고 종료됩니다.
* 이러한 파란색/녹색 구현은 인스턴스를 일시적인 것으로 취급하며 파란색/녹색 파이프라인을 반복할 때마다 새로운 게시 및 Dispatcher 서버 세트가 생성됩니다.
* 설정의 일부로 녹색 로드 밸런서가 생성됩니다. 이 로드 밸런서는 변경되지 않으며 녹색 또는 &quot;테스트&quot; URL을 가리켜야 합니다.
* 파란색/녹색 배포 중에 기존 게시/Dispatcher 계층의 정확한 복제본이 생성됩니다.

#### 파란색/녹색 배포 플로우 {#flow}

파란색/녹색 배포를 활성화한 경우 배포 플로우가 표준 Cloud Service 배포 플로우와 다릅니다.

| 단계 | 파란색/녹색 배포 | 표준 배포 |
|---|---|---|
| 1 | 작성자에 배포 | 작성자에 배포 |
| 2 | 테스트를 위해 일시 중지 | - |
| 3 | 녹색 인프라 생성됨 | - |
| 4 | 녹색 게시/Dispatcher 계층에 배포 | 게시자에 배포 |
| 5 | 테스트를 위해 일시 중지(최대 24시간) | - |
| 6 | 프로덕션 로드 밸런서에 녹색 인프라가 추가됨 | - |
| 7 | 프로덕션 로드 밸런서에서 파란색 인프라가 제거됨- |
| 8 | 파란색 인프라가 자동으로 종료됨 | - |

#### 파란색/녹색 구현 {#implementing}

프로덕션 배포에 Cloud Manager를 사용하는 모든 AMS 사용자는 파란색/녹색 배포를 사용할 수 있습니다. 그러나 파란색/녹색 배포를 사용하려면 Adobe CSE에서 환경 및 설정에 대한 추가 유효성 검사가 필요합니다.

파란색/녹색 배포에 관심이 있는 경우 다음 요구 사항 및 제한 사항을 고려하여 CSE에 문의하십시오.

#### 요구 사항 및 제한 사항 {#limitations}

* 파란색/녹색은 게시/Dispatcher 쌍에만 사용할 수 있습니다.
* 미리보기 Dispatcher/게시 쌍은 파란색/녹색 배포의 일부가 아닙니다.
* 모든 Dispatcher/게시 쌍은 다른 Dispatcher/게시 쌍과 동일합니다.
* 파란색/녹색은 프로덕션 환경에만 사용할 수 있습니다.
* AWS뿐만 아니라 Azure에서도 파란색/녹색을 사용할 수 있습니다.
* 파란색/녹색은 Assets 전용 고객에게는 제공되지 않습니다.
