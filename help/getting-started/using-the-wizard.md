---
title: 새 프로젝트 마법사 사용
description: 마법사를 사용하여 AEM Application Project를 만드는 방법을 배우려면 이 페이지를 따르십시오
exl-id: 9d7c6f4c-9379-471c-8dad-772a7099da54
source-git-commit: cb791a4f148ba394687b5e824b75fe1386d83c18
workflow-type: tm+mt
source-wordcount: '330'
ht-degree: 0%

---


# 새 프로젝트 마법사 사용 {#using-the-wizard}

새 고객으로서 Cloud Manager에 온보딩되면 빈 git 리포지토리가 제공됩니다. 시작하는 데 도움이 되도록 Cloud Manager는 다음을 기반으로 최소한의 AEM 프로젝트를 만드는 마법사를 제공합니다. [AEM 프로젝트 원형](https://github.com/Adobe-Marketing-Cloud/aem-project-archetype) 시작점으로 사용하십시오.

다음 단계에 따라 마법사를 사용하여 AEM 프로젝트를 만듭니다.

1. Cloud Manager에 로그인 위치 [`https://my.cloudmanager.adobe.com`](https://my.cloudmanager.adobe.com) 적절한 조직을 선택합니다.

1. 아직 안하셨다면, [프로그램을 만듭니다.](program-setup.md) 프로그램이 만들어지면 Cloud Manager는 리포지토리가 아직 설정되어 있지 않으며 클릭 유도 카드를 **개요** 화면.

   ![프로젝트 CTA 만들기](/help/assets/image2018-10-3_14-29-44.png)

1. 클릭 **만들기** 마법사를 시작하고 중요한 값을 제공하려면 다음을 수행하십시오.

   * **제목** - 프로젝트 제목이며 기본적으로 프로그램 이름으로 설정됩니다.
   * **새 분기 이름** - Git 리포지토리의 초기 분기이며, 기본적으로 다음과 같습니다. `main`.

   ![프로젝트 값](/help/assets/screen_shot_2018-10-08at55825am.png)

1. 대화 상자에는 아래쪽의 핸들을 클릭하여 열 수 있는 서랍이 있습니다. 확장된 양식에서 대화 상자에는 AEM 프로젝트 원형에 대한 모든 구성 매개 변수가 표시됩니다. 이러한 매개 변수에는 **제목** 이미 제공했으며 수정할 필요가 없습니다. 여기에 설명을 해 드리겠습니다.

   ![자세한 원형 매개 변수](/help/assets/screen_shot_2018-10-08at60032am.png)

1. 클릭 **만들기** 원형 을 사용하여 시작 프로젝트를 만들고 명명된 git 분기에 커밋합니다.

이제 기본 프로젝트가 있습니다! 이제 파이프라인을 설정할 수 있습니다.

## 기존 또는 마이그레이션 고객 {#existing-migrating}

현재 AMS(Adobe Managed Services) 고객이나 로 마이그레이션하는 온-프레미스 AEM 고객인 경우, 이미 git 또는 다른 버전 제어 시스템에 프로젝트 코드가 있을 수 있습니다.

이러한 경우 프로젝트를 Cloud Manager git 리포지토리로 가져옵니다.
