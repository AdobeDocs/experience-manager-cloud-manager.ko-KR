---
title: 평가
seo-title: 평가
description: '이 페이지는 제품 업데이트 마법사에서 학습 평가 단계를 위한 시작점으로 사용됩니다. '
seo-description: 이 페이지는 제품 업데이트 마법사에서 학습 평가 단계를 위한 시작점으로 사용됩니다.
uuid: 62 d 68 E 79-C 2 BA -4 D 8 B-BA 7 D -33709014 D 5 B 6
contentOwner: Jsyal
products: sg_ Experiencemanager/Cloudmanager
discoiquuid: Ebcc 91 a 5-BE 9 E -4684-8146-D 88 F 4013 D 4 D 1
translation-type: tm+mt
source-git-commit: 2fda16bb4826171c993ec07c7ff3e38d1675b9f5

---


# Evaluation Phase {#evaluation}

Once you click **[!UICONTROL Start Update]**, the first phase in Product Update Wizard is the Evaluation phase. 이 단계에서는 마법사에서 바로 액세스할 수 있는 패턴 감지기를 사용하여 업그레이드 복잡성을 평가할 수 있습니다. 이 단계가 끝나면 평가 보고서에 액세스할 수 있습니다.

생성된 보고서를 사용하면 다음과 같은 패턴을 감지함으로써 업그레이드 인스턴스의 작성자 인스턴스를 확인할 수 있습니다.

* 특정 규칙이 위반되며 업그레이드가 영향을 받거나 덮어쓰는 영역에서 수행됩니다.

* AEM 6. x 기능 또는 API가 새로운 AEM에서 역호환되지 않으며 업그레이드 후 잠재적으로 중단할 수 있는 API를 사용합니다.


이는 AEM (Adobe Experience Manager) 6.5로 업그레이드하기 위한 개발 노력에 대한 평가 역할을 합니다.

>[!NOTE]
>To learn more about pattern detector, refer to [Assessing the Upgrade Complexity with the Pattern Detector](https://helpx.adobe.com/experience-manager/6-4/sites/deploying/using/pattern-detector.html)

## Running the Evaluator {#running-evaluator}

아래 절차에 따라 평가기를 실행합니다.

1. Select **[!UICONTROL Run Evaluation]** to run the pattern detector. 패턴 탐지는 모든 환경에서 실행할 수 있습니다. 하지만, 감지 비율을 늘리고 비즈니스 중요한 인스턴스에 대한 느린 속도를 방지하기 위해 클라우드 관리자는 작성자 인스턴스의 스테이징 환경에서 이를 실행합니다.

![](assets/Run-Evaluation.png)

1. 마법사가 작업 상태를 알려줍니다. You will notice **In progress** or **completed** as applicable when the evaluation report is being generated.

Once the report is generated, you can select [!UICONTROL Download] to save a copy of the evaluation report.

![](assets/Evaluation-1.png)

>[!NOTE]
>The other four phases succeeding **Evaluation** namely **Remediation**, **Execution**, **Validation**, and **Completion** are coming soon and are not available in the current release.
