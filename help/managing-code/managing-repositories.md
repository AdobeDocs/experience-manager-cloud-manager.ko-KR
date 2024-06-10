---
title: Cloud Manager에서 저장소 관리
description: Cloud Manager에서 git 저장소를 생성, 확인 및 편집하는 방법에 대해 알아봅니다.
exl-id: 384b197d-f7a7-4022-9b16-9d83ab788966
source-git-commit: 73add7bee892769d1b3864e3238aff26bf96162d
workflow-type: tm+mt
source-wordcount: '660'
ht-degree: 25%

---


# Cloud Manager 저장소 {#cloud-manager-repos}

Cloud Manager에서 git 저장소를 생성, 확인 및 편집하는 방법에 대해 알아봅니다.

## 개요 {#overview}

저장소는 Git을 사용하여 프로젝트의 코드를 저장하고 관리하는 데 사용됩니다. Cloud Manager에서 만드는 모든 프로그램에는 Adobe 관리 저장소가 있습니다.

추가 Adobe 관리 저장소를 생성하고 자신의 개인 저장소를 추가하도록 선택할 수 있습니다. 프로그램과 연결된 모든 저장소는 **저장소** 창.

Cloud Manager에서 만들어진 저장소는 파이프라인을 추가하거나 편집할 때도 선택할 수 있습니다. 자세한 내용은 [CI-CD 파이프라인](/help/overview/ci-cd-pipelines.md)을 참조하십시오.

지정된 파이프라인에 대해 단일 주 저장소 또는 분기가 있습니다. 포함 [git 하위 모듈 지원,](git-submodules.md) 빌드 시 많은 보조 분기를 포함할 수 있습니다.

## 저장소 창 {#repositories-window}

1. [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/)에서 Cloud Manager에 로그인한 다음 적절한 조직과 프로그램을 선택합니다.

1. 다음에서 **프로그램 개요** 페이지에서 **저장소** 탭을으로 전환합니다. **저장소** 페이지를 가리키도록 업데이트하는 중입니다.

1. 다음 **저장소** 창에 프로그램과 연결된 모든 저장소가 표시됩니다.

   ![저장소 창](assets/repositories.png)

다음 **저장소** 창에서는 저장소에 대한 세부 정보를 제공합니다.

* 저장소 유형
   * **Adobe** Adobe 관리 저장소를 나타냅니다.
   * **GitHub** 사용자가 관리하는 개인 GitHub 저장소를 나타냅니다.
* 생성 시기
* 저장소와 연결된 파이프라인

창에서 저장소를 선택하고 줄임표 버튼을 클릭하여 선택한 저장소에서 작업을 수행할 수 있습니다.

* **[분기 확인 / 프로젝트 만들기](#check-branches)** (Adobe 저장소에만 사용 가능)
* **[저장소 URL 복사](#copy-url)**
* **[보기 및 업데이트](#view-update)**
* **[삭제](#delete)**

![저장소 작업](assets/repository-actions.png)

## 저장소 추가 {#adding-repositories}

을(를) 탭하거나 클릭합니다 **저장소 추가** 의 단추 **저장소** 시작 창 **저장소 추가** 마법사.

![저장소 추가 마법사](assets/add-repository-wizard.png)

Cloud Manager는 Adobe이 관리하는 두 저장소를 모두 지원합니다(**Adobe 저장소**)와 자체 자체 관리되는 저장소(**개인 저장소**). 필수 필드는 추가하려는 저장소 유형에 따라 다릅니다. 자세한 내용은 다음 문서를 참조하십시오.

* [Cloud Manager에서 Adobe 저장소 추가](adobe-repositories.md)
* [Cloud Manager에서 개인 저장소 추가](private-repositories.md)

>[!NOTE]
>
>* 저장소를 추가하려면 사용자에게 **배포 관리자** 또는 **비즈니스 소유자** 역할이 있어야 합니다.
>* 특정 회사 또는 IMS 조직의 모든 프로그램에서 300개의 저장소로 제한됩니다.

## 저장소 정보 확인 {#repo-info}

에서 저장소를 볼 때 **저장소** 창에서는 을 탭하거나 클릭하여 Adobe 관리 저장소에 프로그래밍 방식으로 액세스하는 방법에 대한 세부 사항을 볼 수 있습니다. **저장소 정보 액세스** 단추를 클릭합니다.

![저장소 정보](assets/access-repo-info.png)

다음 **저장소 정보** 세부 정보가 포함된 창이 열립니다. 저장소 정보 액세스에 대한 자세한 내용은 문서를 참조하십시오 [저장소 정보에 액세스](accessing-repositories.md)

## 분기 확인 {#check-branches}

다음 **분기 확인 / 프로젝트 만들기** 작업은 저장소의 상태에 따라 두 가지 기능을 수행합니다.

* 저장소가 새로 만들어지면 작업은 다음에 준하여 샘플 프로젝트를 만듭니다. [AEM project archetype.](https://experienceleague.adobe.com/en/docs/experience-manager-core-components/using/developing/archetype/overview)
* 저장소에서 이미 샘플 프로젝트를 만든 경우, 저장소 및 해당 분기의 상태를 확인하고 샘플 프로젝트가 이미 있는지 다시 보고합니다.

![분기 작업 확인](assets/check-branches.png)

## 저장소 URL 복사 {#copy-url}

다음 **저장소 URL 복사** 작업에서 선택한 저장소의 URL을 **저장소** 다른 곳에서 사용할 클립보드에 대한 창입니다.

## 보기 및 업데이트 {#view-update}

다음 **보기 및 업데이트** 작업이 다음을 엽니다. **저장소 업데이트** 대화 상자. 이를 사용하여 다음을 볼 수 있습니다 **이름** 및 **저장소 URL 미리보기** 및 업데이트 **설명** 저장소의 입니다.

![저장소 정보 보기 및 업데이트](assets/update-repository.png)

## 삭제 {#delete}

다음 **삭제** 작업을 수행하면 프로젝트에서 저장소가 제거됩니다. 저장소가 파이프라인과 연결된 경우 삭제할 수 없습니다.

![삭제](assets/delete.png)

저장소가 Cloud Manager에서 삭제되면 해당 저장소는 삭제된 것으로 표시되며 더 이상 사용자가 액세스할 수는 없지만 복구 목적으로 시스템에 유지됩니다.

같은 이름의 저장소를 삭제한 후 새 저장소를 만들려고 하면 오류 메시지가 표시됩니다 `An error has occurred while trying to create repository. Please contact your CSE or Adobe Support.`

이 오류 메시지가 표시되면 Adobe 지원 센터에 문의하여 삭제된 저장소의 이름을 바꾸거나 새 저장소에 대해 다른 이름을 선택할 수 있도록 하십시오.
