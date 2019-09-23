---
title: 평가
seo-title: 평가
description: '이 페이지는 제품 업데이트 마법사에서 평가 단계를 배우기 위한 시작점 역할을 합니다. '
seo-description: 이 페이지는 제품 업데이트 마법사에서 평가 단계를 배우기 위한 시작점 역할을 합니다.
uuid: 62d68e79-c2ba-4d8b-ba7d-33709014d5b6
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
discoiquuid: ebcc91a5-be9e-4684-8146-d88f4013d4d1
translation-type: tm+mt
source-git-commit: 9e33b90818c686f0b7aacaf0955c3f2eba05488f

---


# 평가 단계 {#evaluation}

제품 업데이트 마법사의 첫 번째 단계는 **[!UICONTROL Evaluation]** 단계입니다.
마법사에서 직접 액세스할 수 있는 패턴 탐지기를 사용하여 업그레이드 복잡성을 평가할 수 있습니다. 이 단계 끝에 평가 보고서에 액세스할 수 있습니다.

생성된 보고서를 사용하면 다음과 같은 패턴을 감지하여 작성자 인스턴스에서 업그레이드 가능성을 확인할 수 있습니다.

* 특정 규칙을 위반하고 업그레이드로 인해 영향을 받거나 덮어쓸 영역에서 수행됩니다.

* 새로운 AEM에서 역호환하지 않고 업그레이드 후 중단될 수 있는 AEM 6.x 기능 또는 API를 사용하십시오.

이는 Adobe Experience Manager(AEM) 6.5로 업그레이드하는 데 관련된 개발 노력의 평가입니다.

>[!NOTE]
>패턴 탐지기에 대한 자세한 내용은 패턴 [탐지기를 사용한 업그레이드 복잡성 평가를 참조하십시오.](https://helpx.adobe.com/experience-manager/6-4/sites/deploying/using/pattern-detector.html)

## 평가기 실행 {#running-evaluator}

아래 절차에 따라 평가 보고서를 생성합니다.

1. 을 **[!UICONTROL Run Evaluation]**&#x200B;클릭합니다.

   >[!NOTE]
   >패턴 탐지기는 모든 환경에서 실행될 수 있습니다. 하지만 중요한 비즈니스 인스턴스에서 감지 비율을 높이고 속도 저하를 방지하기 위해 Cloud Manager는 작성자 인스턴스의 스테이징 환경에서 실행됩니다.

   ![](assets/Run-Evaluation.png)

1. 마법사가 작업 상태를 알려줍니다. 평가 보고서가 **생성되면** 진행 중이거나 **완료된** 것을 알 수 있습니다.

   보고서가 생성되면 아이콘을 클릭하여 복사본을 저장할 **[!UICONTROL Download report]** 수 있습니다.

   ![](assets/Evaluation-1.png)


>[!NOTE]
>Cloud Manager의 현재 제품 업데이트 마법사는 평가 **단계만** 지원합니다. 다른 4단계( **교정**, **실행**, **유효성**&#x200B;검사 **및** 완료)는곧 제공될 예정입니다.
