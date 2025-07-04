---
title: 환경 모니터링
description: Cloud Manager에서 환경을 모니터링하는 방법에 대해 알아봅니다.
exl-id: 32886133-d6c0-4aed-8bb0-81b84f63e825
source-git-commit: fb3c2b3450cfbbd402e9e0635b7ae1bd71ce0501
workflow-type: tm+mt
source-wordcount: '865'
ht-degree: 75%

---


# 환경 모니터링 {#monitoring-environments}

Cloud Manager에서 환경을 모니터링하는 방법에 대해 알아봅니다.

## 지표 임계값 {#thresholds}

[!UICONTROL Cloud Manager]의 시스템 모니터링은 환경 내의 개별 인스턴스를 관찰하고 각 인스턴스에 대한 다양한 지표를 추적하여 수행됩니다. 각 지표에는 *경고* 임계값과 *중요* 임계값이라는 두 가지 정의된 임계값이 있습니다.

지표가 경고 임계값을 초과하는 (단, 중요 임계값 미만) 경우 경고 상태에 있는 것으로 간주됩니다.

지표가 중요 임계값을 초과하는 경우 중요 상태에 있는 것으로 간주됩니다.

Adobe Managed Services는 임계값을 설정하는데, [!UICONTROL Cloud Manager]에서 확인할 수 있습니다. 대부분의 경우 임계값은 고객 간에 일관되지만 Adobe Managed Services가 특정 고객 요구 사항에 맞게 임계값을 편집하는 경우가 있습니다. 임계값에 대한 질문이 있는 경우 고객 성공 엔지니어(CSE)에게 문의하십시오.

## 시스템 모니터링 액세스 {#accessing-system-monitoring}

1. [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com)에서 Cloud Manager에 로그인한 다음 적절한 조직과 프로그램을 선택합니다.

1. 모니터링하려는 프로그램의 ![기타 아이콘(줄임표)](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg)을 클릭합니다.
1. 메뉴의 **관리**&#x200B;에서 **모니터링 표시**&#x200B;를 클릭하여 시스템 모니터링 정보를 표시하는 **보고서** 페이지를 엽니다.

   ![설정](/help/assets/first-timea1.png)

.

## 시스템 모니터링 개요 {#system-monitoring-overview}

**보고서** 페이지의 **시스템 모니터링** 섹션에는 프로그램에서 모니터링하는 환경이 나열됩니다. 이 보고서는 다음 네 가지 카테고리에 걸쳐 높은 수준의 상태를 보고합니다.

* 호스트
* 스토리지
* 네트워크
* 애플리케이션

각 카테고리의 상태는 개별 지표의 요약입니다. 카테고리의 지표가 중요 상태에 있는 경우 개요 페이지의 목적에 따라 전체 카테고리가 중요 상태에 있습니다. 환경 수준 및 인스턴스 수준에서 동일한 요약을 볼 수 있습니다.

![시스템 모니터링 개요](/help/assets/System-Monitoring-Reports.png)

>[!NOTE]
>
>기본적으로 이 페이지로 이동하면 프로덕션 환경 인스턴스가 표시되지만 다른 환경도 볼 수 있습니다.

## 시스템 모니터링 세부 정보 {#system-monitoring-detail}

특정 지표의 세부 정보를 보려면 특정 인스턴스의 카테고리 열 중 하나를 클릭하거나 왼쪽 탐색에서 카테고리 제목을 클릭합니다. 각 세부 정보 페이지에는 해당 카테고리 내의 지표에 대한 일련의 그래프가 표시됩니다. 환경의 모든 인스턴스 또는 특정 인스턴스에 대한 지표를 볼 수 있습니다. 오른쪽 상단에 있는 드롭다운 상자를 사용하여 환경과 인스턴스 사이를 전환할 수 있습니다.

![환경 선택](/help/assets/System_Monitoring1.png)

왼쪽의 탐색에는 현재 선택한 카테고리 내에서 사용 가능한 지표가 표시되며, 현재 선택한 환경 및 인스턴스에 대한 데이터가 있습니다.

개별 그래프는 임계값과 함께 시간 경과에 따른 데이터의 상태와 그래프를 보여 줍니다. 여러 인스턴스가 표시되는 경우 각 인스턴스의 데이터는 별도의 시리즈에 저장됩니다.

![지표 그래프](/help/assets/Monitoring_Graphs1.png)

