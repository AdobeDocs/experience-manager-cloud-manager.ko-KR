---
title: 평가
seo-title: 평가
description: '이 페이지는 제품 업데이트 마법사에서 평가 단계를 위한 시작점 역할을 합니다. '
seo-description: 이 페이지는 제품 업데이트 마법사에서 평가 단계를 위한 시작점 역할을 합니다.
uuid: 62d68e79-c2ba-4d8b-ba7d-33709014d5b6
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
discoiquuid: ebcc91a5-be9e-4684-8146-d88f4013d4d1
translation-type: tm+mt
source-git-commit: ace032fbb26235d87d61552a11996ec2bb42abce
workflow-type: tm+mt
source-wordcount: '289'
ht-degree: 0%

---


# 평가 단계 {#evaluation}

제품 업데이트 마법사의 첫 번째 단계는 **[!UICONTROL Evaluation]** 단계입니다.
마법사에서 직접 액세스할 수 있는 패턴 탐지기를 사용하여 업그레이드 복잡성을 평가할 수 있습니다. 이 단계가 끝나면 평가 보고서에 액세스할 수 있습니다.

생성된 보고서를 사용하면 다음과 같은 패턴을 감지하여 작성자 인스턴스를 확인하여 업그레이드할 수 있습니다.

* 특정 규칙을 위반하고 업그레이드로 인해 영향을 받거나 덮어쓸 영역에서 수행됩니다.

* 새 AEM에서 역호환하지 않는 AEM 6.x 기능 또는 API를 사용하고 업그레이드 후 언제든지 중단할 수 있습니다.

이는 Adobe Experience Manager(AEM) 6.5로 업그레이드하는 데 관련된 개발 노력에 대한 평가 역할을 합니다.

>[!NOTE]
>
>패턴 탐지기에 대한 자세한 내용은 패턴 탐지기 [를 사용한 업그레이드 복잡성 평가를 참조하십시오.](https://helpx.adobe.com/experience-manager/6-4/sites/deploying/using/pattern-detector.html)

## 평가기 실행 {#running-evaluator}

아래 절차에 따라 평가 보고서를 생성합니다.

1. 을 클릭합니다 **[!UICONTROL Run Evaluation]**.

   >[!NOTE]
   >패턴 탐지기는 모든 환경에서 실행될 수 있습니다. 하지만 중요한 비즈니스 인스턴스에 대한 감지 비율을 높이고 속도 저하를 방지하기 위해 Cloud Manager는 작성 인스턴스의 스테이징 환경에서 이 인스턴스를 실행합니다.

   ![](assets/Run-Evaluation.png)

1. 마법사가 작업 상태를 알려줍니다. 귀하는 평가 보고서 **가 생성되면** 진행 **중이거나** 완료되었음을알 수 있습니다.

   보고서가 생성되면 아이콘을 클릭하여 복사본 **[!UICONTROL Download report]** 을 저장할 수 있습니다.

   ![](assets/Evaluation-1.png)


   >[!NOTE]
   >
   >Cloud Manager의 현재 제품 업데이트 마법사는 **평가** 단계만 지원합니다. 다른 4단계, 즉 **교정**, **실행**, **검증**&#x200B;및 **완료** 가곧 출시됩니다.
