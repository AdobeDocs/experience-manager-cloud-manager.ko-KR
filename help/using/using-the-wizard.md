---
title: 마법사 사용
description: 이 페이지에서 마법사를 사용하여 AEM 응용 프로그램 프로젝트를 만드는 방법을 알아봅니다.
translation-type: tm+mt
source-git-commit: 7146a41d64365c9de03d32f4fc4c33f9e366c244
workflow-type: tm+mt
source-wordcount: '332'
ht-degree: 0%

---


# 마법사 {#using-wizard-to-create-an-aem-application-project} 사용

고객이 Cloud Manager에 온보드 방식을 사용하는 경우 빈 git 저장소가 제공됩니다. 현재 AMS(Adobe Managed Services) 고객(또는 AMS로 마이그레이션하는 온프레미스 AEM 고객)은 일반적으로 프로젝트 코드를 git(또는 다른 버전 제어 시스템)에 이미 가지고 있으며 프로젝트를 Cloud Manager git 리포지토리로 가져옵니다. 그러나 새 고객은 기존 프로젝트를 가지고 있지 않습니다.

새로운 고객을 위한 Cloud Manager의 시작점으로 최소한의 AEM 프로젝트를 제작할 수 있습니다. 이 프로세스는 [**AEM 프로젝트 원형**](https://github.com/Adobe-Marketing-Cloud/aem-project-archetype)을 기반으로 합니다.


Cloud Manager에서 AEM 애플리케이션 프로젝트를 만들려면 아래 절차를 따르십시오.

1. Cloud Manager에 로그인하고 기본 프로그램 설정이 완료되면 저장소가 비어 있는 경우 작업 카드 호출이 **개요** 화면에 표시됩니다.

   ![](assets/image2018-10-3_14-29-44.png)

1. **만들기를 클릭하여** 대화 상자를 엽니다. 그러면 사용자가 AEM 프로젝트 원형에서 필요한 매개 변수를 제공할 수 있습니다. 기본 양식에서는 대화 상자에 두 개의 값이 표시됩니다.

   * **제목**  - 기본적으로  *프로그램 이름으로 설정됩니다.*

   * **새 분기 이름**  - 기본적으로  *마스터*

   ![](assets/screen_shot_2018-10-08at55825am.png)

   대화 상자에는 대화 상자의 하단의 핸들을 클릭하여 열 수 있는 서랍이 있습니다. 확장된 형식의 대화 상자에는 원형 유형에 대한 모든 구성 매개 변수가 표시됩니다. 이러한 매개 변수 중에는 **Title**&#x200B;을 기반으로 생성된 기본값이 있습니다.

   ![](assets/screen_shot_2018-10-08at60032am.png)

   >[!NOTE]
   >
   >예를 들어 **Title**&#x200B;이 ***We.Finance***&#x200B;이면 Base Maven Artifact Id 매개 변수가 ***com.wefinance***&#x200B;로 생성됩니다. 원하는 경우 이러한 값을 변경할 수 있습니다.
   >
   >
   >예를 들어 생성된 ***value com.wefinance***&#x200B;에서 ***net.wefinance***&#x200B;로 변경할 수 있습니다.

1. 이전 단계에서 **만들기**&#x200B;를 클릭하여 시작 프로젝트를 만들고 지정된 git 분기에 커밋합니다. 이렇게 하면 파이프라인을 설정할 수 있습니다.