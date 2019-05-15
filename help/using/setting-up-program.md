---
title: 프로그램 설정
seo-title: 프로그램 설정
description: 출장 후 비즈니스 소유자가 프로그램의 초기 설정을 수행해야 합니다.
seo-description: '출장 후 비즈니스 소유자가 Adobe AEM 클라우드 관리자를 처음 설정해야 합니다. 여기에는 프로그램 설명을 설정하고 성능 테스트에 사용될 KPI를 정의하는 작업이 포함됩니다. '
uuid: 9 ECF 8743-1 F 5 A -4744-86 AF-E 2256567642 F
contentOwner: Jsyal
products: sg_ Experiencemanager/Cloudmanager
topic-tags: Getting-Started
discoiquuid: C 2393540-E 852-4 F 7 C-AAFD -1427209065 D 2
translation-type: tm+mt
source-git-commit: 1dfb065c09569f811e5a006d3d74825d3bd7cc8d

---


# 프로그램 설정 {#setup-your-program}

출장 후 비즈니스 소유자가 프로그램의 초기 설정을 완료해야 합니다. 여기에는 프로그램 설명을 설정하고 성능 테스트에 사용될 KPI (Key Performance Indicator) 를 정의하는 작업이 포함됩니다. 선택적으로 썸네일을 업로드할 수 있습니다. 또한 비즈니스 소유자는 프로그램을 설정할 때 환경을 프로비저닝할 수 있습니다.

정의된 KPI는 파이프라인이 실행될 때마다 전달되는 성능 테스트의 기준선 역할을 합니다.

>[!NOTE]
>
>정의된 KPI는 **스테이지** 환경에서 실행된 테스트에 대해 측정됩니다. 일반적으로 이러한 KPI는 스테이지 환경의 기능에 맞게 축소됩니다.
>
>예를 들어 사용자는 프로덕션 **환경에서** 분당 평균 1,000 페이지 뷰를 기대하고 있으며 프로덕션 시 발송자/게시 서버가 4 개 있는 경우 분당 250 페이지 보기로 크기를 조절해야 합니다 (스테이지 환경이 단일 발송인/게시 서버 쌍으로 구성되어 있다고 가정할 경우).
>
>또한 대부분의 사용자는 프로덕션 환경 앞에서 Akamai 또는 CloudFront와 같은 CDN (Content Delivery Network) 를 갖게 됩니다. 스테이지 환경에 대한 [!UICONTROL Cloud Manager] 테스트 이후 KPI는 CDN를 통과하는 트래픽, 즉 캐시 실패를 반영해야 합니다. 일반적으로 이는 총 프로덕션 트래픽 중 비교적 적은 하위 세트가 됩니다.

## 프로그램을 설정하는 [!UICONTROL Cloud Manager] 데 사용 {#using-cloud-manager-to-setup-your-program}

프로그램을 설정하고 KPI를 정의하려면 아래 절차를 따르십시오.

1. **설정 프로그램을** 클릭하여 설정 [!UICONTROL Cloud Manager]프로세스를 시작합니다.

   ![](assets/SetUpProgram1.png)

1. **설정 프로그램** 화면에는 프로그램 편집 정보가 표시됩니다.

1. 세 가지 옵션이 **일반**, **KPI**및 **프로비저닝** 탭으로 표시됩니다.

1. **일반** 탭에서 프로그램에 썸네일을 업로드합니다. 프로그램에 관련 설명을 추가할 수도 있습니다.

   ![](assets/Setup_Program-General.png)

1. **KPI**아래에서 두 KPI를 정의할 수 있습니다 (각 배포에 대한 기대치). 개별 KPI는 **AEM Sites** 및 **AEM 자산에 대해 정의됩니다**. 라이선스가 부여된 제품에 대한 KPI를 지정할 수 있습니다.

   **AEM Sites**

   1. 허용되는 95 번째 백분위수 응답 시간은 언제입니까?

      * 권장 값 - 3 초
   1. 피크 로드 아래 분당 페이지 뷰 수는 몇 개입니까?

      * 권장 값 - 분당 200 페이지 보기
   **AEM Assets**

   초기 릴리스 이후 클라우드 관리자는 AEM Sites 프로그램에 대한 성능 테스트를 실행할 수 있었습니다. 이번 릴리스에서는 AEM Assets 프로그램에도 성능 테스트를 실행하는 기능이 추가되었습니다. 자산 성과 테스트는 30 분 테스트 기간 동안 반복적으로 자산을 업로드하고 각 자산의 처리 시간 및 다양한 시스템 수준 지표를 측정하여 수행됩니다.
프로그램 설정 중에 자산 관련 KPI가 지정됩니다.

   * 95 번째 백분위수 처리 시간
   * 분당 업로드된 자산 수
   ![](assets/Setup_Program-KPIs.png)

1. **프로비저닝**아래에서 프로그램의 프로덕션 및 비프로덕션 환경에 대한 프로비저닝 구성을 보거나 편집할 수 있습니다. 프로그램에 대해 자동 크기 조정을 설정한 경우 **자동 크기 조절이 켜짐을**볼 수 있습니다.

   >[!NOTE]
   >
   >* 자동 크기 조절 기능은 프로덕션 환경에만 해당되며 일부 고객 프로그램에서는 사용할 수 없습니다.
   >* On-Demand Scaling는 이 릴리스에서 사용할 수 [!UICONTROL Cloud Manager]없습니다.


   ![](assets/Setup_Program-Provisioning.png)

1. **저장을** 클릭하여 설정 마법사를 완료합니다.

   >[!NOTE]
   >
   >초기 프로그램이 이미 설정된 후에는 언제든지 프로그램을 편집할 수 있습니다. 자세한 내용은 아래 단계를 따르십시오.

## 프로그램 편집

1. **클라우드 관리자** 홈 화면에서 솔루션으로 이동합니다.

   ![](assets/SetUpProgram5.png)

1. 아래 그림과 같이 솔루션을 선택하고 **편집을** 클릭하여 프로그램을 업데이트하거나 수정합니다.

   ![](assets/SetUpProgram6.png)

1. 프로그램을 업데이트하거나 수정할 수 있는 프로그램 **편집** 화면이 표시됩니다.

   ![](assets/Editing_Program-screen3.png)

## 다음 단계 {#the-next-steps}

**이미 파이프라인을**설정한 경우 다음 실행 시 업데이트된 설정이 고려됩니다. 아직 파이프라인을 설정하지 않은 경우 단계에 따라 파이프라인을 먼저 설정하십시오.

파이프라인을 [설정하려면 CI/CD 파이프라인](https://helpx.adobe.com/experience-manager/cloud-manager/using/configuring-pipeline.html) 구성을 참조하십시오.
