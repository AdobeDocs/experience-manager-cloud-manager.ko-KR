---
title: 프로그램 설정
description: 온보딩 후에는 비즈니스 소유자가 프로그램의 초기 설정을 수행해야 합니다.
exl-id: 795c7112-d564-4fbf-96a1-152a6c286bf2
source-git-commit: 6572c16aea2c5d2d1032ca5b0f5d75ade65c3a19
workflow-type: tm+mt
source-wordcount: '581'
ht-degree: 1%

---


# 프로그램 설정 {#program-setup}

온보딩 후 비즈니스 소유자는 프로그램 설명을 설정하고 성능 테스트에 사용되는 주요 성과 지표(KPI)를 정의하는 등 프로그램의 초기 설정을 완료합니다.

## 프로그램 설정 [!UICONTROL Cloud Manager] {#program-setup-cloud-manager}

다음 단계에 따라 프로그램을 설정하고 KPI를 정의합니다.

1. Cloud Manager에 로그인 위치 [`https://my.cloudmanager.adobe.com`](https://my.cloudmanager.adobe.com) 적절한 조직을 선택합니다.

1. 클릭 **설치 프로그램** 설정 프로세스를 시작하려면

   ![프로그램 설정](/help/assets/set-up-program/setup1.png)

1. 에서 **설치 프로그램** 대화 상자는 다음 세 개의 탭에 프로그램 정보를 입력할 수 있습니다.

   * **일반**
   * **KPI**
   * **프로비저닝**

1. 설정 **일반** 탭을 클릭하고 프로그램에 대한 설명을 추가하고 필요에 따라 아이콘을 클릭하여 축소판을 업로드합니다 **사진 변경**.

   ![일반 탭](/help/assets/Setup_Program-General.png)

1. 설정 **KPI** 탭에서 KPI를 정의합니다. 이 예제에 대해 별도의 KPI가 정의됩니다 **AEM Sites** 및 **AEM Assets**. 라이선스를 구입한 제품에 대한 KPI를 지정할 수 있습니다.

   * 섹션을 참조하십시오 [KPI](#kpis) cloud Manager에서 KPI를 측정하는 방법에 대한 자세한 내용.

   ![KPI 정의](/help/assets/Setup_Program-KPIs.png)

1. 설정 **프로비저닝** 프로그램에 대해 자동 크기 조절이 활성화된 경우 탭에서 환경에 대한 온디맨드 크기 조절 옵션을 정의할 수 있습니다.

   * 자동 크기 조절은 프로덕션 환경에만 적용되며 모든 고객 프로그램에는 사용할 수 없습니다.

   ![프로비저닝 옵션](/help/assets/Setup_Program-Provisioning.png)

1. 클릭 **저장** 설정 마법사를 완료하려면

프로그램이 생성됩니다. 프로그램을 사용할 준비가 되기 전에 리소스를 제공하려면 몇 분이 걸릴 수 있습니다.

## 프로그램 편집 {#editing-program}

프로그램을 설정한 후에 편집할 수 있습니다. 프로그램을 편집하려면 다음 단계를 따르십시오.

1. Cloud Manager에 로그인 위치 [`https://my.cloudmanager.adobe.com`](https://my.cloudmanager.adobe.com) 적절한 조직을 선택합니다.

1. Cloud Manager 홈 화면에서 프로그램으로 이동합니다.

1. 클릭 **프로그램 편집** 프로그램을 업데이트하거나 수정하려면 **개요** 페이지.

   ![프로그램 편집 옵션](/help/assets/set-up-program/edit-program1.png)

1. 다음 **프로그램 편집** 프로그램을 업데이트할 수 있는 대화 상자가 표시됩니다. 섹션을 참조하십시오 [Cloud Manager를 사용한 프로그램 설정](#program-setup-cloud-manager) 사용 가능한 필드에 대한 자세한 내용을 참조하십시오.

   ![프로그램 편집 대화 상자](/help/assets/set-up-program/edit-program-general.png)

1. 클릭 **업데이트** 변경 사항을 저장하려면 을 클릭합니다.

변경 사항은 Cloud Manager에 즉시 저장되지만, 다음 파이프라인이 실행될 때까지 환경에 반영되지 않습니다.

파이프라인을 아직 만들지 않은 경우 문서를 참조하십시오 [프로덕션 파이프라인 구성](/help/using/production-pipelines.md) 및 [비프로덕션 파이프라인 구성.](/help/using/non-production-pipelines.md)

## 프로그램 간 전환 {#swithing-programs}

프로그램에서 작업할 때 Cloud Manager 개요 페이지로 돌아가지 않고 다른 프로그램으로 빠르게 전환할 수 있습니다.

작업 표시줄을 사용하여 다른 프로그램으로 전환하거나 현재 프로그램을 편집하거나 새 프로그램을 추가합니다.

![프로그램 전환기](/help/assets/set-up-program/setup2.png)

## KPI {#kpis}

사이트 KPI는 스테이징 환경에서 실행되는 테스트에서 측정됩니다. 일반적으로 이러한 KPI는 스테이징 환경의 기능에 맞게 크기가 조절됩니다.

예를 들어, 사용자는 프로덕션 환경에서 분당 평균 1000개의 페이지 보기 수를 예상하며, 프로덕션에 4개의 디스패처/게시 서버가 있는 경우 이를 분당 250개의 페이지 보기 수로 조정해야 합니다. 이 경우 스테이징 환경이 단일 디스패처/게시 서버 쌍으로만 구성된다고 가정합니다.

자산 성능 테스트는 30분 테스트 기간 동안 자산을 반복적으로 업로드하고, 다양한 시스템 수준 지표뿐만 아니라 각 자산에 대한 처리 시간을 측정하여 수행됩니다.

프로덕션 환경 앞에 Akamai 또는 CloudFront와 같은 CDN(콘텐츠 전달 네트워크)이 있을 수 있습니다. 이후 [!UICONTROL Cloud Manager] 스테이징 환경에 대해 직접 테스트하는 경우, KPI는 CDN을 통과해야 하는 트래픽(즉, 캐시 누락)만 반영해야 합니다. 일반적으로 이는 전체 프로덕션 트래픽의 비교적 작은 하위 집합입니다.

## 비디오 개요 {#video}

>[!VIDEO](https://video.tv.adobe.com/v/26313/)
