---
title: Cloud Manager에서 저장소 관리
description: Cloud Manager에서 Git 저장소를 조회, 추가 및 삭제하는 방법을 알아봅니다.
exl-id: 384b197d-f7a7-4022-9b16-9d83ab788966
source-git-commit: fb3c2b3450cfbbd402e9e0635b7ae1bd71ce0501
workflow-type: tm+mt
source-wordcount: '730'
ht-degree: 97%

---


# Cloud Manager에서 저장소 관리 {#cloud-manager-repos}

Cloud Manager에서 Git 저장소를 조회, 추가 및 삭제하는 방법을 알아봅니다.

## 개요 {#overview}

Cloud Manager의 저장소는 Git을 사용하여 프로젝트의 코드를 저장하고 관리하는 데 사용됩니다. 추가하는 모든 *프로그램*&#x200B;에는 Adobe 관리 저장소가 자동으로 생성됩니다.

또한 추가 Adobe 관리 저장소를 생성하거나 비공개 저장소를 추가할 수 있습니다. 프로그램에 연결된 모든 저장소는 **저장소** 페이지에서 볼 수 있습니다.

Cloud Manager에서 만들어진 저장소는 파이프라인을 추가하거나 편집할 때도 선택할 수 있습니다. 파이프라인 구성에 대한 자세한 내용은 [CI-CD 파이프라인](/help/overview/ci-cd-pipelines.md)을 참조하십시오.

각 파이프라인은 주 저장소 또는 분기에 연결됩니다. 하지만, [Git 하위 모듈 지원](/help/managing-code/git-submodules.md)을 통해 빌드 프로세스 중에 여러 보조 분기를 포함할 수 있습니다.

## 저장소 페이지 보기 {#repositories-window}

**저장소** 페이지에서 선택한 저장소에 대한 세부 정보를 볼 수 있습니다. 이 정보에는 사용 중인 저장소 유형이 포함됩니다. 저장소가 **Adobe**&#x200B;로 표시된 경우 해당 저장소가 Adobe 관리 저장소임을 나타냅니다. **GitHub**&#x200B;로 레이블이 지정된 경우 관리하는 비공개 GitHub 저장소를 의미함을 나타냅니다. 또한 이 페이지에는 저장소 생성 시기와 관련된 파이프라인과 같은 세부 정보가 있습니다.

선택한 저장소에서 작업을 수행하려면 저장소를 클릭하고 ![기타 아이콘](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg)을 사용하여 드롭다운 메뉴를 엽니다. Adobe 관리 저장소의 경우 **[분기 확인 및 프로젝트 만들기](#check-branches)** 기능을 수행할 수 있습니다.

![저장소 액션](assets/repository-actions.png)
*저장소 페이지의 드롭다운 메뉴*

드롭다운 메뉴에 제공되는 다른 액션에는 **[저장소 URL 복사](#copy-url)**, **[보기 및 업데이트](#view-update)** 및 **[저장소 삭제](#delete)**&#x200B;가 있습니다.

**저장소 페이지를 보려면 다음 작업을 수행하십시오.**

1. [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/)에서 Cloud Manager에 로그인한 다음 적절한 조직과 프로그램을 선택합니다.

1. 사이드 메뉴의 **프로그램 개요** 페이지에서 ![폴더 아이콘](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Folder_18_N.svg) **저장소**&#x200B;를 클릭합니다.

1. **저장소** 페이지에는 선택한 프로그램과 관련된 모든 저장소가 표시됩니다.

   ![저장소 페이지](assets/repositories.png)
   *Cloud Manager의 저장소 페이지.*


## 저장소 추가 {#adding-repositories}

저장소를 추가하려면 사용자에게 **배포 관리자** 또는 **비즈니스 소유자** 역할이 있어야 합니다.

오른쪽 상단 근처의 **저장소** 페이지에서 **저장소 추가**&#x200B;를 클릭합니다.

![저장소 추가 대화 상자.](assets/repository-add.png)
*저장소 추가 대화 상자.*

Cloud Manager는 Adobe 관리 저장소(**Adobe 저장소**)와 사용자 관리 저장소(**비공개 저장소**) 등 두 가지 유형의 저장소를 지원합니다. 설정할 필수 필드는 추가하기 위해 선택한 저장소 유형에 따라 다릅니다. 자세한 내용은 다음을 참조하십시오.

* [Cloud Manager에서 Adobe 저장소 추가](/help/managing-code/adobe-repositories.md)
* [Cloud Manager에서 비공개 저장소 추가](/help/managing-code/private-repositories.md)

특정 회사 또는 IMS 조직의 모든 프로그램에서 300개의 저장소로 제한됩니다.

## 저장소 정보 액세스 {#repo-info}

**저장소** 창에서 저장소를 볼 때 도구 모음에서 **저장소 정보 액세스** 버튼을 클릭하여 Adobe 관리 저장소에 액세스하는 방법에 대한 세부 정보를 프로그래밍 방식으로 볼 수 있습니다.

![저장소 정보](assets/repository-access-repo-info2.png)

**저장소 정보** 창이 열리고 세부 정보가 나타납니다. 저장소 정보 액세스에 대한 자세한 내용은 [저장소 정보 액세스](/help/managing-code/accessing-repositories.md)를 참조하십시오.

## 분기 확인 및 프로젝트 만들기 {#check-branches}

**AEM Cloud Manager**&#x200B;에서 **분기 확인/프로젝트 만들기**&#x200B;는 현재 저장소 상태에 따라 두 가지 용도로 사용됩니다.

* 저장소가 새로 생성된 경우 이 액션은 [AEM Project Archetype](https://experienceleague.adobe.com/ko/docs/experience-manager-core-components/using/developing/archetype/overview)을 사용하여 샘플 프로젝트를 생성합니다.
* 저장소에 이미 샘플 프로젝트가 생성된 경우 액션은 저장소와 해당 분기의 상태를 확인하고 샘플 프로젝트가 이미 존재하는지 여부에 대한 피드백을 제공합니다.

  ![분기 확인 액션](assets/check-branches.png)

## 저장소 URL 복사 {#copy-url}

**저장소 URL 복사** 액션은 **저장소** 페이지에서 선택한 저장소의 URL을 다른 곳에 사용하기 위해 클립보드에 복사합니다.

## 저장소 보기 및 업데이트 {#view-update}

**보기 및 업데이트** 액션은 저장소의 **이름** 및 **저장소 URL 미리보기**&#x200B;를 볼 수 있는 **저장소 업데이트** 대화 상자를 엽니다. 또한 저장소의 **설명**&#x200B;을 업데이트할 수 있습니다.

![저장소 정보 보기 및 업데이트](assets/repository-view-update.png)

## 저장소 삭제 {#delete}

**삭제** 액션은 프로젝트에서 저장소를 제거합니다. 파이프라인과 연결된 저장소는 삭제할 수 없습니다.

![저장소 삭제](assets/delete.png)

Cloud Manager에서 저장소가 삭제되면 삭제됨으로 표시되며 더 이상 사용자가 액세스할 수 없습니다. 그러나 복구 목적으로 시스템에서는 유지됩니다.

동일한 이름의 저장소를 삭제한 후 새 저장소를 만들려고 하면 다음과 같은 오류 메시지가 표시됩니다.

`An error has occurred while trying to create repository. Contact your CSE or Adobe Support.`

이 오류 메시지가 표시되면 Adobe 지원 팀에 문의하십시오. 삭제된 저장소의 이름을 바꾸거나 새 저장소에 대해 다른 이름을 선택할 수 있습니다.
