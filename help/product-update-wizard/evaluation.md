---
title: 평가 단계
seo-title: Evaluation Phase
description: 제품 업데이트 마법사의 평가 단계에서 패턴 감지기의 업그레이드 복잡성을 평가하는 방법에 대해 알아봅니다.
exl-id: 1ffcbc21-dc36-435d-b83b-0209f81a15e7
source-git-commit: ce2145da3b9e605e8a41bac28df520f14e255557
workflow-type: tm+mt
source-wordcount: '296'
ht-degree: 100%

---


# 평가 단계 {#evaluation}

제품 업데이트 마법사의 첫 번째 단계는 **[!UICONTROL 평가]** 단계로, 마법사 내에서 직접 패턴 감지기를 사용하여 업그레이드 복잡성을 평가합니다. 이 단계를 마치면 평가 보고서에 액세스할 수 있습니다.

생성된 보고서를 통해 다음 패턴을 감지하여 작성자 인스턴스의 업그레이드 적격성을 확인할 수 있습니다.

* 업그레이드의 영향을 받거나 덮어쓸 영역에 대한 특정 규칙을 위반합니다.

* 새 버전의 AEM과 역으로 호환되지 않으며 업그레이드 후 잠재적으로 중단될 수 있는 AEM 6.x 기능 또는 API를 사용합니다.

이 보고서는 Adobe Experience Manager(AEM) 6.5로의 업그레이드와 관련된 개발 노력에 대한 평가 역할로 사용됩니다.

>[!NOTE]
>
>패턴 감지기에 대한 자세한 내용은 [패턴 감지기를 사용한 업그레이드 복잡성 평가](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/upgrading/pattern-detector.html?lang=ko) 문서를 참조하십시오.

## 평가 실행 {#running}

패턴 감지기는 모든 환경에서 실행할 수 있습니다. 그러나 검색 속도를 높이고 비즈니스 크리티컬 인스턴스의 지연을 방지하기 위해 Cloud Manager는 작성자 인스턴스의 스테이징 환경에서 이 인스턴스를 실행합니다.

평가 보고서를 생성하려면 다음 단계를 수행하십시오.

1. [제품 업데이트 마법사](/help/product-update-wizard/overview.md)의 설명에 따라 마법사를 시작합니다.

1. **[!UICONTROL 평가 실행]**&#x200B;을 클릭합니다.

   ![평가 실행](/help/assets/Run-Evaluation.png)

1. 마법사가 작업 상태를 알려 줍니다. 평가 보고서가 생성되면 **진행 중** 또는 **완료됨**&#x200B;이 표시됩니다.

1. 보고서가 생성되면 **[!UICONTROL 보고서 다운로드]**&#x200B;를 클릭하여 사본을 저장할 수 있습니다.

   ![보고서 생성됨](/help/assets/Evaluation-1.png)

Cloud Manager에서 제품 업데이트 마법사의 현재 릴리스는 **평가** 단계만 지원합니다. 나머지 네 가지 단계인 **교정**, **실행**, **유효성 검사** 및 **완료**&#x200B;가 곧 제공될 예정입니다.
