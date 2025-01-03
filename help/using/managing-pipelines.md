---
title: 파이프라인 관리
description: 실행, 편집 및 삭제를 포함하여 기존 파이프라인을 관리하는 방법을 알아봅니다.
exl-id: e36420d2-57c5-4375-99fb-dd47c1c8bffd
source-git-commit: 9d910e1b1a4aad000a8389ddc22ce380bbccd4ef
workflow-type: ht
source-wordcount: '840'
ht-degree: 100%

---


# 파이프라인 관리 {#managing-pipelines}

실행, 편집 및 삭제를 포함하여 기존 파이프라인을 관리하는 방법을 알아봅니다.

## 파이프라인 카드 {#pipeline-card}

Cloud Manager의 **프로그램 개요** 페이지에 있는 **파이프라인** 카드는 모든 파이프라인과 현재 상태에 대한 개요를 제공합니다.

![Cloud Manager의 파이프라인 카드](/help/assets/configure-pipelines/pipelines-card.png)

각 파이프라인 옆에 있는 줄임표 버튼을 클릭하여 다음 액션을 수행할 수 있습니다.

* [파이프라인 실행](#running-pipelines).
* [파이프라인 편집](#editing-pipelines).
* [파이프라인 삭제](#deleting-pipelines).
* [세부 정보 보기](#view-details).

파이프라인 목록의 맨 아래에는 다음의 일반 옵션이 있습니다.

* **추가** - [새 프로덕션 파이프라인을 추가](/help/using/production-pipelines.md)하거나 [새 비프로덕션 파이프라인을 추가](/help/using/non-production-pipelines.md)합니다.
* **모두 표시** - **파이프라인** 화면으로 사용자를 이동하여 더 자세한 테이블에서 모든 파이프라인을 볼 수 있습니다.
* **저장소 액세스 정보** - Cloud Manager Git 저장소에 액세스하는 데 필요한 정보를 표시합니다.
* **자세히 알아보기** - CI/CD 파이프라인 설명서 리소스로 이동합니다.

## 파이프라인 페이지 {#pipelines}

**파이프라인** 페이지에는 선택한 프로그램에 대한 모든 파이프라인의 전체 목록이 표시됩니다. 이 목록은 [파이프라인 카드](#pipeline-card)에서 제공되는 정보보다 더 포괄적인 정보를 담고 있으므로 유용합니다.

1. [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/)에서 Cloud Manager에 로그인한 다음 적절한 조직과 프로그램을 선택합니다.

1. **프로그램 개요** 페이지에서 **파이프라인** 탭을 클릭하여 **파이프라인** 페이지로 전환합니다.

1. 여기서는 **파이프라인 카드**&#x200B;에서와 같이 프로그램의 모든 파이프라인 목록을 보고 파이프라인 실행을 시작 및 정지할 수도 있습니다.

`i` 아이콘을 클릭하면 파이프라인의 마지막 실행 또는 현재 실행에 대한 세부 정보가 표시됩니다.

![파이프라인 실행 세부 정보](/help/assets/configure-pipelines/pipeline-status.png)

**세부 정보 보기**&#x200B;를 클릭하면 [파이프라인 실행에 대한 세부 정보](#view-details)를 확인할 수 있습니다.

## 활동 페이지 {#activity}

**활동** 페이지에는 선택한 프로그램에 대한 모든 파이프라인 실행의 전체 목록이 표시됩니다.

1. [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/)에서 Cloud Manager에 로그인한 다음 적절한 조직과 프로그램을 선택합니다.

1. **프로그램 개요** 페이지에서 **활동** 탭을 클릭하여 **활동** 페이지로 전환합니다.

1. 여기에서는 현재 실행과 이전 실행을 포함하여 프로그램에 대한 모든 파이프라인 실행 목록을 볼 수 있습니다.

`i` 아이콘을 클릭하면 선택한 파이프라인 실행의 실행에 대한 세부 정보가 표시됩니다.

![파이프라인 실행 세부 정보](/help/assets/configure-pipelines/pipeline-activity.png)

**세부 정보 보기**&#x200B;를 클릭해 [파이프라인 실행 세부 정보](#view-details)를 확인합니다.

## 파이프라인 실행 {#running-pipelines}

1. [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/)에서 Cloud Manager에 로그인한 다음 적절한 조직과 프로그램을 선택합니다.
1. **프로그램 개요** 페이지에서 **파이프라인** 카드로 이동합니다.
1. 실행하는 파이프라인 옆의 줄임표 버튼을 클릭한 다음 메뉴에서 **실행**&#x200B;을 선택합니다.

   파이프라인 실행이 시작되면 상태 열에 표시됩니다.

   줄임표 버튼을 다시 클릭하고 **[세부 정보 보기](#view-details)**&#x200B;를 선택하면 실행 세부 정보를 볼 수 있습니다.

   파이프라인 유형에 따라 줄임표 버튼을 다시 클릭하고 **취소**&#x200B;를 선택하여 실행을 취소할 수 있습니다.

## 파이프라인 편집 {#editing-pipelines}

1. [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/)에서 Cloud Manager에 로그인한 다음 적절한 조직과 프로그램을 선택합니다.

1. **프로그램 개요** 페이지에서 **파이프라인** 카드로 이동한 다음 편집할 파이프라인 옆에 있는 줄임표 버튼을 클릭하고 메뉴에서 **편집**&#x200B;을 선택합니다.

1. **프로덕션 파이프라인 편집** 또는 **비프로덕션 파이프라인 편집** 대화 상자가 나타납니다. 파이프라인을 생성하는 동안 입력한 것과 동일한 세부 정보를 편집할 수 있습니다.

   파이프라인에 사용 가능한 필드 및 구성 옵션에 대한 자세한 내용은 [프로덕션 파이프라인 구성](/help/using/production-pipelines.md) 및 [비프로덕션 파이프라인 구성](/help/using/non-production-pipelines.md)을 참조하십시오.

1. 완료되면 **업데이트**&#x200B;를 클릭합니다.

>[!NOTE]
>
>실행 중인 파이프라인은 편집할 수 없습니다.

## 파이프라인 삭제 {#deleting-pipelines}

1. [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/)에서 Cloud Manager에 로그인한 다음 적절한 조직과 프로그램을 선택합니다.

1. **프로그램 개요** 페이지에서 **파이프라인** 카드로 이동한 다음 실행하는 파이프라인 옆에 있는 줄임표 버튼을 클릭하고 메뉴에서 **삭제**&#x200B;를 선택합니다.

>[!NOTE]
>
>실행 중인 파이프라인은 삭제할 수 없습니다.

## 세부 정보 보기 {#view-details}

1. [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/)에서 Cloud Manager에 로그인한 다음 적절한 조직과 프로그램을 선택합니다.

1. **프로그램 개요** 페이지에서 **파이프라인** 카드로 이동한 다음 실행하는 파이프라인 옆에 있는 줄임표 버튼을 클릭하고 메뉴에서 **세부 정보 보기**&#x200B;를 선택합니다.

1. 실행 중인 파이프라인의 세부 정보 페이지로 이동합니다.

![파이프라인 세부 정보](/help/assets/configure-pipelines/pipeline-running-details.png)

여기에서 파이프라인의 다양한 단계 상태를 확인하고 진단 목적으로 빌드 로그를 검색할 수 있습니다. 자세한 내용은 [코드 배포](/help/using/code-deployment.md) 문서를 참조하십시오.

모든 파이프라인 실행 단계는 아직 시작되지 않은 단계가 회색으로 바뀌어 표시됩니다. 완료된 단계에는 기간이 표시됩니다.

파이프라인 단계가 완료되면 요약이 표시됩니다.

![단계 요약](/help/assets/configure-pipelines/pipeline-step.png)

**기간** 섹션을 표시하려면 **세부 정보 보기** 링크를 클릭합니다. 이 섹션에는 해당 프로그램의 과거 트렌드를 기반으로 한 파이프라인의 평균 기간이 포함됩니다.

![기간](/help/assets/configure-pipelines/duration.png)

파이프라인에 문제가 발생한 **코드 스캔** 단계가 있는 경우 **세부 정보 다운로드** 버튼을 클릭하여 통과하지 못한 [코드 품질 테스트](/help/using/code-quality-testing.md) 목록을 볼 수 있습니다.

![코드 품질 문제](assets/managing-pipelines-code-quality-issues.png)

**프로젝트 파일 위치** 열은 문제가 있는 코드의 위치를 &#x200B;&#x200B;나타내는 CSV 파일에서 사용할 수 있습니다. 이 열은 프로젝트 관련 경로이며, **파일 위치** 열은 Maven에서 생성됩니다.

![프로젝트 코드 스캔 문제 세부 정보](assets/managing-pipelines-code-quality-details.png)


>[!NOTE]
>
>실행 중이거나 한 번 이상 실행된 파이프라인의 세부 정보만 볼 수 있습니다.
