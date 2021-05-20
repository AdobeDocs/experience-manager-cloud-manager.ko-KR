---
title: 마법사 사용
description: 마법사를 사용하여 AEM Application Project를 만드는 방법을 배우려면 이 페이지를 따르십시오
feature: 시작하기
exl-id: 9d7c6f4c-9379-471c-8dad-772a7099da54
source-git-commit: 43bb3c477ef9c1ce178509b8180479d7616edc66
workflow-type: tm+mt
source-wordcount: '334'
ht-degree: 0%

---

# 마법사 사용 {#using-wizard-to-create-an-aem-application-project}

고객이 Cloud Manager에 온보딩되면 빈 git 리포지토리가 제공됩니다. 현재 AMS(Adobe Managed Services) 고객(또는 AMS로 마이그레이션하는 온-프레미스 AEM 고객은 일반적으로 git(또는 다른 버전 제어 시스템)에서 프로젝트 코드를 이미 가지고 있으며 해당 프로젝트를 Cloud Manager git 저장소로 가져옵니다. 그러나 새 고객은 기존 프로젝트를 가지고 있지 않습니다.

새로운 고객을 시작할 수 있도록 이제 Cloud Manager에서 최소한의 AEM 프로젝트를 시작점으로 만들 수 있습니다. 이 프로세스는 [**AEM Project Archetype**](https://github.com/Adobe-Marketing-Cloud/aem-project-archetype)를 기반으로 합니다.


Cloud Manager에서 AEM 애플리케이션 프로젝트를 생성하려면 아래 절차를 따르십시오.

1. Cloud Manager에 로그인하고 기본 프로그램 설정이 완료되면 저장소가 비어 있는 경우 작업 카드에 대한 특수 호출이 **개요** 화면에 표시됩니다.

   ![](assets/image2018-10-3_14-29-44.png)

1. **만들기 를 클릭하여** 대화 상자를 엽니다. 그러면 사용자가 AEM Project Archetype에 필요한 매개 변수를 제공할 수 있습니다. 기본 양식에서 대화 상자는 다음 두 값을 요청합니다.

   * **제목**  - 기본적으로  *프로그램 이름으로 설정됩니다.*

   * **새 분기 이름**  - 기본적으로  *마스터입니다.*

   ![](assets/screen_shot_2018-10-08at55825am.png)

   대화 상자에는 대화 상자의 하단에서 핸들을 클릭하여 열 수 있는 서랍이 있습니다. 확장된 양식에서 대화 상자에는 Archetype에 대한 모든 구성 매개 변수가 표시됩니다. 이러한 매개 변수의 대부분은 **제목**&#x200B;을 기반으로 생성되는 기본값이 있습니다.

   ![](assets/screen_shot_2018-10-08at60032am.png)

   >[!NOTE]
   >
   >예를 들어 **Title**&#x200B;이 ***We.Finance***&#x200B;인 경우 Base Maven Artifact Id 매개 변수가 ***com.wefinance***&#x200B;로 생성됩니다. 원하는 경우 이러한 값을 변경할 수 있습니다.
   >
   >
   >예를 들어 생성된 ***value com.wefinance***&#x200B;에서 ***net.wefinance***&#x200B;로 변경할 수 있습니다.

1. 이전 단계에서 **만들기** 를 클릭하여 원형 을 사용하여 시작 프로젝트를 만들고 명명된 git 분기에 커밋합니다. 이 작업이 완료되면 파이프라인을 설정할 수 있습니다.
