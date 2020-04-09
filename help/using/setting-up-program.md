---
title: 프로그램 설정
seo-title: 프로그램 설정
description: 탑승 후에, 사업 소유자는 프로그램의 초기 설정을 수행해야 할 것입니다.
seo-description: '온보딩 후 비즈니스 소유자는 Adobe AEM Cloud Manager의 초기 설정을 수행해야 합니다. 여기에는 프로그램 설명을 설정하고 성능 테스트에 사용할 KPI를 정의하는 작업이 포함됩니다. '
uuid: 9ecf8743-1f5a-4744-86af-e2256567642f
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: getting-started
discoiquuid: c2393540-e852-4f7c-aafd-1427209065d2
translation-type: tm+mt
source-git-commit: 16893b8bcd2b2d681a14bb6be3786e358e1952fb

---


# 프로그램 설정 {#setup-your-program}

탑승 후, 사업 소유자는 프로그램의 초기 설정을 완료해야 합니다. 여기에는 프로그램 설명을 설정하고 성능 테스트에 사용할 주요 성능 지표(KPI)를 정의하는 작업이 포함됩니다. 축소판을 업로드할 수도 있습니다. 또한 비즈니스 소유자는 프로그램을 설정하는 동안 환경 프로비저닝을 구성할 수 있습니다.

정의된 KPI는 파이프라인이 실행될 때마다 전달되는 성능 테스트의 기준 요소로 사용됩니다.

>[!NOTE]
>
>정의된 KPI는 **단계** 환경에서 실행되는 테스트에서 측정됩니다. 일반적으로 이러한 KPI는 스테이지 환경의 기능에 맞게 축소됩니다.
>
>예를 들어 사용자는 제작 환경에서 분당 평균 1,000개의 페이지 보기를 예상하고 제작 **시 4개의 디스패처** /게시 서버가 이를 분당 250개의 페이지 뷰로 조정해야 합니다(스테이지 환경이 단일 디스패처/게시 서버 쌍으로만 구성된다고 가정함).
>
>또한 대부분의 사용자는 제작 환경 앞에 Akamai 또는 CloudFront와 같은 CDN(Content Delivery Network)을 갖게 됩니다. 스테이지 환경에 대해 직접 [!UICONTROL Cloud Manager] 테스트를 실시하므로 KPI는 CDN을 통과하는 예상 트래픽(즉, 캐시 누락)만 반영해야 합니다. 일반적으로 전체 프로덕션 트래픽의 비교적 작은 하위 세트가 됩니다.

## 프로그램 [!UICONTROL Cloud Manager] 설정에 사용 {#using-cloud-manager-to-setup-your-program}

아래 절차에 따라 프로그램을 설정하고 KPI를 정의합니다.

1. 설정 **프로그램을** 클릭하여 에서 설정 프로세스를 시작합니다 [!UICONTROL Cloud Manager].

   ![image1](assets/set-up-program/setup1.png)

   >[!NOTE]
   > 아래 그림과 같이 작업 표시줄에서 언제든지 프로그램을 전환, 편집 또는 추가할 수 있습니다.

   ![image1](assets/set-up-program/setup2.png)


1. 설정 **프로그램** 화면에 프로그램 정보 편집 화면이 표시됩니다.

1. 일반 사항, KPI 및 **프로비저닝****탭**&#x200B;세 가지 옵션이 **표시됩니다** .

1. 일반 **탭에서** 축소판을 프로그램에 업로드합니다. 프로그램에 관련 설명을 추가할 수도 있습니다.

   ![](assets/Setup_Program-General.png)

1. KPI **에서**&#x200B;두 개의 KPI를 정의할 수 있습니다(각 배포에 대한 기대). 개별 KPI는 AEM Sites **및 AEM Assets에** 대해 **정의됩니다**. 라이선스를 구입한 제품의 KPI를 지정할 수 있습니다.

   **AEM Sites**

   1. 허용되는 95번째 백분위수 응답 시간은 어떻게 됩니까?

      * 권장 값 - 3초
   1. 최대 로드 시 분당 페이지 보기 수는 얼마나 됩니까?

      * 권장 값 - 분당 200페이지 보기
   **AEM Assets**

   초기 릴리스 이후 Cloud Manager는 AEM Sites 프로그램에 대한 성능 테스트를 실행할 수 있었습니다. 이번 릴리스에서는 AEM Assets 프로그램에 대한 성능 테스트를 실행하는 기능도 추가되었습니다. 자산 성과 테스트는 30분 테스트 기간 동안 자산을 반복적으로 업로드하고 각 자산에 대한 처리 시간과 다양한 시스템 수준 지표를 측정하여 수행됩니다.
프로그램 설정 중에 자산별 KPI가 지정됩니다.

   * 95번째 백분위수 처리 시간
   * 분당 업로드된 자산
   ![](assets/Setup_Program-KPIs.png)

1. 프로비저닝 **아래에서**&#x200B;프로그램의 프로덕션 및 비프로덕션 환경에 대한 프로비저닝 구성을 보거나 편집할 수 있습니다. 자동 크기 조정이 **설정되어**&#x200B;있는 경우, 자동 크기 조절이 켜져 있는 것을 볼 수 있습니다.

   >[!NOTE]
   >
   >* 자동 처리 기능은 프로덕션 환경에만 적용되며 일부 고객 프로그램에서는 사용할 수 없습니다.
   >* 의 이번 릴리스에서는 On-Demand 크기 조정을 사용할 수 없습니다 [!UICONTROL Cloud Manager].


   ![](assets/Setup_Program-Provisioning.png)

1. 저장을 **클릭하여** 설치 마법사를 완료합니다.

   >[!NOTE]
   >
   >초기 프로그램이 이미 설정된 후에는 언제든지 프로그램을 편집할 수 있습니다. 자세한 내용은 아래 절차를 따르십시오.

## 프로그램 편집

1. Cloud Manager 홈 화면에서 **솔루션으로** 이동합니다.

   ![](assets/SetUpProgram5.png)

1. 솔루션을 선택하고 편집을 클릭하여 **프로그램을** 업데이트하거나 수정합니다(아래 그림 참조).

   ![](assets/SetUpProgram6.png)

1. 프로그램 **편집** 화면이 표시되어 프로그램을 업데이트하거나 수정할 수 있습니다.

   ![](assets/Editing_Program-screen3.png)

## 다음 단계 {#the-next-steps}

이미 파이프라인을 설정한 **경우**&#x200B;다음 실행에서는 업데이트된 설정을 고려합니다. 아직 파이프라인을 설정하지 않은 경우 단계에 따라 먼저 파이프라인을 설정합니다.

파이프라인을 [설정하려면 CI/CD](https://helpx.adobe.com/experience-manager/cloud-manager/using/configuring-pipeline.html) 파이프라인 구성을 참조하십시오.