범례의 시리즈를 클릭하여 그래프에서 개별 시리즈를 숨길 수 있습니다.
예를 들어 경고 임계값 시리즈를 클릭하면 중요 임계값만 표시됩니다.

![그래프 수정](/help/assets/Monitoring_Graphs2.png)

### 지표 정의 {#metric-definitions}

#### 호스트 {#host}

* **`Load Per Core`**: CPU에서 실행 중인 프로세스 수입니다. 또는 대기 상태에 있는 대기 중인 프로세스의 수가 1분(load1), 5분(load5) 및 15분(load15) 동안 평균한 것입니다.
* **P`rocess Count`**: 현재 열려 있는 프로세스 수입니다.
* **`User Count`**: 활성 셸 세션을 가진 사용자 수입니다.
* **`Memory Usage`**: 현재 할당된 시스템 메모리의 비율입니다.
* **`JVM Memory`**: 할당된 Java 힙의 크기(메가바이트)입니다.
* **`Old Generation Space`**: 현재 할당된 JVM 이전 세대 메모리의 비율입니다.

#### 네트워크 {#network}

* **`CQ Port Check`**: AEM 또는 Dispatcher 포트에 액세스하는 데 걸리는 응답 시간(초)입니다. 작성자, 게시 및 Dispatcher에 대한 다양한 지표가 있습니다.

#### 스토리지 {#storage}

* **`Disk Space`**: 호스트의 각 마운트 지점에 사용된 디스크 공간(MB)입니다. 각 마운트 지점에 대한 다양한 지표가 있습니다. 최소한 `/` 및 `/mnt`에 대한 지표가 있지만 특정 인스턴스 구성에 따라 추가 마운트 지점 지표를 사용할 수 있습니다.
* **`Folder Size`**
* **`AEM Segment Store`**: AEM 세그먼트 저장소에 사용된 디스크 공간(기가바이트).

#### 애플리케이션 {#application}

* **`Replication Agent`**: 테스트 복제 이벤트의 시간(초)
   * 각 복제 에이전트에 대한 별도의 지표가 있습니다.
* **`Dispatcher Flush`**: 현재 Dispatcher 플러시 큐에 있는 항목 수

## SLA 보고 {#sla-reporting}

계약된 SLA(서비스 수준 계약)와 관련하여 프로덕션 AEM 환경의 성능을 확인할 수 있습니다.

다음 그래프는 2019년 월별 SLA 달성을 보여 줍니다.

![SLA 2018 그래프](/help/assets/SLA-Reports-one.png)

시스템 모니터링 그래프와 마찬가지로 데이터 지점을 롤오버하면 해당 월의 특정 값이 표시됩니다.

![데이터 지점 롤오버](/help/assets/SLA-Reports-two.png)

이 그래프 아래의 **이벤트 분석** 섹션은 현재 선택된 해 동안 프로그램에 대해 발생한 일련의 인시던트를 보여 줍니다. 각 인시던트에는 시간 범위, 원인 및 댓글 집합이 있습니다.

![이벤트 분석](/help/assets/sla-reporting3.png)

## SLA 지표 {#sla-metrics}

* **`Author Contract`**: 작성자 계층에 대해 Adobe Managed Services과의 계약에 정의된 SLA.
* **`AMS Author SLA`**: 공급업체 또는 Adobe에 의해 발생한 인시던트, 프로덕션 작성자 계층의 측정된 가동 시간입니다.
* **`Author SLA`**: 유지 관리 기간과 같은 예약된 가동 중단을 무시하는 작성자 계층의 측정된 가동 시간입니다.
* **`End User Contract`**: 게시 계층에 대해 Adobe Managed Services과의 계약에 정의된 SLA.
* **`AMS End User SLA`**: 공급업체 또는 Adobe에 의해 발생한 프로덕션 게시 계층, 팩토링 인시던트의 측정된 런타임입니다.
* **`End User SLA`**: 유지 관리 기간과 같은 예약된 가동 중단을 무시하는 게시 계층의 측정된 가동 시간입니다.

## 비디오 튜토리얼 {#video-tutorial}

이 비디오는 프로그램 환경을 보기 위해 Cloud Manager Reports에서 생성한 차트를 사용하는 방법에 대한 개요를 제공합니다.

>[!VIDEO](https://video.tv.adobe.com/v/34275?captions=kor)
