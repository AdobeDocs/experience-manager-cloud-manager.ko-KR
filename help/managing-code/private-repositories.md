---
title: Cloud Manager에서 비공개 저장소 추가
description: 개인 GitHub 저장소에서 작동하도록 Cloud Manager를 설정하는 방법에 대해 알아봅니다.
feature: Release Information
exl-id: e0d103c9-c147-4040-bf53-835e93d78a0b
source-git-commit: fb3c2b3450cfbbd402e9e0635b7ae1bd71ce0501
workflow-type: tm+mt
source-wordcount: '815'
ht-degree: 97%

---


# Cloud Manager에서 비공개 저장소 추가 {#private-repositories}

개인 GitHub 저장소에서 작동하도록 Cloud Manager를 설정하는 방법에 대해 알아봅니다.

## 개요 {#overview}

개인 GitHub 저장소로 Cloud Manager를 구성하면 GitHub 내에서 직접 코드를 검증할 수 있으므로 Adobe 저장소와 자주 동기화할 필요가 없습니다.

>[!NOTE]
>
>이 기능은 공개 GitHub 전용입니다. 자체 호스팅 GitHub에 대해서는 지원되지 않습니다.

## 구성 {#configuration}

구성은 두 가지 기본 단계로 구성됩니다.

1. [저장소 추가](#add-repo)
1. [비공개 저장소 소유권 유효성 검사](#validate-ownership)



### 저장소 추가 {#add-repo}

1. Cloud Manager의 **프로그램 개요** 페이지에서 **저장소** 탭을 탭하거나 클릭하여 **저장소** 페이지로 전환한 다음 **저장소 추가**&#x200B;를 클릭합니다.

1. **저장소 추가** 대화 상자에서 **비공개 저장소**&#x200B;를 저장소 유형으로 선택합니다.

1. 저장소의 세부 정보 제공

   * **저장소 이름** - 표현적인 이름
   * **저장소 URL** - `.git`으로 끝나는 저장소 URL
   * **설명**(선택 사항) - 필요에 따라 저장소에 대한 자세한 설명

   ![자체 저장소 추가](/help/assets/repositories/add-own-github.png)

1. **저장**&#x200B;을 클릭합니다.

>[!TIP]
>
>Cloud Manager의 저장소 관리에 대한 자세한 내용은 [Cloud Manager 저장소](/help/managing-code/managing-repositories.md)를 참조하십시오.



### 비공개 저장소 소유권 유효성 검사 {#validate-ownership}

이제 Cloud Manager는 GitHub 저장소에 대해 알게 되었지만 여전히 이에 대한 액세스가 필요합니다. 액세스 권한을 부여하려면 Adobe GitHub 앱을 설치하고 지정된 저장소를 소유하고 있는지 확인해야 합니다.

1. 자체 저장소를 추가하면 **비공개 저장소 소유권 유효성 검사** 대화 상자가 나타납니다.

   ![비공개 저장소 소유권 유효성 검사](/help/assets/repositories/private-repo-validate.png)

1. Cloud Manager는 GitHub 앱을 사용하여 저장소와 안전하게 상호 작용합니다.

   GitHub 조직의 소유자는 `https://github.com/apps/cloud-manager-for-aem`에 있는 앱을 설치하고 저장소에 대한 액세스 권한을 부여해야 합니다. 자세한 내용은 GitHub의 설명서를 참조하십시오.

1. 보안 강화를 위해 저장소의 기본 분기에 시크릿 파일을 만듭니다. **생성**&#x200B;을 클릭합니다.

1. **확인**&#x200B;을 클릭하여 시크릿 파일이 생성되었는지 확인합니다.

   ![시크릿 생성 확인](/help/assets/repositories/confirm-generation.png)

1. **비공개 저장소 소유권 유효성 검사** 대화 상자로 돌아가면 Cloud Manager가 **시크릿 파일 콘텐츠** 필드에 콘텐츠를 생성했습니다. 해당 필드의 콘텐츠를 복사합니다.

   시크릿 파일의 콘텐츠는 한 번만 표시됩니다. 이 창을 닫기 전에 콘텐츠를 복사하지 않으면 시크릿을 다시 생성해야 합니다.

   ![시크릿 파일 콘텐츠 복사](/help/assets/repositories/new-secret.png)

1. `.well-known/adobe/cloud-manager-challenge`라는 GitHub 저장소의 기본 분기에 새 파일을 만들고 시크릿 파일 콘텐츠를 해당 파일에 붙여넣어 저장합니다.

1. 앱을 설치하고 시크릿 파일이 저장소에 있으면 **비공개 저장소 소유권 유효성 검사** 대화 상자의 **유효성 검사**&#x200B;를 클릭할 수 있습니다.

앱을 설치하고 시크릿 파일을 순서에 관계없이 생성할 수 있습니다. 그러나 유효성을 검사하려면 두 단계를 모두 완료해야 합니다.

유효성 검사 전까지 저장소는 빨간색 아이콘으로 나열되며, 이는 아직 검증되지 않았고 사용할 수 없음을 나타냅니다.

![검증되지 않은 저장소](/help/assets/repositories/unvalidated-repo.png)

**유형** 열을 통해 Adobe 제공 저장소(**Adobe**) 및 자체 GitHub 저장소(**GitHub**)를 쉽게 식별할 수 있습니다.

나중에 저장소로 돌아와서 유효성 검사를 완료하려면 **저장소** 페이지로 이동합니다. 추가한 GitHub 저장소 옆에 있는 ![기타 아이콘(줄임표)](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg)를 클릭한 다음 **소유권 확인**&#x200B;을 클릭합니다.


## Cloud Manager로 비공개 저장소 사용 {#using}

Cloud Manager에서 GitHub 저장소의 유효성을 검사하면 통합이 완료되고 Cloud Manager에서 저장소를 사용할 수 있습니다.

**Cloud Manager로 비공개 저장소를 사용하려면:**

1. 가져오기 요청을 만들면 GitHub 검사가 자동으로 시작됩니다.

   ![GitHub 검사](/help/assets/repositories/github-checks.png)

1. 각 가져오기 요청에 대해 [전체 스택 코드 품질 파이프라인](/help/using/managing-pipelines.md)이 자동으로 생성됩니다. 이 파이프라인은 가져오기 요청이 업데이트될 때마다 시작됩니다.

1. GitHub 검사는 코드 품질 검사가 완료될 때까지 실행 상태로 유지됩니다. 그러면 코드 품질 결과가 GitHub 검사에 반영됩니다.

   ![GitHub 코드 품질 검사](/help/assets/repositories/github-code-quality.png)

가져오기 요청이 닫히거나 병합되면 생성된 전체 스택 코드 품질 파이프라인이 자동으로 삭제됩니다.

>[!TIP]
>
>가져오기 요청 검사가 실행될 때 GitHub를 통해 제공되는 정보에 대한 자세한 내용은 [GitHub 검사 주석](github-annotations.md) 문서를 참조하십시오.

>[!TIP]
>
>비공개 저장소에 대한 각각의 가져오기 요청 유효성 검사를 위해 자동으로 생성되는 파이프라인 제어할 수 있습니다. 자세한 내용은 [비공개 저장소에 대한 GitHub 검사 구성](github-check-config.md)을 참조하십시오.



## 비공개 저장소를 파이프라인과 연결 {#pipelines}

유효성이 확인된 비공개 저장소는 [전체 스택 및 프론트엔드 파이프라인](/help/overview/ci-cd-pipelines.md)과 연결될 수 있습니다.



## 제한 사항 {#limitations}

Cloud Manager으로 비공개 저장소를 사용하는 경우 특정 제한 사항이 있습니다.

* 웹 계층 및 구성 파이프라인은 비공개 저장소에서 지원되지 않습니다.
* 프로덕션 전체 스택 파이프라인에서 비공개 저장소를 사용할 때 Git 태그가 생성 및 푸시되지 않습니다.
* Adobe GitHub 애플리케이션이 GitHb 조직에서 제거되면 모든 저장소에 대한 가져오기 요청 유효성 검사 기능이 제거됩니다.
* 개인 저장소 및 커밋된 빌드 트리거를 사용하는 파이프라인은 새 커밋이 선택한 분기에 푸시될 때 자동으로 시작되지 않습니다.
* [아티팩트 재사용 기능](/help/getting-started/project-setup.md#build-artifact-reuse)은 비공개 저장소에는 적용되지 않습니다.
* Cloud Manager의 GitHub 검사를 사용하여 가져오기 요청 유효성 검사를 일시 정지할 수 없습니다. GitHub 저장소가 Cloud Manager에서 검증되면 Cloud Manager는 해당 저장소에 대해 생성된 가져오기 요청의 유효성 검사를 시도합니다.
