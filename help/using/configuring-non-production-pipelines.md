---
title: 비프로덕션 파이프라인 구성
description: 코드를 배포하기 위해 Cloud Manager를 사용하여 비프로덕션 파이프라인을 만들고 구성하는 방법을 알아봅니다.
source-git-commit: 205113735cc743e11e140b1161413002844f5b79
workflow-type: tm+mt
source-wordcount: '624'
ht-degree: 0%

---


# 비프로덕션 파이프라인 구성 {#configuring-non-production-pipelines}

코드를 배포하기 위해 Cloud Manager를 사용하여 비프로덕션 파이프라인을 만들고 구성하는 방법을 알아봅니다. 먼저 Cloud Manager에서 파이프라인이 작동하는 방식에 대한 개념적 개요를 보려면 [CI/CD 파이프라인 개요 설명서.](ci-cd-pipeline.md)

>[!NOTE]
>
>AEM as a Cloud Service에서 Cloud Manager의 CI/CD 파이프라인을 구성하는 방법에 대해 알아보려면 다음을 참조하십시오 [aemAaCS 설명서 .](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/configure-pipeline.html#using-cloud-manager)

## 개요 {#understanding-the-flow}

다음 **배포 관리자** 역할은 를 사용하여 파이프라인을 설정할 책임이 있습니다 **파이프라인** 의 타일 [!UICONTROL Cloud Manager] UI.

두 가지 유형의 파이프라인을 생성할 수 있습니다.

* **프로덕션 파이프라인** - 프로덕션 파이프라인은 소스 코드를 프로덕션에 완전히 투입하기 위해 일련의 오케스트레이션된 단계로 구성된 목적으로 만들어진 파이프라인입니다.
* **비프로덕션 파이프라인** - 비프로덕션 파이프라인은 주로 코드 품질 검사를 실행하거나 소스 코드를 개발 환경에 배포하는 역할을 합니다.

이 문서는 비프로덕션 파이프라인에 중점을 둡니다. 비프로덕션 파이프라인을 구성하는 방법에 대한 자세한 내용은 문서를 참조하십시오 [비프로덕션 파이프라인 구성.](configuring-non-production-pipelines.md)

다음과 같은 두 가지 유형의 비프로덕션 파이프라인이 있습니다.

* **코드 품질 파이프라인** - 이러한 실행 코드 품질은 Git 분기의 코드에서 검색하고 빌드 및 코드 품질 단계를 실행합니다.
* **배포 파이프라인** - 코드 품질 파이프라인과 같은 빌드 및 코드 품질 단계를 실행하는 것 외에도 코드를 비프로덕션 환경에 배포합니다.

>[!NOTE]
>
>연관된 Git 리포지토리에 하나 이상의 분기와 [프로그램 설정](setting-up-program.md) 가 완료되었습니다. 자세한 내용은 [저장소 추가 및 관리](cloud-manager-repositories.md) cloud Manager에서 저장소를 추가하고 관리하는 방법을 알아봅니다.

## 비디오 자습서 {#video-tutorial-two}

>[!VIDEO](https://video.tv.adobe.com/v/26316/)

## 비프로덕션 파이프라인 추가 {#add-non-production-pipeline}

프로그램을 설정하고 Cloud Manager UI를 사용하여 하나 이상의 환경을 만들면 다음 단계를 수행하여 비프로덕션 파이프라인을 추가할 수 있습니다.

1. Cloud Manager에 로그인 위치 [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com) 적절한 조직과 프로그램을 선택합니다.

1. Cloud Manager 홈 화면에서 파이프라인 카드에 액세스합니다. 클릭 **추가** 을(를) 선택합니다. **비프로덕션 파이프라인 추가**.

   ![비프로덕션 파이프라인 추가](/help/using/assets/configure-pipelines/nonprod-pipeline-add1.png)

1. 설정 **구성** 의 탭 **비프로덕션 파이프라인 추가** 대화 상자에서 생성할 파이프라인 유형을 선택합니다. **코드 품질 파이프라인** 또는 **배포 파이프라인**.


   ![파이프라인 유형 선택](/help/using/assets/configure-pipelines/add-non-production-pipeline.png)

1. 에서 파이프라인에 대한 설명을 제공합니다. **비프로덕션 파이프라인 이름** 필드.

1. 을(를) 추가하도록 선택한 경우 **배포 파이프라인**&#x200B;에서 target 배포 환경을 선택합니다. **적합한 배포 환경** 드롭다운.

1. 파이프라인이 코드를 검색해야 하는 저장소를 제공합니다.

   * **저장소** - 이 옵션은 파이프라인이 코드를 검색해야 하는 Git 리포지토리를 정의합니다.
   * **Git 분기** - 이 옵션은 선택한 파이프라인의 어느 분기에서 코드를 검색해야 하는지를 정의합니다.

1. 배포 옵션을 정의합니다.

   1. 아래 **배포 트리거**&#x200B;을(를) 통해 파이프라인을 활성화하는 이벤트를 정의합니다.

      * **수동** - 이 옵션을 사용하여 파이프라인을 수동으로 시작합니다.
      * **Git 변경 시** - 이 옵션은 구성된 git 분기에 커밋이 추가될 때마다 파이프라인을 시작합니다. 이 옵션을 사용하면 필요에 따라 파이프라인을 수동으로 시작할 수 있습니다.
   1. 아래 **중요한 지표 실패 동작**&#x200B;을(를) 통해 품질 게이트에서 중요한 오류가 발생하는 경우 파이프라인의 동작을 정의합니다.

      * **매번 질문하기** - 기본 설정이며 중요한 오류에 대해 수동으로 개입해야 합니다.
      * **즉시 실패** - 이 옵션을 선택하면 중요한 오류가 발생할 때마다 파이프라인이 취소됩니다. 이것은 기본적으로 사용자가 각 실패를 수동으로 거부하는 것을 에뮬레이션합니다.
      * **즉시 계속** - 이 옵션을 선택하면 중요한 오류가 발생할 때마다 파이프라인이 자동으로 진행됩니다. 이것은 기본적으로 사용자가 각 실패를 수동으로 승인하는 것입니다.


1. 클릭 **저장** 를 클릭하여 파이프라인을 저장합니다.

## 다음 단계 {#the-next-steps}

파이프라인을 구성한 후에는 코드를 배포해야 합니다.

문서 보기 [코드 배포](deploying-code.md) 자세한 내용
