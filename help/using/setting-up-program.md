---
title: 프로그램 설정
seo-title: 프로그램 설정
description: 온보딩 후에는 비즈니스 소유자가 프로그램의 초기 설정을 수행해야 합니다.
seo-description: '온보딩 후에 비즈니스 소유자는 AEM Cloud Manager Adobe의 초기 설정을 수행해야 합니다. 여기에는 프로그램 설명을 설정하고 성능 테스트에 사용할 KPI를 정의하는 작업이 포함됩니다. '
feature: 시작하기
exl-id: 795c7112-d564-4fbf-96a1-152a6c286bf2
source-git-commit: 71a6f2709efb9c4c3831deaa1ce89d93e30b775c
workflow-type: tm+mt
source-wordcount: '727'
ht-degree: 2%

---

# 프로그램 설정 {#setup-your-program}

온보딩 후 비즈니스 소유자는 프로그램의 초기 설정을 완료해야 합니다. 여기에는 프로그램 설명을 설정하고 성능 테스트에 사용할 주요 성능 지표(KPI)를 정의하는 작업이 포함됩니다. 선택적으로 축소판을 업로드할 수 있습니다. 또한 비즈니스 소유자는 프로그램을 설정하는 동안 환경 프로비저닝을 구성할 수 있습니다.

정의된 KPI는 파이프라인이 실행될 때마다 전달되는 성능 테스트의 기준선 역할을 합니다.

>[!NOTE]
>정의된 KPI는 **stage** 환경에서 실행되는 테스트에서 측정됩니다. 일반적으로 이러한 KPI는 스테이지 환경의 기능에 맞게 축소됩니다.
>예를 들어, 사용자는 프로덕션 **환경**에서 분당 평균 1000개의 페이지 보기가 예상되며 프로덕션에 4개의 디스패처/게시 서버가 있는 경우 이를 분당 250개의 페이지 보기로 조정해야 합니다(스테이지 환경이 단일 디스패처/게시 서버 쌍으로만 구성된다고 가정할 경우).
>또한 많은 사용자에게 프로덕션 환경 앞에 Akamai 또는 CloudFront와 같은 CDN(Content Delivery Network)이 제공됩니다. 스테이지 환경에 대해 직접 테스트하므로 KPI는 CDN을 통과하는 예상 트래픽, 즉 캐시 누락만 반영해야 합니다. [!UICONTROL Cloud Manager] 일반적으로 이는 전체 프로덕션 트래픽의 비교적 작은 하위 집합입니다.

## [!UICONTROL Cloud Manager]을 사용하여 프로그램 {#using-cloud-manager-to-setup-your-program} 설정

프로그램을 설정하고 KPI를 정의하려면 아래 단계를 따르십시오.

1. **설치 프로그램**&#x200B;을 클릭하여 [!UICONTROL Cloud Manager]에서 설정 프로세스를 시작합니다.

   ![image1](assets/set-up-program/setup1.png)

   >[!NOTE]
   > 아래 그림과 같이 항상 작업 표시줄에서 새 프로그램을 전환, 편집 또는 추가할 수 있습니다.

   ![image1](assets/set-up-program/setup2.png)


1. **설치 프로그램** 화면에 프로그램 정보 편집이 표시됩니다.

1. **일반**, **KPI** 및 **프로비저닝** 탭이 3개 표시됩니다.

1. **일반** 탭에서 축소판을 프로그램에 업로드합니다. 프로그램에 관련 설명을 추가할 수도 있습니다.

   ![](assets/Setup_Program-General.png)

1. **KPI**&#x200B;에서 두 개의 KPI(각 배포에 대한 기대)를 정의할 수 있습니다. 별도의 KPI는 **AEM Sites** 및 **AEM Assets**&#x200B;에 대해 정의됩니다. 라이선스를 구입한 제품에 대한 KPI를 지정할 수 있습니다.

   **AEM Sites**

   1. 허용되는 95번째 백분위수 응답 시간은 얼마입니까?

      * 권장 값 - 3초
   1. 최대 로드 시 분당 페이지 보기 수는 몇 개입니까?

      * 권장 값 - 분당 200개의 페이지 보기 수

   **AEM Assets**

   초기 릴리스 이후 Cloud Manager는 AEM Sites 프로그램에 대한 성능 테스트를 실행할 수 있었습니다. 이 릴리스에서는 AEM Assets 프로그램에 대한 성능 테스트를 실행하기 위한 기능도 추가되었습니다. 자산 성능 테스트는 30분 테스트 기간 동안 자산을 반복적으로 업로드하고, 다양한 시스템 수준 지표뿐만 아니라 각 자산에 대한 처리 시간을 측정하여 수행됩니다.
프로그램 설정 중에 자산별 KPI가 지정됩니다.

   * 95번째 백분위수 처리 시간
   * 분당 업로드된 자산

   ![](assets/Setup_Program-KPIs.png)

1. **프로비저닝**&#x200B;에서 프로그램의 프로덕션 및 비프로덕션 환경에 대한 프로비저닝 구성을 보거나 편집할 수 있습니다. 프로그램에 대해 자동 크기 조절이 설정된 경우 **자동 크기 조절이**&#x200B;에 표시됩니다.

   >[!NOTE]
   >자동 크기 조정 기능은 프로덕션 환경에만 적용되며 모든 고객 프로그램에는 사용할 수 없습니다.

   ![](assets/Setup_Program-Provisioning.png)

1. **저장**&#x200B;을 클릭하여 설정 마법사를 완료합니다.

   >[!NOTE]
   >초기 프로그램이 이미 설정되면 언제든지 프로그램을 편집할 수 있습니다. 자세한 내용은 아래 절차를 따르십시오.

## 프로그램 편집 {#editing-program}

1. **Cloud Manager** 홈 화면에서 프로그램으로 이동합니다.

1. 아래 그림과 같이 **개요** 페이지에서 프로그램을 업데이트하거나 수정하려면 **프로그램 편집**&#x200B;을 클릭하십시오.

   ![](assets/set-up-program/edit-program1.png)

1. 프로그램을 업데이트하거나 수정할 수 있는 **프로그램 편집** 화면이 표시됩니다.

   **일반** 탭에서 프로그램 설명을 업데이트할 수 있습니다.

   ![](assets/set-up-program/edit-program-general.png)

   **KPI** 탭으로 이동하여 AEM Sites 및 자산에 대한 정보를 업데이트합니다.

   ![](assets/set-up-program/edit-program-kpi.png)

   또한 **프로비저닝** 탭으로 이동하여 프로그램의 프로덕션 및 비프로덕션 환경에 대한 프로비저닝 구성을 편집할 수 있습니다.

   ![](assets/set-up-program/edit-program-provision.png)

1. **업데이트**&#x200B;를 클릭하여 편집 내용을 저장합니다.

## 다음 단계 {#the-next-steps}

이미 파이프라인을 설정한 경우 다음 실행에서는 업데이트된 설정을 고려합니다. 파이프라인을 아직 설정하지 않은 경우 절차에 따라 파이프라인을 먼저 설정합니다.

파이프라인을 설정하려면 [CI/CD 파이프라인 구성](https://helpx.adobe.com/experience-manager/cloud-manager/using/configuring-pipeline.html)을 참조하십시오.
