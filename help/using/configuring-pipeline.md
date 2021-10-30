---
title: CI/CD 파이프라인 구성
seo-title: Configure your CI/CD Pipeline
description: 이 페이지를 따라 Cloud Manager에서 파이프라인 설정을 구성합니다.
seo-description: Before you start to deploy your code, you must configure your pipeline settings from the AEM Cloud Manager.
uuid: 35fd56ac-dc9c-4aca-8ad6-36c29c4ec497
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: using
content-type: reference
discoiquuid: ba6c763a-b78a-439e-8c40-367203a719b3
feature: CI-CD Pipeline
exl-id: d489fa3c-df1e-480b-82d0-ac8cce78a710
source-git-commit: 2be8f290b58fff2991f876c37dd1b499bc6c5352
workflow-type: tm+mt
source-wordcount: '1834'
ht-degree: 0%

---

# CI/CD 파이프라인 구성 {#configure-your-ci-cd-pipeline}

>[!NOTE]
>AEM as a Cloud Service에서 Cloud Manager용 CI/CD 파이프라인을 구성하는 방법에 대해 알아보려면 다음을 참조하십시오 [여기](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/configure-pipeline.html?lang=en#using-cloud-manager).

다음 페이지에서는 을 구성하는 방법을 설명합니다 **파이프라인**. 파이프라인의 작동 방식에 대한 자세한 개념 정보를 검토하려면 [CI/CD 파이프라인 개요](ci-cd-pipeline.md).


## 흐름 이해 {#understanding-the-flow}

에서 파이프라인을 구성할 수 있습니다 **파이프라인 설정** 의 타일 [!UICONTROL Cloud Manager] UI.

배포 관리자는 파이프라인 설정을 담당합니다. 이 경우 먼저 **Git 리포지토리**. 파이프라인 구성은 다음으로 구성됩니다.

* 파이프라인을 시작할 트리거를 정의합니다.
* 프로덕션 배포를 제어하는 매개 변수 정의
* 성능 테스트 매개 변수 구성

## 비디오 자습서 {#video-tutorial-one}

### Cloud Manager에서 파이프라인 구성 {#config-pipeline-video}

CI/CD 프로덕션 파이프라인 구성은 파이프라인을 시작하는 트리거, 프로덕션 배포를 제어하는 매개 변수 및 성능 테스트 매개 변수를 정의합니다.

>[!VIDEO](https://video.tv.adobe.com/v/26314/)

## 파이프라인 설정 {#setting-up-the-pipeline}

>[!CAUTION]
>
>Git 리포지토리에 하나 이상의 분기와 가 있어야 파이프라인을 설정할 수 있습니다 [프로그램 설정](setting-up-program.md) 가 완료되었습니다.

코드를 배포하기 전에 [!UICONTROL Cloud Manager].

>[!NOTE]
>
>초기 설정 후 파이프라인 설정을 변경할 수 있습니다.

### 파이프라인 카드에서 새 프로덕션 파이프라인 추가 {#adding-production-pipeline}

프로그램을 설정하고 [!UICONTROL Cloud Manager] UI 프로덕션 파이프라인을 추가할 준비가 되었습니다.

다음 단계에 따라 프로덕션 파이프라인에 대한 동작 및 환경 설정을 구성합니다.

1. 로 이동합니다 **파이프라인** 카드로부터 **프로그램 개요** 페이지.

1. 클릭 **+추가** 을(를) 선택합니다. **프로덕션 파이프라인 추가**.

   ![](/help/using/assets/configure-pipelines/add-prod1.png)

1. **프로덕션 파이프라인 추가** 대화 상자가 표시됩니다.

   1. 을(를) 입력합니다. **파이프라인 이름**. 을(를) 선택할 수 있습니다 **저장소** 그리고 **Git 분기**.

      ![](/help/using/assets/configure-pipelines/add-prod2.png)

   1. 다음을 설정할 수 있습니다 **배포 트리거** 및 **중요한 지표 실패 동작** 변환 전: **배포 옵션**.

      ![](/help/using/assets/configure-pipelines/add-prod3.png)


      다음 배포 트리거를 할당하여 파이프라인을 시작할 수 있습니다.

      * **수동** - UI를 사용하여 파이프라인을 수동으로 시작합니다.
      * **Git 변경 시** - 구성된 git 분기에 커밋이 추가될 때마다 CI/CD 파이프라인을 시작합니다. 이 옵션을 선택하더라도 항상 파이프라인을 수동으로 시작할 수 있습니다.

      파이프라인 설정 또는 편집 중에 품질 게이트에서 중요한 오류가 발생하는 경우 배포 관리자에서 파이프라인의 동작을 정의할 수 있습니다.

      이 기능은 자동화된 프로세스를 원하는 고객에게 유용합니다. 사용 가능한 옵션은 다음과 같습니다.

      * **매번 질문하기** - 기본 설정이며 중요 오류에 대해 수동으로 개입해야 합니다.
      * **즉시 실패** - 이 옵션을 선택하면 중요한 오류가 발생할 때마다 파이프라인이 취소됩니다. 이것은 기본적으로 사용자가 각 실패를 수동으로 거부하는 것을 에뮬레이션합니다.
      * **즉시 계속** - 이 옵션을 선택하면 중요한 오류가 발생할 때마다 파이프라인이 자동으로 진행됩니다. 이것은 기본적으로 사용자가 각 실패를 수동으로 승인하는 것입니다.
   1. 을(를) 선택합니다 **배포 옵션**.

      ![](/help/using/assets/configure-pipelines/add-prod4.png)

      * **단계 배포 후 승인** 함수는 프로덕션 배포 전 승인과 유사하지만 테스트가 수행되기 전, 즉 모든 테스트가 완료된 후 수행되는 프로덕션 배포 전 승인 대비, 단계 배포 단계 바로 직후에 발생합니다.

      * **로드 밸런서 변경 건너뛰기** 변경 사항을 건너뜁니다.
   1. 을(를) 선택합니다 **Dispatcher 구성** 준비 중입니다. 경로를 입력하고 작업을 선택합니다. **유형**&#x200B;를 클릭하고 **경로 추가**. 환경당 최대 100개의 경로를 지정할 수 있습니다.

      ![](/help/using/assets/configure-pipelines/dispatcher-stage.png)

   1. 을(를) 선택합니다 **배포 옵션** 제작 관련 이제 프로덕션 배포를 제어하는 매개 변수를 정의합니다.

      ![](/help/using/assets/configure-pipelines/prod-deploymentoptions.png)

      사용 가능한 세 가지 옵션은 다음과 같습니다.

      * **Go Live 승인 사용** - 배포를 수동으로 승인하려면 [!UICONTROL Cloud Manager] UI.

      * **예약됨** - 이 옵션을 사용하면 예약된 프로덕션 배포를 활성화할 수 있습니다.

         >[!NOTE]
         >If **예약됨** 옵션을 선택하면 파이프라인에 프로덕션 배포를 예약할 수 있습니다 **after** 단계 배포(및 **GoLive 승인 사용**&#x200B;가 활성화된 경우) 을(를) 사용하여 스케줄을 설정할 때까지 기다립니다. 사용자는 프로덕션 배포를 즉시 실행하도록 선택할 수도 있습니다.
         >
         >자세한 내용은 [코드 배포](deploying-code.md)을 눌러 배포 일정을 설정하거나 프로덕션을 즉시 실행합니다.

         * **CSE 감독 사용** - CSE가 실제로 배포를 시작하기 위해 를 사용합니다. CSE 감시가 활성화되면 파이프라인 설정 또는 편집 중에 배포 관리자에서 선택할 수 있는 옵션이 있습니다.

            * **모든 CSE**: 사용 가능한 모든 CSE를 참조합니다.
            * **내 CSE**: 는 CSE가 부재 중인 경우 고객 또는 해당 백업에 할당된 특정 CSE를 나타냅니다
   1. 설정 **Dispatcher 구성** 제작 관련 경로를 입력하고 작업을 선택합니다. **유형**&#x200B;를 클릭하고 **경로 추가**. 환경당 최대 100개의 경로를 지정할 수 있습니다.

      ![](/help/using/assets/configure-pipelines/dispatcher-prod.png)

      배포 관리자는 다음과 같은 컨텐츠 경로 세트를 구성할 수 있습니다 **무효화** 또는 **플러시됨** 파이프라인을 설정하거나 편집하는 동안 게시 인스턴스에 대한 AEM Dispatcher 캐시에서 배관.

      스테이지 및 프로덕션 배포에 대해 별도의 경로 세트를 구성할 수 있습니다. 구성된 경우, 이러한 캐시 작업은 컨텐츠 패키지가 배포된 바로 후에 배포 파이프라인 단계의 일부로 수행됩니다. 이러한 설정은 표준 AEM Dispatcher 동작을 사용합니다. 무효화는 캐시 무효화를 수행합니다. 이는 컨텐츠가 작성자에서 게시로 활성화될 때와 유사합니다. 플러시는 캐시 삭제를 수행합니다.

      일반적으로 무효화 작업을 사용하는 것이 좋지만, 특히 AEM HTML 클라이언트 라이브러리를 사용할 때 플러시가 필요한 경우가 있을 수 있습니다.

      >[!NOTE]
      >
      >자세한 내용은 [Dispatcher 개요](dispatcher-configurations.md) dispatcher 캐싱에 대한 자세한 내용을 확인하십시오.





1. 클릭 **계속** 모든 옵션을 선택하면

1. 에서 옵션을 선택합니다 **단계 테스트** 단계. 다음을 구성할 수 있습니다 *AEM Sites* 및 *AEM Assets* 성능 테스트(라이선스를 구입한 제품에 따라 다름) 을(를) 참조하십시오. [성능 테스트](understand-your-test-results.md#performance-testing) 자세한 내용

   1. 선택 사항 선택 **사이트 컨텐츠 전달/분산 로드 가중치**. 자세한 내용은 [성능 테스트의 AEM Sites](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/how-to-use/understand-your-test-results.html?lang=en#aem-sites) 자세한 내용

      ![](/help/using/assets/configure-pipelines/add-prod5.png)

   1. 선택 사항 선택 **Assets 성능 테스트 배포**. 자세한 내용은 [성능 테스트의 AEM Assets](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/how-to-use/understand-your-test-results.html?lang=en#aem-assets) 자세한 내용

      ![](/help/using/assets/configure-pipelines/add-prod6.png)

1. 클릭 **저장** 를 클릭하여 프로덕션 파이프라인 추가를 완료합니다.

### 프로덕션 파이프라인 편집 {#editing-prod-pipeline}

에서 파이프라인 구성을 편집할 수 있습니다 **프로그램 개요** 페이지.

구성된 파이프라인을 편집하려면 아래 절차를 따르십시오.

1. 다음으로 이동 **파이프라인** 카드로부터 **프로그램 개요** 페이지.

1. 클릭 **...** 에서 **파이프라인** 카드를 클릭하고 **편집**&#x200B;아래 그림과 같이,

   ![](/help/using/assets/configure-pipelines/edit-prod1.png)

1. 다음 **프로덕션 파이프라인 편집** 대화 상자가 표시됩니다.

   1. 다음 **구성** 탭에서 다음을 업데이트할 수 있습니다 **파이프라인 이름**, **저장소**, **Git 분기**, **배포 트리거**, **중요한 지표 실패 동작**, **배포 옵션** 및 **Dispatcher 구성**.

      >[!NOTE]
      >자세한 내용은 [저장소 추가 및 관리](/help/using/cloud-manager-repositories.md) cloud Manager에서 저장소를 추가하고 관리하는 방법을 알아봅니다.


   1. 다음 **단계 테스트** 탭에서 옵션을 다시 선택하는 옵션이 제공됩니다 **사이트 컨텐츠 전달/분산 로드 가중치** 및 **Assets 성능 테스트 배포**.

1. 클릭 **업데이트** 파이프라인 편집을 완료하면 됩니다.

### 추가 프로덕션 파이프라인 작업 {#additional-prod-actions}

#### 프로덕션 파이프라인 실행 {#run-prod}

파이프라인 카드에서 프로덕션 파이프라인을 실행할 수 있습니다.

1. 다음으로 이동 **파이프라인** 카드로부터 **프로그램 개요** 페이지.

1. 클릭 **...** 에서 **파이프라인** 카드를 클릭하고 **실행**&#x200B;아래 그림과 같이,

   ![](/help/using/assets/configure-pipelines/prod-run.png)

#### 프로덕션 파이프라인 삭제 {#delete-prod}

파이프라인 카드에서 프로덕션 파이프라인을 삭제할 수 있습니다.

1. 다음으로 이동 **파이프라인** 카드로부터 **프로그램 개요** 페이지.

1. 클릭 **...** 에서 **파이프라인** 카드를 클릭하고 **삭제**&#x200B;아래 그림과 같이,

   ![](/help/using/assets/configure-pipelines/prod-delete.png)

   >[!NOTE]
   >이제 배포 관리자 역할의 사용자는 를 통해 셀프 서비스 방식으로 프로덕션 파이프라인을 삭제할 수 있습니다 **삭제** 옵션 을 클릭합니다.

## 비프로덕션 및 코드 품질 전용 파이프라인

단계 및 프로덕션에 배포되는 기본 파이프라인 외에도 고객은 라고 하는 추가 파이프라인을 설정할 수 있습니다 **비프로덕션 파이프라인**. 이러한 파이프라인은 항상 빌드 및 코드 품질 단계를 실행합니다. Adobe Managed Services 환경에 선택적으로 배포할 수도 있습니다.

## 비디오 자습서 {#video-tutorial-two}

### Cloud Manager 비프로덕션 및 코드 품질 전용 파이프라인 {#non-prod-video}

CI/CD 비프로덕션 파이프라인은 코드 품질 파이프라인 및 배포 파이프라인의 두 가지 카테고리로 분류됩니다. 코드 품질 파이프라인은 Git 분기에서 모든 코드를 작성하여 Cloud Manager의 코드 품질 검사에 대해 평가됩니다.

>[!VIDEO](https://video.tv.adobe.com/v/26316/)

### 비프로덕션 파이프라인 추가 {#add-non-production-pipeline}

홈 화면에서는 이러한 파이프라인이 새 카드에 나열됩니다.

1. 액세스 권한 **파이프라인** Cloud Manager 홈 화면에서 카드를 생성할 수 있습니다. 클릭 **+추가** 을(를) 선택합니다. **비프로덕션 파이프라인 추가**.

   ![](/help/using/assets/configure-pipelines/nonprod-pipeline-add1.png)

1. **비프로덕션 파이프라인 추가**  대화 상자가 표시됩니다. 생성할 파이프라인 유형을 선택합니다 **코드 품질 파이프라인** 또는 **배포 파이프라인**.

   또한 **배포 트리거** 및 **중요한 지표 실패 동작** 변환 전: **배포 옵션**. 클릭 **계속**.

   ![](/help/using/assets/configure-pipelines/nonprod-pipeline-add2.png)


1. 이제 새로 생성된 비프로덕션 파이프라인이 **파이프라인** 카드.

   ![](/help/using/assets/configure-pipelines/nonprod-pipeline-add4.png)


   파이프라인은 아래와 같이 세 가지 작업이 있는 홈 화면의 카드에 표시됩니다.

   * **추가** - 새 파이프라인을 추가할 수 있습니다.
   * **보고서 정보에 액세스** - 사용자가 Cloud Manager Git 리포지토리에 액세스하는 데 필요한 정보를 얻을 수 있도록 해줍니다.
   * **추가 정보** - CI/CD 파이프라인 설명서 리소스를 이해하도록 이동합니다.

### 비프로덕션 파이프라인 편집 {#editing-nonprod-pipeline}

에서 파이프라인 구성을 편집할 수 있습니다 **파이프라인 카드** 변환 전: **프로그램 개요** 페이지.

구성된 비프로덕션 파이프라인을 편집하려면 아래 절차를 따르십시오.

1. 다음으로 이동 **파이프라인** 카드로부터 **프로그램 개요** 페이지.

1. 비프로덕션 파이프라인을 선택하고 을(를) 클릭합니다 **...**. 클릭 **편집**&#x200B;아래 그림과 같이,

   ![](/help/using/assets/configure-pipelines/non-prod-pipeline-edit1.png)

1. 다음 **프로덕션 파이프라인 편집** 업데이트할 수 있는 대화 상자가 표시됩니다 **파이프라인 이름**, **저장소**, **Git 분기**, **배포 트리거**, 및 **중요한 지표 실패 동작**.

   ![](/help/using/assets/configure-pipelines/non-prod-pipeline-edit2.png)

   >[!NOTE]
   >자세한 내용은 [저장소 추가 및 관리](/help/using/cloud-manager-repositories.md) cloud Manager에서 저장소를 추가하고 관리하는 방법을 알아봅니다.

   다음 배포 트리거를 할당하여 파이프라인을 시작할 수 있습니다.

   * **수동** - UI를 사용하여 파이프라인을 수동으로 시작합니다.
   * **Git 변경 시** - 구성된 git 분기에 커밋이 추가될 때마다 CI/CD 파이프라인을 시작합니다. 이 옵션을 선택하더라도 항상 파이프라인을 수동으로 시작할 수 있습니다.

   파이프라인 설정 또는 편집 중에 품질 게이트에서 중요한 오류가 발생하는 경우 배포 관리자에서 파이프라인의 동작을 정의할 수 있습니다. 이 기능은 자동화된 프로세스를 원하는 고객에게 유용합니다. 사용 가능한 옵션은 다음과 같습니다.

   * **매번 질문하기** - 기본 설정이며 중요 오류에 대해 수동으로 개입해야 합니다.
   * **즉시 실패** - 이 옵션을 선택하면 중요한 오류가 발생할 때마다 파이프라인이 취소됩니다. 이것은 기본적으로 사용자가 각 실패를 수동으로 거부하는 것을 에뮬레이션합니다.
   * **즉시 계속** - 이 옵션을 선택하면 중요한 오류가 발생할 때마다 파이프라인이 자동으로 진행됩니다. 이것은 기본적으로 사용자가 각 실패를 수동으로 승인하는 것입니다.


1. 클릭 **업데이트** 비프로덕션 파이프라인의 편집을 완료하면 됩니다.

### 추가 비프로덕션 파이프라인 작업 {#additional-nonprod-actions}

#### 비프로덕션 파이프라인 실행 {#run-nonprod}

파이프라인 카드에서 프로덕션 파이프라인을 실행할 수 있습니다.

1. 다음으로 이동 **파이프라인** 카드로부터 **프로그램 개요** 페이지.

1. 클릭 **...** 에서 **파이프라인** 카드를 클릭하고 **실행**&#x200B;아래 그림과 같이,

   ![](/help/using/assets/configure-pipelines/nonprod-run1.png)

#### 비프로덕션 파이프라인 삭제 {#delete-nonprod}

파이프라인 카드에서 프로덕션 파이프라인을 삭제할 수 있습니다.

1. 다음으로 이동 **파이프라인** 카드로부터 **프로그램 개요** 페이지.

1. 클릭 **...** 에서 **파이프라인** 카드를 클릭하고 **삭제**&#x200B;아래 그림과 같이,

   ![](/help/using/assets/configure-pipelines/nonprod-delete.png)


## 다음 단계 {#the-next-steps}

파이프라인을 구성한 후에는 코드를 배포해야 합니다.

자세한 내용은 [코드 배포](deploying-code.md) 자세한 내용
