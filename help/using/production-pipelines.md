---
title: 프로덕션 파이프라인 구성
description: Cloud Manager를 사용하여 코드를 배포할 프로덕션 파이프라인을 만들고 구성하는 방법을 알아봅니다.
exl-id: d489fa3c-df1e-480b-82d0-ac8cce78a710
source-git-commit: 99325c28c379103db2ba4c19bb6d206849c6e126
workflow-type: tm+mt
source-wordcount: '1296'
ht-degree: 0%

---


# 프로덕션 파이프라인 구성 {#configuring-production-pipelines}

Cloud Manager를 사용하여 코드를 배포할 프로덕션 파이프라인을 만들고 구성하는 방법을 알아봅니다. 먼저 Cloud Manager에서 파이프라인이 작동하는 방식에 대한 개념적 개요를 보려면 문서를 참조하십시오 [CI/CD 파이프라인.](/help/overview/ci-cd-pipelines.md)

## 개요 {#overview}

사용 **파이프라인 설정** 타일 [!UICONTROL Cloud Manager] 두 가지 서로 다른 유형의 파이프라인을 생성할 수 있습니다.

* **프로덕션 파이프라인** - 프로덕션 파이프라인은 Git 리포지토리의 소스 코드를 프로덕션으로 가져오기 위해 일련의 오케스트레이션된 단계로 구성된 목적으로 만들어진 파이프라인입니다.
* **비프로덕션 파이프라인** - 비프로덕션 파이프라인은 주로 코드 품질 검사를 실행하거나 소스 코드를 개발 환경에 배포하는 역할을 합니다.

이 문서는 프로덕션 파이프라인에 중점을 둡니다. 비프로덕션 파이프라인을 구성하는 방법에 대한 자세한 내용은 문서를 참조하십시오 [비프로덕션 파이프라인 구성.](/help/using/non-production-pipelines.md)

다음 **배포 관리자** 역할은 파이프라인을 설정할 책임이 있습니다. 파이프라인 구성은 다음으로 구성됩니다.

1. 파이프라인을 시작할 트리거를 정의합니다.
1. 프로덕션 배포를 제어하는 매개 변수 정의
1. 성능 테스트 매개 변수 구성

>[!NOTE]
>
>연관된 Git 리포지토리에 하나 이상의 분기와 [프로그램 설정](/help/getting-started/program-setup.md) 가 완료되었습니다.

## 비디오 자습서 {#video-tutorial-one}

이 비디오에서는 이 문서에 자세히 설명된 파이프라인 생성 프로세스에 대한 개요를 제공합니다.

