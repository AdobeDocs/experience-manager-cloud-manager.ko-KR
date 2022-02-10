---
title: CI/CD 파이프라인
seo-title: CI/CD Pipeline
description: Cloud Manager의 스테이지 및 프로덕션에 대한 배포를 처리하는 CI/CD 파이프라인에 대한 개요
seo-description: Follow this section to learn about the CI/CD pipeline, which handles deployments to stage and production in Cloud Manager
uuid: 763ddb24-05cd-463f-8d72-a2e69bbe6b7e
topic-tags: introduction
discoiquuid: 1cdb76eb-1a91-4689-8579-0fa9fccc0592
feature: CI-CD Pipeline
exl-id: 7130e5b7-6986-48c8-900c-90f3e4187f91
source-git-commit: 4f0e1d163001fd18cfa838256c813152d65c3b4c
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# CI/CD 파이프라인 {#ci-cd-pipeline}

## 파이프라인 개요 {#pipeline-overview}

[!UICONTROL Cloud Manager] 구현 팀이 새 코드 또는 업데이트된 코드를 신속하게 테스트하고 전달할 수 있는 CI(Continuous Integration) 및 CD(Continuous Delivery) 프레임워크를 포함합니다. 예를 들어 구현 팀은 Adobe 코딩 모범 사례를 활용하여 완벽한 코드 검사를 수행하고 최상의 코드 품질을 보장하는 자동화된 CI/CD 파이프라인을 설정, 구성 및 시작할 수 있습니다.

또한 CI/CD 파이프라인은 장치 및 성능 테스트 프로세스를 자동화하여 배포 효율성을 높이고 배포 후 수정하기 위해 비용이 많이 드는 중요한 문제를 능동적으로 식별합니다. 구현 팀은 코드가 프로덕션에 배포되는 경우 포괄적인 코드 성과 보고서에 액세스하여 KPI에 대한 잠재적 영향 및 중요한 보안 유효성 검사에 대한 가시성을 얻을 수 있습니다.

## 파이프라인 프로세스 {#pipeline-process}

다음 다이어그램은에서 릴리스가 트리거되면 발생하는 일을 보여줍니다. [!UICONTROL Cloud Manager]. 함께 제공되는 표에서는 워크플로우의 각 단계에 대해 설명합니다.

![](assets/screen_shot_2018-05-30at82457pm.png)

다음 표에서는 프로세스의 각 단계에서 수행되는 작업을 자세히 설명합니다.

| 파이프라인 프로세스 단계 | 무슨 일이야? |
|---|---|
| 1. 릴리스 시작 | 배포 관리자는 Git 커밋을 사용하거나 되풀이하는 일정을 기반으로 하여 수동으로 릴리스를 트리거합니다. |
| 2. 릴리스 태그 만들기 | [!UICONTROL Cloud Manager] 자동으로 생성된 버전 번호를 사용하여 릴리스를 표시하는 Git 태그를 만듭니다. 예: 2018.531.245527.0000001222 |
| 3. 자동 생성 버전으로 빌드됨 | [!UICONTROL Cloud Manager] 새로 할당된 버전 번호로 애플리케이션을 빌드합니다. |
| 4. 코드 품질 평가 | [!UICONTROL Cloud Manager] 소스 코드를 검색하고 코드를 스테이지 환경에 배포하기 전에 요약을 제공합니다 |
| 5. 버전이 지정된 객체 저장 | 릴리스 객체는 배포 단계에서 나중에 사용하기 위해 저장됩니다. |
| 6. AMS AEM Stage에 대한 아티팩트의 자동 배포 | 릴리스 아티팩트는 스테이지 환경에 배포됩니다. |
| 7. 자동화된 테스트 트리거 | [!UICONTROL Cloud Manager] 객체에서 성능 및 보안 테스트를 실행합니다. |
| 8. 프로덕션 트리거 배포 | 자동화된 테스트가 완료되면 [!UICONTROL Cloud Manager] 프로덕션에 배포를 시작합니다. |
| 9. [!UICONTROL Cloud Manager] 배포할 아티팩트를 가져옵니다. | [!UICONTROL Cloud Manager] 저장된 릴리스 아티팩트를 가져옵니다. |
| 10. 프로덕션에 가공물 배포 | 릴리스 객체는 프로덕션 환경에 배포됩니다. |

### CI/CD 파이프라인을 설정하는 방법 {#how-to-setup-a-ci-cd-pipeline}

파이프라인 구성에 대한 자세한 내용은 문서를 참조하십시오 [프로덕션 파이프라인 구성](configuring-production-pipelines.md) 및 [비프로덕션 파이프라인 구성.](configuring-non-production-pipelines.md)

## 품질 게이트 {#quality-gates}

CI/CD 파이프라인은 코드를 스테이지 환경에서 배포 환경으로 이동하기 전에 충족해야 하는 품질 게이트 또는 수락 기준을 제공합니다. 파이프라인에는 세 개의 게이트가 있습니다.

* 코드 품질
* 성능 테스트
* 보안 테스트

이러한 각 게이트에 대해 세 가지 수준의 문제가 식별됩니다.

* **중요** - 게이트에서 식별한 문제로 인해 파이프라인이 즉시 실패합니다.
* **중요 사항** - 파이프라인이 일시 중지된 상태로 들어가는 게이트로 식별되는 문제 배포 관리자, 프로젝트 관리자 또는 비즈니스 소유자는 파이프라인이 진행되는 경우 문제를 무시하거나 문제를 수락할 수 있습니다. 이 경우 파이프라인이 오류로 중단됩니다.
* **정보** - 순전히 정보용으로 제공되며 파이프라인 실행에 영향을 주지 않는 게이트에서 식별되는 문제

다음은 코드에 대해 식별된 문제가 있는 코드 검사의 예입니다.

![](assets/quality-gate-failed.png)

### 게이트를 설정하는 방법 {#how-to-setup-gates}

문서를 참조하십시오 [프로덕션 파이프라인 구성](configuring-production-pipelines.md) 코드, 품질 및 성능 게이트 설정에 대한 자세한 내용은
