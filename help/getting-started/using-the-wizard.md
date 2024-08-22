---
title: 새 프로젝트 마법사 사용
description: 마법사를 사용하여 AEM 애플리케이션 프로젝트를 만드는 방법에 대해 배우려면 이 페이지를 따르십시오.
exl-id: 9d7c6f4c-9379-471c-8dad-772a7099da54
source-git-commit: 984269e5fe70913644d26e759fa21ccea0536bf4
workflow-type: tm+mt
source-wordcount: '321'
ht-degree: 30%

---


# 새 프로젝트 마법사 사용 {#using-the-wizard}

새 고객으로 Cloud Manager에 온보딩되면 빈 Git 저장소가 제공됩니다. 시작하는 데 도움을 주기 위해 Cloud Manager는 [AEM Project Archetype](https://github.com/adobe/aem-project-archetype)을 기반으로 최소 AEM 프로젝트를 생성하는 마법사를 제공합니다.

마법사를 사용하여 AEM 프로젝트를 생성하려면 다음 단계를 수행하십시오.

1. [`https://my.cloudmanager.adobe.com`](https://my.cloudmanager.adobe.com)에서 Cloud Manager에 로그인한 다음 적절한 조직을 선택합니다.

1. 아직 만들지 않은 경우 [프로그램을 만듭니다](program-setup.md). 프로그램이 생성되면 Cloud Manager은 저장소가 아직 설정되지 않았음을 감지합니다. 그러면 특수 콜 투 액션 카드가 **개요** 화면에 나타납니다.

   ![프로젝트 CTA 제작](/help/assets/image2018-10-3_14-29-44.png)

1. **만들기**&#x200B;를 클릭하여 마법사를 시작하고 중요한 값을 제공합니다.

   * **제목** - 프로젝트의 제목입니다. 기본적으로 프로그램 이름으로 설정됩니다.
   * **새 분기 이름** - Git 저장소의 초기 분기. 기본적으로 `main`입니다.

   ![프로젝트 값](/help/assets/screen_shot_2018-10-08at55825am.png)

1. 대화 상자에는 아래쪽을 향해 핸들을 클릭하여 열 수 있는 창이 있습니다. 확장된 형태에서 대화 상자에는 AEM Project Archetype에 대한 모든 구성 매개변수가 표시됩니다. 이러한 매개 변수에는 이미 제공한 **Title**&#x200B;을(를) 기반으로 생성되는 기본값이 있으며 수정할 필요가 없습니다. 사용자 정보의 경우 여기에 설명되어 있습니다.

   ![자세한 Archetype 매개변수](/help/assets/screen_shot_2018-10-08at60032am.png)

1. Archetype을 사용하여 스타터 프로젝트를 만들고 지정된 Git 분기에 커밋하려면 **만들기**&#x200B;를 클릭하십시오.

이제 기본 프로젝트가 준비되었습니다. 파이프라인을 설정할 시간입니다.

## 기존 또는 마이그레이션 고객 {#existing-migrating}

현재 Adobe Managed Services(AMS) 고객이거나 마이그레이션 중인 온-프레미스 AEM 고객인 경우 Git이나 다른 버전 제어 시스템에 프로젝트 코드가 있을 수 있습니다.

이러한 경우 프로젝트를 Cloud Manager Git 저장소로 가져올 수 있습니다.