>[!VIDEO](https://video.tv.adobe.com/v/26314/)

## 새 프로덕션 파이프라인 추가 {#adding-production-pipeline}

를 사용한 후 [!UICONTROL Cloud Manager] UI를 통해 프로그램을 설정하고 하나 이상의 환경을 구축할 수 있으므로 프로덕션 파이프라인을 추가할 수 있습니다.

1. Cloud Manager에 로그인 위치 [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) 적절한 조직과 프로그램을 선택합니다.

1. 로 이동합니다 **파이프라인** 카드로부터 **프로그램 개요** 페이지를 클릭하고 **+추가** 을(를) 선택합니다. **프로덕션 파이프라인 추가**.

   ![프로덕션 파이프라인 추가](/help/assets/configure-pipelines/add-prod1.png)

1. 다음 **프로덕션 파이프라인 추가** 대화 상자가 열립니다 **구성** 탭의 탭에서는 파이프라인에 대한 여러 옵션을 정의해야 합니다. 이러한 옵션은 축소 가능한 섹션으로 그룹화되어 다음 단계에 설명되어 있습니다.

   1. 에서 파이프라인의 수사적 이름을 입력합니다 **파이프라인 이름** 필드.

   1. 아래에 **소스 코드** 섹션에서 파이프라인이 처리할 코드를 검색할 위치를 정의합니다.

      * **저장소** - 이 옵션은 파이프라인에서 코드를 검색해야 하는 Git 리포지토리를 정의합니다.
      >[!TIP]
      >
      >문서를 참조하십시오 [프로그램 설정](/help/getting-started/program-setup.md) cloud Manager에서 저장소를 추가하고 관리하는 방법을 알아봅니다.

      * **Git 분기** - 이 옵션은 선택한 파이프라인의 어느 분기에서 코드를 검색해야 하는지를 정의합니다.
      * **코드 위치** - 이 옵션은 파이프라인이 코드를 검색해야 하는 선택한 리포지토리의 분기에서 경로를 정의합니다.

      ![파이프라인에 대한 보고서 정의](/help/assets/configure-pipelines/add-prod2.png)

   1. 아래에 **환경** 섹션에서 배포를 트리거하는 대상과 각 환경별로 롤아웃해야 하는 방법을 정의합니다.

      1. 에서 **단계** 섹션에서 파이프라인이 스테이징 환경에 롤아웃되는 방식을 정의할 수 있습니다.

         * **배포 트리거** - 파이프라인을 시작할 배포 트리거를 정의하는 다음 옵션이 있습니다.

            * **수동** - 이 옵션을 사용하여 Cloud Manager UI를 사용하여 파이프라인을 수동으로 시작합니다.
            * **Git 변경 시** - 이 옵션은 구성된 git 분기에 커밋이 추가될 때마다 CI/CD 파이프라인을 시작합니다. 이 옵션을 사용하면 필요에 따라 파이프라인을 수동으로 시작할 수 있습니다.
         * **중요한 지표 실패 동작** - 파이프라인 설정 또는 편집 중에 품질 게이트에서 중요한 오류가 발생하는 경우 배포 관리자에서 파이프라인의 동작을 정의할 수 있습니다. 사용 가능한 옵션은 다음과 같습니다.

            * **매번 질문하기** - 기본 설정이며 중요한 오류에 대해 수동으로 개입해야 합니다.
            * **즉시 실패** - 이 옵션을 선택하면 중요한 오류가 발생할 때마다 파이프라인이 취소됩니다. 이것은 기본적으로 사용자가 각 실패를 수동으로 거부하는 것을 에뮬레이션합니다.
            * **즉시 계속** - 이 옵션을 선택하면 중요한 오류가 발생할 때마다 파이프라인이 자동으로 진행됩니다. 이것은 기본적으로 사용자가 각 실패를 수동으로 승인하는 것입니다.

         ![배포 트리거](/help/assets/configure-pipelines/add-prod3.png)

         * **배포 옵션** - 특정 배포 작업을 가속화할 수 있습니다.

            * **단계 배포 후 승인** - 이 승인은 스테이징 환경에 배포한 후 테스트하기 전에 발생합니다. 그렇지 않으면 모든 테스트가 완료된 후 수행되는 프로덕션 배포 전에 승인이 발생합니다.

            * **로드 밸런서 변경 건너뛰기** - 로드 밸런서를 변경하지 않았습니다.

         ![스테이징 배포 옵션](/help/assets/configure-pipelines/add-prod4.png)

         * **Dispatcher 구성** - **배포 관리자** 역할은 파이프라인이 실행될 때 AEM Dispatcher 캐시에서 무효화되거나 플러시되는 컨텐츠 경로 집합을 구성할 수 있습니다. 이러한 캐시 작업은 컨텐츠 패키지가 배포된 직후에 배포 파이프라인 단계의 일부로 수행됩니다. 이러한 설정은 표준 AEM Dispatcher 동작을 사용합니다. 구성하려면:

            1. 아래 **경로** 컨텐츠 경로를 제공합니다.
            1. 아래 **유형**&#x200B;을 눌러 해당 경로에서 수행할 작업을 선택합니다.
            * **플러시** - 캐시 무효화를 수행합니다. 이 작업은 작성 인스턴스에서 게시 인스턴스로 컨텐츠가 활성화될 때와 유사합니다.
            * **무효화** - 캐시 삭제를 수행합니다.
            1. 클릭 **경로 추가** 지정된 경로를 추가하려면 환경당 최대 100개의 경로를 추가할 수 있습니다.

         ![Dispatcher 구성](/help/assets/configure-pipelines/dispatcher-stage.png)

         >[!TIP]
         >
         >일반적으로 무효화 작업을 사용하는 것이 좋지만, 특히 AEM HTML 클라이언트 라이브러리를 사용할 때 플러시가 필요한 경우가 있을 수 있습니다.

      1. 에서 **프로덕션** 섹션에서 파이프라인이 프로덕션 환경에 롤아웃되는 방법을 정의할 수 있습니다.

         * **배포 옵션** - 프로덕션 배포를 제어하는 매개 변수를 정의할 수 있습니다.

            * **Go Live 승인 사용** - 배포는 사용자가 수동으로 승인해야 **비즈니스 소유자**, **프로젝트 관리자**, 또는 **배포 관리자** 을 통한 역할 [!UICONTROL Cloud Manager] UI.
            * **예약됨** - 이 옵션은 프로덕션 배포 전에 파이프라인을 중지하여 예약할 수 있도록 합니다. 이 옵션을 선택하면 스테이징 환경에 배포하면 파이프라인이 중지되고 사용자에게 작업을 수행할 것인지 묻는 메시지가 표시됩니다.
               * **지금** - 이 옵션은 즉시 프로덕션에 배포되어 파이프라인을 효과적으로 완료할 수 있습니다.
               * **날짜** - 이 옵션을 사용하면 배포를 완료해야 하는 시간을 예약할 수 있습니다.
               * **실행 중지** - 이 옵션은 프로덕션에 대한 배포를 중단합니다.

            >[!TIP]
            >
            >문서를 참조하십시오 [코드 배포,](/help/using/code-deployment.md) 을 클릭하여 배포 일정을 설정하거나 파이프라인을 즉시 실행하는 방법을 알아봅니다.

            * **CSE 감독 사용** - 이 옵션을 선택하면 CSE가 실제로 배포를 시작하기 위해 참여합니다. 이 옵션이 활성화되면 파이프라인을 작성하거나 편집할 때 **배포 관리자** 역할에는 다음 옵션이 있습니다.

               * **모든 CSE** - 이 옵션을 사용하면 모든 사용 가능한 CSE에서 배포를 시작할 수 있습니다.
               * **내 CSE** - 이 옵션을 사용하면 고객에게 할당된 특정 CSE만 배포를 시작할 수 있습니다. 할당된 CSE를 사용할 수 없는 경우 지정된 CSE 백업에도 적용됩니다.

            ![프로덕션 배포 옵션](/help/assets/configure-pipelines/prod-deploymentoptions.png)

         * **Dispatcher 구성** - 프로덕션 환경에 대한 디스패처 구성을 정의합니다. 옵션은 스테이징 환경에 대한 옵션과 동일합니다.











1. 클릭 **계속** 앞으로 나아가다 **단계 테스트** 라이선스를 구입한 제품에 따라 AEM Sites 및 AEM Assets 성능 테스트를 구성할 수 있는 탭입니다.

   >[!TIP]
   >
   >문서를 참조하십시오 [코드 품질 테스트](/help/using/code-quality-testing.md#performance-testing) 에서 사용할 수 있는 옵션에 대한 자세한 내용은 **단계 테스트** 탭.

   1. 아래에 **사이트 컨텐츠 전달/분산 로드 가중치** 섹션에서는 사용 가능하게 하거나 비활성화할 수 있는 세 페이지 세트 간 페이지 요청의 가중치를 기반으로 사이트 성능 테스트가 구성되는 방식을 정의합니다.

      * **인기 있는 라이브 페이지**
      * **기타 라이브 페이지**
      * **새 페이지**

      ![사이트 로드 가중치](/help/assets/configure-pipelines/add-prod5.png)

   1. 아래에 **Assets 성능 테스트 배포** 섹션에서 이미지 및 PDF의 테스트 배포를 정의하고 테스트 자산을 정의합니다.

      * **이미지** - 슬라이더를 조정하여 이미지와 PDF 간에 테스트 분할을 조정합니다.
      * **PDF** - 슬라이더를 조정하여 이미지와 PDF 간에 테스트 분할을 조정합니다.

      * 업로드하여 자신만의 사용자 지정 자산을 정의합니다.

         1. **형식** - 사용자 지정 자산이 이미지 PDF인지 여부를 선택합니다.
         1. **파일 이름** - 파일 브라우저 단추를 사용하여 로컬 시스템에서 이미지를 선택합니다.
         1. **테스트 파일 추가** - 선택한 자산을 업로드하려면 을(를) 클릭합니다.

      ![Assets 테스트 배포](/help/assets/configure-pipelines/add-prod6.png)



1. 클릭 **저장** 를 클릭하여 프로덕션 파이프라인 추가를 완료합니다.

## 다음 단계 {#the-next-steps}

파이프라인을 구성한 후에는 코드를 배포해야 합니다. 문서 보기 [코드 배포](/help/using/code-deployment.md) 자세한 내용
