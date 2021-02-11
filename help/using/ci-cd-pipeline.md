---
title: CI/CD 파이프라인
seo-title: CI/CD 파이프라인
description: Cloud Manager의 스테이지 및 프로덕션에 대한 배포를 처리하는 CI/CD 파이프라인 개요
seo-description: Cloud Manager의 스테이지 및 프로덕션에 대한 배포를 처리하는 CI/CD 파이프라인에 대해 알아보려면 이 섹션을 따르십시오
uuid: 763ddb24-05cd-463f-8d72-a2e69bbe6b7e
topic-tags: introduction
discoiquuid: 1cdb76eb-1a91-4689-8579-0fa9fccc0592
translation-type: tm+mt
source-git-commit: 2dda85baa5e7ed9bfd8933df3580ec6fc3c210fd
workflow-type: tm+mt
source-wordcount: '546'
ht-degree: 1%

---


# CI/CD 파이프라인 {#ci-cd-pipeline}

## 파이프라인 개요 {#pipeline-overview}

[!UICONTROL Cloud Manager] 구현 팀이 새로운 코드 또는 업데이트된 코드를 신속하게 테스트하여 제공할 수 있는 CI(Continuous Integration) 및 CD(Continuous Delivery) 프레임워크가 포함되어 있습니다. 예를 들어 구현 팀은 Adobe 코딩 모범 사례를 활용하는 자동화된 CI/CD 파이프라인을 설정, 구성 및 시작하여 철저한 코드 검사를 수행하고 최고 코드 품질을 보장할 수 있습니다.

또한 CI/CD 파이프라인은 유닛 및 성능 테스트 프로세스를 자동화하여 배포 효율성을 높이고 배포 후 수정하기에 많은 비용이 소모되는 중요한 문제를 적극적으로 식별합니다. 구현 팀은 포괄적인 코드 성과 보고서를 이용하여 코드가 프로덕션에 배포될 경우 KPI에 미치는 잠재적 영향을 파악하고 중요한 보안 유효성 검사를 수행할 수 있습니다.

## 파이프라인 프로세스 {#pipeline-process}

다음 다이어그램은 [!UICONTROL Cloud Manager]에서 릴리스가 트리거되면 발생하는 상황을 보여줍니다. 함께 제공되는 표에서는 워크플로우의 각 단계에 대해 설명합니다.

![](assets/screen_shot_2018-05-30at82457pm.png)

다음 표에서는 각 프로세스 단계 중 진행 사항에 대해 자세히 설명합니다.

| 파이프라인 프로세스 단계 | 무슨 일이야? |
|---|---|
| 1. 릴리스 시작 | 배포 관리자는 Git 커밋을 사용하거나 반복 일정을 기반으로 릴리스를 수동으로 트리거합니다. |
| 2. 릴리스 태그 만들기 | [!UICONTROL Cloud Manager] 자동으로 생성된 버전 번호를 사용하여 릴리스를 표시하는 Git 태그를 만듭니다. 예:2018.531.245527.0000001222 |
| 3. 자동 생성된 버전으로 빌드된 릴리스 | [!UICONTROL Cloud Manager] 응용 프로그램을 새로 할당된 버전 번호로 만듭니다. |
| 4. 코드 품질 평가 | [!UICONTROL Cloud Manager] 소스 코드를 스캔하고 코드를 스테이지 환경에 배포하기 전에 요약을 제공합니다. |
| 5. 버전 관리 객체 | 릴리스 객체는 배포 단계에서 나중에 사용하도록 저장됩니다. |
| 6. AMS AEM Stage에 대한 가공물의 자동 배포 | 릴리즈 객체는 스테이지 환경에 배포됩니다. |
| 7. 자동 테스트 트리거 | [!UICONTROL Cloud Manager] 가공물에 대해 성능 및 보안 테스트를 실행합니다. |
| 8. 프로덕션 트리거 배포 | 자동화된 테스트가 완료되면 [!UICONTROL Cloud Manager]이(가) 프로덕션에 대한 배포를 시작합니다. |
| 9.[!UICONTROL Cloud Manager]은(는) 배포할 객체를 가져옵니다. | [!UICONTROL Cloud Manager] 저장된 릴리스 아티팩트를 가져옵니다. |
| 10. 제작에 대한 가공물 배포 | 릴리즈 객체는 프로덕션 환경에 배포됩니다. |

### CI/CD 파이프라인을 설정하는 방법 {#how-to-setup-a-ci-cd-pipeline}

파이프라인 구성에 대한 자세한 내용은 [파이프라인 구성](configuring-pipeline.md)을 참조하십시오.

## 품질 게이트 {#quality-gates}

CI/CD 파이프라인은 품질 게이트 또는 승인 기준을 제공하므로 코드를 스테이지 환경에서 배포 환경으로 이동하려면 먼저 충족해야 합니다. 파이프라인에는 세 개의 문이 있습니다.

* 코드 품질
* 성능 테스트
* 보안 테스트

이러한 각 문마다 세 가지 수준의 문제가 확인됩니다.

* **중요한**  - 파이프라인의 즉각적인 실패를 초래하는 게이트로 식별된 문제.
* **중요**  - 파이프라인이 일시 중지된 상태로 전환되는 게이트로 식별되는 문제 배포 관리자, 프로젝트 관리자 또는 비즈니스 소유자는 파이프라인이 진행되는 경우 문제를 무시하거나 해당 문제를 허용할 수 있습니다. 이 경우 파이프라인이 오류로 인해 중단됩니다.
* **정보**  - 정보 제공용으로만 제공되고 파이프라인 실행에 영향을 주지 않는 게이트로 식별되는 문제

다음은 코드에 대해 식별된 문제가 있는 코드 스캔의 예입니다.

![](assets/quality-gate-failed.png)

### {#how-to-setup-gates} 게이트를 설정하는 방법

코드, 품질 및 성능 게이트를 설정하는 방법에 대한 자세한 내용은 **[게이츠 구성](configuring-pipeline.md)**&#x200B;을 참조하십시오.
