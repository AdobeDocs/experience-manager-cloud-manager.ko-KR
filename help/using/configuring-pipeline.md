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
source-git-commit: e748383fb627ac6ecf69f1b6e313bb5710fbf444
workflow-type: tm+mt
source-wordcount: '1379'
ht-degree: 0%

---

# CI/CD 파이프라인 구성 {#configure-your-ci-cd-pipeline}

>[!NOTE]
>AEM as a Cloud Service에서 Cloud Manager에 대한 CI/CD 파이프라인을 구성하는 방법에 대해 알아보려면 [여기](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/configure-pipeline.html?lang=en#using-cloud-manager)를 참조하십시오.

다음 페이지에서는 **파이프라인**&#x200B;을 구성하는 방법을 설명합니다. 파이프라인의 작동 방식에 대한 자세한 개념 정보를 검토하려면 [CI/CD 파이프라인 개요](ci-cd-pipeline.md)를 참조하십시오.

## 비디오 자습서 {#video-tutorial-one}

### Cloud Manager에서 파이프라인 구성 {#config-pipeline-video}

CI/CD 프로덕션 파이프라인 구성은 파이프라인을 시작하는 트리거, 프로덕션 배포를 제어하는 매개 변수 및 성능 테스트 매개 변수를 정의합니다.

>[!VIDEO](https://video.tv.adobe.com/v/26314/)


## 흐름 이해 {#understanding-the-flow}

[!UICONTROL Cloud Manager] UI의 **파이프라인 설정** 타일에서 파이프라인을 구성할 수 있습니다.

배포 관리자는 파이프라인 설정을 담당합니다. 이 경우 먼저 **Git 리포지토리**&#x200B;에서 분기를 선택합니다. 파이프라인 구성은 다음으로 구성됩니다.

* 파이프라인을 시작할 트리거를 정의합니다.
* 프로덕션 배포를 제어하는 매개 변수 정의
* 성능 테스트 매개 변수 구성

## 파이프라인 설정 {#setting-up-the-pipeline}

>[!CAUTION]
>
>Git 리포지토리에 하나 이상의 분기가 있고 [프로그램 설정](setting-up-program.md)이 완료될 때까지 파이프라인을 설정할 수 없습니다.

코드를 배포하기 전에 [!UICONTROL Cloud Manager]에서 파이프라인 설정을 구성해야 합니다.

>[!NOTE]
>
>초기 설정 후 파이프라인 설정을 변경할 수 있습니다.

### [!UICONTROL Cloud Manager]에서 파이프라인 설정 구성 {#configuring-the-pipeline-settings-from-cloud-manager}

[!UICONTROL Cloud Manager] UI를 사용하여 프로그램을 설정했으면 파이프라인을 설정할 준비가 된 것입니다.

다음 단계에 따라 파이프라인에 대한 동작 및 환경 설정을 구성합니다.

1. **파이프라인 설정** 을 클릭하여 파이프라인을 설정하고 구성합니다.

   ![](assets/Setup-Pipeline.png)

1. **파이프라인 설정** 화면이 표시됩니다.

   3단계 마법사를 사용하여 **Branch**, **환경** 및 **테스트** 환경을 설정할 수 있습니다.
Git 분기를 선택하고 **다음**&#x200B;을 클릭합니다.

   >[!NOTE]
   >
   >Git 리포지토리에 있는 분기는 프로그램에 연결됩니다.


1. **환경** 탭에 액세스하여 **스테이지** 및 **프로덕션** 옵션을 선택합니다.

   트리거를 정의하여 파이프라인을 시작할 수 있습니다.

   * **Git 변경**  시 - 구성된 Git 분기에 커밋이 추가될 때마다 CI/CD 파이프라인을 시작합니다. 이 옵션을 선택하더라도 항상 파이프라인을 수동으로 시작할 수 있습니다.
   * **수동**  - UI를 사용하여 파이프라인을 수동으로 시작합니다.

   파이프라인을 설정하거나 편집하는 동안 배포 관리자는 코드 품질, 보안 테스트 및 성능 테스트와 같은 품질 게이트에서 중요한 오류가 발생하는 경우 파이프라인의 동작을 정의할 수 있습니다.

   이 기능은 자동화된 프로세스를 원하는 고객에게 유용합니다. 사용 가능한 옵션은 다음과 같습니다.

* **매번**  묻기 - 기본 설정이며 중요한 오류에 대해 수동 개입이 필요합니다.
* **즉시 취소**  - 이 옵션을 선택하면 중요한 오류가 발생할 때마다 파이프라인이 취소됩니다. 이것은 기본적으로 사용자가 각 실패를 수동으로 거부하는 것을 에뮬레이션합니다.
* **즉시 승인**  - 이 옵션을 선택하면 중요한 오류가 발생할 때마다 파이프라인이 자동으로 진행됩니다. 이것은 기본적으로 사용자가 각 실패를 수동으로 승인하는 것입니다.

   이제 프로덕션 배포를 제어하는 매개 변수를 정의합니다. 사용 가능한 세 가지 옵션은 다음과 같습니다.

* **Go Live Approval 사용**  - 배포는  [!UICONTROL Cloud Manager] UI를 통해 비즈니스 소유자, 프로젝트 관리자 또는 배포 관리자가 수동으로 승인해야 합니다.
* **CSE 감독 사용**  - CSE는 실제로 배포를 시작하기 위해 참여합니다. CSE 감시가 활성화되면 파이프라인 설정 또는 편집 중에 배포 관리자에서 선택할 수 있는 옵션이 있습니다.

   * **모든 CSE**: 사용 가능한 모든 CSE를 참조합니다.
   * **내 CSE**: 는 CSE가 부재 중인 경우 고객 또는 해당 백업에 할당된 특정 CSE를 나타냅니다

* **예약됨**  - 이 옵션을 사용하면 예약된 프로덕션 배포를 활성화할 수 있습니다.

>[!NOTE]
>**Scheduled** 옵션이 선택된 경우, 단계 배포(및 **GoLive 승인 사용**)가 활성화된 경우 파이프라인 **에 프로덕션 배포를 예약하여 일정이 설정될 때까지 기다릴 수 있습니다.** 사용자는 프로덕션 배포를 즉시 실행하도록 선택할 수도 있습니다.
>
>배포 일정을 설정하거나 프로덕션 즉시 실행하려면 [**코드 배포**](deploying-code.md)&#x200B;를 참조하십시오.

![](assets/configure-pipeline-new.png)

>[!NOTE]
>
>모든 고객은 **CSE 감독 사용** 옵션을 사용할 수 없습니다.

**단계 배포 후 승인**

프로덕션 파이프라인에서 구성할 수 있는 선택적 단계 **스테이지 배포 후 승인**이 있습니다.
이 기능은 **파이프라인 편집** 화면의 새 옵션에서 활성화됩니다.

![](assets/post_deployment1.png)

그러면 파이프라인 실행 중에 별도의 단계로 표시됩니다.

![](assets/post_deployment2.png)

>[!NOTE]
>
>**단계 배포 후** 승인 기능은 프로덕션 배포 전 승인과 유사하게 작동하지만 단계 배포 단계 바로 뒤에 발생합니다. 이는 모든 테스트가 완료된 후 수행되는 프로덕션 배포 전 승인 대비 수행되는 테스트 방식입니다.

**디스패처 무효화**

배포 관리자는 파이프라인을 설정하거나 편집하는 동안 게시 인스턴스를 위해 AEM Dispatcher 캐시에서 **무효화** 또는 **플러시된**&#x200B;의 컨텐츠 경로 집합을 구성할 수 있습니다.

스테이지 및 프로덕션 배포에 대해 별도의 경로 세트를 구성할 수 있습니다. 구성된 경우, 이러한 캐시 작업은 컨텐츠 패키지가 배포된 바로 후에 배포 파이프라인 단계의 일부로 수행됩니다. 이러한 설정은 표준 AEM Dispatcher 동작을 사용합니다. 무효화는 캐시 무효화를 수행합니다. 이는 컨텐츠가 작성자에서 게시로 활성화될 때와 유사합니다. 플러시는 캐시 삭제를 수행합니다.

일반적으로 무효화 작업을 사용하는 것이 좋지만, 특히 AEM HTML 클라이언트 라이브러리를 사용할 때 플러시가 필요한 경우가 있을 수 있습니다.

>[!NOTE]
>
>Dispatcher 캐싱에 대한 자세한 내용은 [Dispatcher 개요](dispatcher-configurations.md) 를 참조하십시오.

아래 절차에 따라 Dispatcher 무효화를 구성하십시오.

1. Dispatcher 구성 제목 아래에 있는 **구성**&#x200B;을 클릭합니다

   ![](assets/image2018-8-7_14-53-24.png)

1. 경로를 입력하고 **유형**&#x200B;에서 작업을 선택한 다음 **추가**&#x200B;를 클릭합니다. 환경당 최대 100개의 경로를 지정할 수 있습니다. 경로를 추가한 후 **적용**&#x200B;을 클릭합니다.

   ![](assets/image2018-8-7_14-58-11.png)

1. **파이프라인 설정** 페이지를 다시 방문하면 선택 사항에 대한 업데이트된 요약이 표시됩니다.

   **저장**&#x200B;을 클릭하여 이 구성을 유지합니다.

   ![](assets/image2018-8-7_15-4-30.png)

1. **테스트** 탭에 액세스하여 프로그램에 대한 테스트 기준을 정의합니다. 이제 성능 테스트 매개 변수를 구성할 수 있습니다.

   라이선스를 구입한 제품에 따라 *AEM Sites* 및 *AEM Assets* 성능 테스트를 구성할 수 있습니다. 자세한 내용은 [성능 테스트](understand-your-test-results.md#performance-testing)를 참조하십시오.

1. **저장**&#x200B;을 클릭하여 파이프라인 프로세스 설정을 완료합니다.

   >[!NOTE]
   >또한 파이프라인을 설정한 후에는 [!UICONTROL Cloud Manager] UI의 **프로덕션 파이프라인 설정** 타일을 사용하여 동일한 것에 대한 설정을 계속 편집할 수 있습니다.

   ![](assets/Production-Pipeline.png)


## 비프로덕션 및 코드 품질 전용 파이프라인

스테이징 및 프로덕션에 배포되는 기본 파이프라인 외에도 고객은 **비프로덕션 파이프라인**&#x200B;이라고 하는 추가 파이프라인을 설정할 수 있습니다. 이러한 파이프라인은 항상 빌드 및 코드 품질 단계를 실행합니다. Adobe Managed Services 환경에 선택적으로 배포할 수도 있습니다.

## 비디오 자습서 {#video-tutorial-two}

### Cloud Manager 비프로덕션 및 코드 품질 전용 파이프라인 {#non-prod-video}

CI/CD 비프로덕션 파이프라인은 코드 품질 파이프라인 및 배포 파이프라인의 두 가지 카테고리로 분류됩니다. 코드 품질 파이프라인은 Git 분기에서 모든 코드를 작성하여 Cloud Manager의 코드 품질 검사에 대해 평가됩니다.

>[!VIDEO](https://video.tv.adobe.com/v/26316/)

### 비프로덕션 파이프라인 추가 {#add-non-production-pipeline}

홈 화면에서는 이러한 파이프라인이 새 카드에 나열됩니다.

1. Cloud Manager 홈 화면에서 **파이프라인** 카드에 액세스합니다. **+추가**&#x200B;를 클릭하고 **비프로덕션 파이프라인 추가**&#x200B;를 선택합니다.

   ![](/help/using/assets/configure-pipelines/nonprod-pipeline-add1.png)

1. **비프로덕션 파이프라인 추가**  대화 상자가 표시됩니다. 만들려는 파이프라인 유형을 **코드 품질 파이프라인** 또는 **배포 파이프라인** 선택합니다.

   또한 **배포 옵션**&#x200B;에서 **배포 트리거** 및 **중요 실패 동작**&#x200B;을 설정할 수도 있습니다. **계속**&#x200B;을 클릭합니다.

   ![](/help/using/assets/configure-pipelines/nonprod-pipeline-add2.png)


1. 이제 새로 생성된 비프로덕션 파이프라인이 **파이프라인** 카드에 표시됩니다.

   ![](/help/using/assets/configure-pipelines/nonprod-pipeline-add4.png)


   파이프라인은 아래와 같이 세 가지 작업이 있는 홈 화면의 카드에 표시됩니다.

   * **추가**  - 새 파이프라인을 추가할 수 있습니다.
   * **리포지토리 정보에 액세스**  - 사용자가 Cloud Manager Git 리포지토리에 액세스하는 데 필요한 정보를 얻을 수 있습니다.
   * **자세히 알아보기**  - CI/CD 파이프라인 설명서 리소스를 이해합니다.

### 비프로덕션 파이프라인 편집 {#editing-nonprod-pipeline}

**프로그램 개요** 페이지의 **파이프라인 카드**&#x200B;에서 파이프라인 구성을 편집할 수 있습니다.

구성된 비프로덕션 파이프라인을 편집하려면 아래 절차를 따르십시오.

1. **프로그램 개요** 페이지에서 **파이프라인** 카드로 이동합니다.

1. 비프로덕션 파이프라인을 선택하고 **... 을 클릭합니다.**. 아래 그림과 같이 **편집**&#x200B;을 클릭합니다.

   ![](/help/using/assets/configure-pipelines/non-prod-pipeline-edit1.png)

1. **프로덕션 파이프라인 편집** 대화 상자가 표시되면 **파이프라인 이름**, **저장소**, **Git 분기**, **배포 트리거** 및 **중요한 지표 실패 동작**&#x200B;을 업데이트할 수 있습니다.

   ![](/help/using/assets/configure-pipelines/non-prod-pipeline-edit2.png)

   >[!NOTE]
   >Cloud Manager에서 저장소를 추가 및 관리하는 방법에 대해 알아보려면 [저장소 추가 및 관리](/help/implementing/cloud-manager/managing-code/cloud-manager-repositories.md)를 참조하십시오.


1. 비프로덕션 파이프라인의 편집을 완료했으면 **업데이트**&#x200B;를 클릭합니다.


## 다음 단계 {#the-next-steps}

파이프라인을 구성한 후에는 코드를 배포해야 합니다.

자세한 내용은 [코드 배포](deploying-code.md)를 참조하십시오.
