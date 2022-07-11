---
title: 평가 단계
seo-title: Evaluation Phase
description: 제품 업데이트 마법사의 평가 단계에서 패턴 탐지기로 업그레이드 복잡성을 평가하는 방법을 알아봅니다.
exl-id: 1ffcbc21-dc36-435d-b83b-0209f81a15e7
source-git-commit: ce2145da3b9e605e8a41bac28df520f14e255557
workflow-type: tm+mt
source-wordcount: '291'
ht-degree: 0%

---


# 평가 단계 {#evaluation}

제품 업데이트 마법사의 첫 번째 단계는 다음과 같습니다 **[!UICONTROL Evaluation]** 단계 - 마법사 내에서 직접 패턴 탐지기와 업그레이드 복잡도를 평가합니다. 이 단계를 마치면 평가 보고서에 액세스할 수 있습니다.

생성된 보고서를 사용하면 다음과 같은 패턴을 감지하여 작성자 인스턴스에서 업그레이드 자격 조건을 확인할 수 있습니다.

* 업그레이드에 의해 영향을 받거나 덮어쓸 영역에 대한 특정 규칙을 위반합니다.

* AEM 6.x 기능 또는 새 AEM 버전과 호환되지 않으며 업그레이드 후 중단될 수 있는 API를 사용하십시오.

이 보고서는 AEM(Adobe Experience Manager) 6.5로 업그레이드하는 작업에 대한 평가 역할을 합니다.

>[!NOTE]
>
>패턴 탐지기에 대한 자세한 내용은 문서를 참조하십시오 [패턴 탐지기를 사용하여 업그레이드 복잡성 평가](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/upgrading/pattern-detector.html?lang=en)

## 평가 실행 {#running}

패턴 탐지기는 모든 환경에서 실행할 수 있습니다. 그러나 비즈니스 크리티컬 인스턴스의 감지율을 높이고 속도를 저하하지 않도록 작성자 인스턴스의 스테이징 환경에서 Cloud Manager가 실행합니다.

다음 단계에 따라 평가 보고서를 생성합니다.

1. 문서에 설명된 대로 마법사를 시작합니다 [제품 업데이트 마법사.](/help/product-update-wizard/overview.md)

1. 클릭 **[!UICONTROL Run Evaluation]**.

   ![평가 실행](/help/assets/Run-Evaluation.png)

1. 마법사가 작업 상태를 알려줍니다. 이 경우 **진행 중** 또는 **완료됨** 평가 보고서가 생성될 때 적용되는 것입니다.

1. 보고서가 생성되면 **[!UICONTROL Download report]** 복사본을 저장하려면 다음을 수행합니다.

   ![생성된 보고서](/help/assets/Evaluation-1.png)

Cloud Manager의 제품 업데이트 마법사의 현재 릴리스는 **평가** 페이지만 사용합니다. 다른 4단계 즉 **수정**, **실행**, **유효성 검사**, 및 **완료** 곧 올 겁니다.
