---
title: 평가
seo-title: 평가
description: '이 페이지는 제품 업데이트 마법사에서 평가 단계 학습 시작점의 역할을 합니다. '
seo-description: 이 페이지는 제품 업데이트 마법사에서 평가 단계 학습 시작점의 역할을 합니다.
uuid: 62d68e79-c2ba-4d8b-ba7d-33709014d5b6
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
discoiquuid: ebcc91a5-be9e-4684-8146-d88f4013d4d1
feature: 시작하기
exl-id: 1ffcbc21-dc36-435d-b83b-0209f81a15e7
source-git-commit: 43bb3c477ef9c1ce178509b8180479d7616edc66
workflow-type: tm+mt
source-wordcount: '291'
ht-degree: 1%

---

# 평가 단계 {#evaluation}

제품 업데이트 마법사의 첫 번째 단계는 **[!UICONTROL Evaluation]** 단계입니다.
마법사에서 직접 액세스할 수 있는 패턴 탐지기를 사용하여 업그레이드 복잡도를 평가할 수 있습니다. 이 단계를 마치면 평가 보고서에 액세스할 수 있습니다.

생성된 보고서에서는 다음과 같은 패턴을 감지하여 작성자 인스턴스에서 업그레이드를 확인할 수 있습니다.

* 특정 규칙을 위반하고 업그레이드에 의해 영향을 받거나 덮어쓸 영역에서 수행됩니다.

* 새 AEM에서 이전 버전과 호환되지 않으며 업그레이드 후 중단될 수 있는 AEM 6.x 기능 또는 API를 사용하십시오.

AEM(Adobe Experience Manager) 6.5로 업그레이드하는 작업에 대한 평가 역할을 합니다.

>[!NOTE]
>
>패턴 탐지기에 대한 자세한 내용은 [패턴 탐지기를 사용하여 업그레이드 복잡성 평가](https://helpx.adobe.com/experience-manager/6-4/sites/deploying/using/pattern-detector.html)를 참조하십시오

## 평가기 {#running-evaluator} 실행

평가 보고서를 생성하려면 아래 절차를 따릅니다.

1. **[!UICONTROL Run Evaluation]**&#x200B;을 클릭합니다.

   >[!NOTE]
   >
   >패턴 탐지기는 모든 환경에서 실행할 수 있습니다. 하지만 검출율을 높이고 비즈니스 크리티컬 인스턴스의 속도를 저하하지 않도록 작성자 인스턴스의 스테이징 환경에서 Cloud Manager가 실행합니다.

   ![](assets/Run-Evaluation.png)

1. 마법사가 작업 상태를 알려줍니다. 평가 보고서가 생성될 때 적용 가능한 **진행 중** 또는 **완료**&#x200B;가 표시됩니다.

   보고서가 생성되면 **[!UICONTROL Download report]** 을 클릭하여 복사본을 저장할 수 있습니다.

   ![](assets/Evaluation-1.png)


   >[!NOTE]
   >
   >Cloud Manager의 제품 업데이트 마법사의 현재 릴리스는 **평가** 단계만 지원합니다. 다른 네 가지 단계 즉, **수정**, **실행**, **유효성 검사** 및 **완료**&#x200B;가 곧 제공될 예정입니다.
