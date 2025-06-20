---
title: 평가 단계
seo-title: Evaluation Phase
description: 제품 업데이트 마법사의 평가 단계에서 패턴 감지기의 업그레이드 복잡성을 평가하는 방법에 대해 알아봅니다.
exl-id: 1ffcbc21-dc36-435d-b83b-0209f81a15e7
source-git-commit: fb3c2b3450cfbbd402e9e0635b7ae1bd71ce0501
workflow-type: tm+mt
source-wordcount: '257'
ht-degree: 57%

---


# 평가 단계 {#evaluation}

제품 업데이트 마법사의 첫 번째 단계는 **[!UICONTROL 평가]** 단계입니다. 마법사 내에서 패턴 감지기를 실행하여 업그레이드 복잡성을 평가합니다. 이 단계가 끝나면 평가 보고서를 볼 수 있습니다.

이 보고서는 다음에 대한 패턴을 감지하여 작성자 인스턴스의 업그레이드 준비 상태를 확인합니다.

* 업그레이드의 영향을 받거나 덮어쓴 영역의 규칙 위반.
* 이전 버전과 호환되지 않으며 업그레이드 후 중단될 수 있는 AEM 6.x 기능 또는 API를 사용합니다.

이 보고서는 Adobe Experience Manager(AEM) 6.5로 업그레이드하는 데 필요한 개발 노력을 예상하는 데 도움이 됩니다.

>[!NOTE]
>
>패턴 감지기에 대한 자세한 내용은 [패턴 감지기를 사용한 업그레이드 복잡성 평가](https://experienceleague.adobe.com/ko/docs/experience-manager-65/content/implementing/deploying/upgrading/pattern-detector)를 참조하십시오.

## 평가 보고서 실행 {#running}

패턴 감지기는 모든 환경에서 실행할 수 있습니다. 그러나 검색 속도를 높이고 비즈니스 크리티컬 인스턴스의 지연을 방지하기 위해 Cloud Manager는 작성자 인스턴스의 스테이징 환경에서 이 인스턴스를 실행합니다.

**평가 보고서 실행하려면:**

1. [제품 업데이트 마법사](/help/product-update-wizard/overview.md)의 설명에 따라 마법사를 시작합니다.

1. **[!UICONTROL 평가 실행]**&#x200B;을 클릭합니다.

   ![평가 실행](/help/assets/Run-Evaluation.png)

1. 마법사가 작업 상태를 알려 줍니다. 평가 보고서가 생성되면 **진행 중** 또는 **완료됨**&#x200B;이 표시됩니다.

1. 보고서가 생성되면 **[!UICONTROL 보고서 다운로드]**&#x200B;를 클릭하여 사본을 저장할 수 있습니다.

   ![보고서 생성됨](/help/assets/Evaluation-1.png)

Cloud Manager의 현재 제품 업데이트 마법사는 **평가** 단계만 지원합니다. 나머지 네 가지 단계인 **교정**, **실행**, **유효성 검사** 및 **완료**&#x200B;가 곧 제공될 예정입니다.
