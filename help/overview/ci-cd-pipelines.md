---
title: CI/CD 파이프라인
description: CI/CD 파이프라인과 Cloud Manager에서 스테이징 및 프로덕션 환경에 대한 배포를 처리하는 방법에 대해 알아보십시오.
exl-id: 7130e5b7-6986-48c8-900c-90f3e4187f91
TQID: https://experienceleague.adobe.com/BwkZH2MIbXrzSxf0yk9yeDZZIpw7-Ldue-OPQPkWrdg
product_v2: id: c68cd75e-5bca-4bc3-a60e-9e183f816441id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2: id: cd2426f1-5719-4006-b8c2-738e5969754bid: ff09c71c-26a9-449a-85f8-2aeb8ce96100
subfeature_v2: id: c14b2f98-ee16-4c49-b87b-919c91b01d9d
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
topic_v2: id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87cid: d095671a-1355-40aa-8b5f-06c33c68080b
source-git-commit: badb64b816e83ca08a39b2b39eda13335f6a3c1d
workflow-type: tm+mt
source-wordcount: 1091
ht-degree: 51%

---

# CI/CD 파이프라인 {#ci-cd-pipeline}

CI/CD 파이프라인과 Cloud Manager에서 스테이징 및 프로덕션 환경에 대한 배포를 처리하는 방법에 대해 알아보십시오.

## 개요 {#overview}

[!UICONTROL Cloud Manager]에는 CI/CD(지속적 통합 및 지속적 게재) 프레임워크가 포함되어 있어 구현 팀이 새로운 코드 또는 업데이트된 코드를 신속하게 테스트하고 제공할 수 있습니다. 구현 팀은 자동화된 CI/CD 파이프라인을 설정, 구성 및 시작할 수 있습니다. 이 파이프라인은 포괄적인 코드 스캔을 수행하고 최고의 코드 품질을 보장하기 위해 Adobe 코딩 모범 사례를 따릅니다.

또한 CI/CD 파이프라인은 장치 및 성능 테스트 프로세스를 자동화하여 배포 효율성을 높이고 배포 후 수정 비용이 많이 드는 중요한 문제를 사전에 파악합니다. 구현 팀은 포괄적인 코드 성능 보고서에 액세스하여 코드가 프로덕션 환경에 구현될 경우 KPI에 미칠 수 있는 영향과 중요한 보안 검증에 대한 가시성을 확보할 수 있습니다.

## 파이프라인 프로세스 정보 {#pipeline-process}

다음 다이어그램은 [!UICONTROL Cloud Manager]에서 파이프라인을 사용하여 릴리스가 트리거되면 발생하는 작업을 보여 줍니다.

![파이프라인 프로세스](/help/assets/screen_shot_2018-05-30at82457pm.png)

| 파이프라인 단계 | 설명 |
| --- | --- |
| &#x200B;1. 릴리스 시작 | 배포 관리자는 수동으로, Git 커밋을 사용하여 또는 반복 예약을 기반으로 릴리스를 트리거합니다. |
| &#x200B;2. 릴리스 태그 만들기 | [!UICONTROL Cloud Manager]는 자동으로 생성된 버전 번호(예: `2018.531.245527.0000001222`)를 사용하여 릴리스를 표시하는 Git 태그를 생성합니다. |
| &#x200B;3. 자동 생성 버전을 사용하여 릴리스로 빌드 | [!UICONTROL Cloud Manager]는 새로 추가된 버전 번호로 애플리케이션을 빌드합니다. |
| &#x200B;4. 코드 품질 평가 | [!UICONTROL Cloud Manager]는 스테이징 환경에 코드를 배포하기 전에 소스 코드를 스캔하고 요약을 제공합니다. |
| &#x200B;5. 버전이 지정된 아티팩트가 저장됨 | 릴리스 아티팩트는 나중에 배포 단계에서 사용할 수 있도록 저장됩니다. |
| &#x200B;6. AMS AEM 스테이징에 아티팩트 자동 배포 | 릴리스 아티팩트는 스테이징 환경에 배포됩니다. |
| &#x200B;7. 자동화된 테스트 트리거 | [!UICONTROL Cloud Manager]는 아티팩트에 대한 성능 및 보안 테스트를 실행합니다. |
| &#x200B;8. 프로덕션 트리거 배포 | 자동화된 테스트가 완료되면 [!UICONTROL Cloud Manager]는 프로덕션에 배포를 시작합니다. |
| &#x200B;9. [!UICONTROL Cloud Manager]에서 배포할 아티팩트를 가져옵니다. | [!UICONTROL Cloud Manager]는 저장된 릴리스 아티팩트를 가져옵니다. |
| &#x200B;10. 프로덕션에 아티팩트 배포 | 릴리스 아티팩트는 프로덕션 환경에 배포됩니다. |

### 코드 소스 {#code-sources}

파이프라인은 프로덕션 및 비프로덕션 외에도 배포하는 코드 유형에 따라 다를 수 있습니다.

* **[전체 스택 파이프라인](#full-stack-pipeline)** - HTTPD/Dispatcher 구성과 함께 전체 AEM 애플리케이션 코드를 배포합니다.
* **[웹 계층 구성 파이프라인](#web-tier-config-pipelines)** - HTTPD/Dispatcher 구성만 배포합니다.

### 전체 스택 파이프라인 {#full-stack-pipeline}

전체 스택 파이프라인은 전체 AEM 애플리케이션 코드를 AEM 런타임에 배포하며 기본적으로 웹 계층 구성도 배포합니다.

다음 제한 사항이 적용됩니다.

* 파이프라인을 구성하거나 실행하려면 사용자가 **배포 관리자** 역할로 로그인해야 합니다.
* 언제든지 환경당 하나의 전체 스택 파이프라인만 있을 수 있습니다.

다음은 전체 스택 파이프라인이 [웹 계층 구성 파이프라인](#web-tier-config-pipelines)과 상호 작용하는 방법에 대해 설명합니다.

* 해당 웹 계층 구성 파이프라인이 있는 경우 환경에 대한 전체 스택 파이프라인은 Dispatcher 구성을 무시합니다.
* 환경에 해당하는 웹 계층 구성 파이프라인이 없는 경우 사용자는 Dispatcher 구성을 포함하거나 무시하도록 전체 스택 파이프라인을 구성할 수 있습니다.

전체 스택 파이프라인은 코드 품질 파이프라인 또는 배포일 수 있습니다.

#### 전체 스택 파이프라인 구성 {#configure-full-stack}

[프로덕션 파이프라인 추가](/help/using/production-pipelines.md#full-stack-code)를 참조하십시오.
[비프로덕션 파이프라인 추가](/help/using/non-production-pipelines.md#add-non-production-pipeline)를 참조하십시오.

### 웹 계층 구성 파이프라인 {#web-tier-config-pipelines}

웹 계층 구성 파이프라인을 사용하면 HTTPD/Dispatcher 구성을 AEM 런타임에 독점적으로 배포하여 다른 코드 변경과 분리할 수 있습니다. Dispatcher 구성 변경 사항만 배포하려는 사용자에게 단 몇 분 만에 신속하게 배포할 수 있는 가속화된 파이프라인입니다.

>[!TIP]
>
>웹 계층 구성 파이프라인을 사용하면 프로젝트 구조에 가장 적합한 것에 따라 웹 구성을 전체 스택 파이프라인과 동일하거나 다른 소스 위치에 저장할 수 있습니다.

다음 제한 사항이 적용됩니다.

* 파이프라인을 구성하거나 실행하려면 사용자가 **배포 관리자** 역할로 로그인해야 합니다.
* 언제든지 환경당 하나의 웹 계층 구성 파이프라인만 있을 수 있습니다.
* 해당 전체 스택 파이프라인이 실행 중일 때 사용자는 웹 계층 구성 파이프라인을 구성할 수 없습니다.

다음은 웹 계층 구성 파이프라인이 [전체 스택 파이프라인](#full-stack-pipeline)과(와) 상호 작용하는 방법에 대해 설명합니다.

* 웹 계층 구성 파이프라인이 환경에 대해 설정되지 않은 경우 사용자는 전체 스택 파이프라인을 구성하는 동안 Dispatcher 구성을 포함하거나 무시하도록 선택할 수 있습니다.
* 웹 계층 구성 파이프라인이 환경에 대해 구성되면 해당 전체 스택 파이프라인(있는 경우)은 실행 및 배포 중에 Dispatcher 구성을 무시합니다.
* 웹 계층 구성 파이프라인이 삭제되면 해당 전체 스택 파이프라인(있는 경우)이 실행 중에 Dispatcher 구성을 배포하도록 재설정됩니다.

>[!NOTE]
>
>파란색-녹색 배포가 활성화된 AMS 프로그램의 경우 웹 계층 업데이트는 기본적으로 롤링 배포를 사용합니다. 웹 계층 변경을 위해 파란색-녹색 배포가 필요한 경우 전체 스택 파이프라인을 사용합니다.

#### 웹 계층 파이프라인 구성 {#configure-web-tier}

[프로덕션 파이프라인 추가](/help/using/production-pipelines.md#web-tier-config)를 참조하십시오.
[비프로덕션 파이프라인 추가](/help/using/non-production-pipelines.md#add-non-production-pipeline)를 참조하십시오.

### 스마트 빌드를 사용한 더 빠른 빌드 {#use=smart-build}

이제 Cloud Manager에서는 **스마트 빌드**&#x200B;라는 최적화된 빌드 전략을 사용하는데, 이 전략에서는 모듈 수준 캐싱을 사용하여 빌드 프로세스의 속도를 높입니다. 각 빌드 동안 변경된 모듈만 다시 빌드되고 변경되지 않은 모듈은 캐시에서 재사용됩니다.

스마트 빌드는 코드 품질 및 개발 전체 스택 배포 파이프라인에만 사용할 수 있습니다.

[비프로덕션 파이프라인 추가](/help/using/non-production-pipelines.md#add-non-production-pipeline) 및 [비프로덕션 파이프라인에서의 스마트 빌드 사용 정보](/help/using/non-production-pipelines.md#about-smart-build)를 참조하십시오.


### CI/CD 파이프라인 설정 방법 {#how-to-setup-a-ci-cd-pipeline}

파이프라인 구성에 대한 자세한 내용은 [프로덕션 파이프라인 구성](/help/using/production-pipelines.md) 및 [비프로덕션 파이프라인 구성](/help/using/non-production-pipelines.md)을 참조하십시오.

## 품질 게이트 {#quality-gates}

CI/CD 파이프라인은 코드를 스테이징 환경에서 배포 환경으로 이동하기 전에 충족해야 하는 품질 게이트 또는 허용 기준을 제공합니다. 파이프라인에는 3개의 게이트가 있습니다.

* 코드 품질
* 성능 테스트
* 보안 테스트

이러한 각 게이트에 대해 식별할 수 있는 세 가지 수준의 문제가 있습니다.

* **심각** - 게이트에 의해 식별된 심각한 문제는 파이프라인의 즉각적인 실패를 초래합니다.
* **중요** - 게이트에 의해 식별된 중요한 문제는 파이프라인을 일시 중지 상태로의 전환을 초래합니다. 배포 관리자, 프로젝트 관리자 또는 비즈니스 소유자는 파이프라인을 계속 진행할 수 있도록 문제를 재정의할 수 있습니다. 또는 파이프라인이 오류로 중단되는 경우 문제를 수락할 수 있습니다.
* **정보** - 게이트에 의해 식별된 정보 문제는 순전히 정보 제공 목적으로 제공되며 파이프라인 실행에 영향을 미치지 않습니다.

다음은 문제가 식별된 코드 스캔의 예입니다.

![코드 스캔 예](/help/assets/quality-gate-failed.png)

### 게이트 설정 방법 {#how-to-setup-gates}

코드, 품질 및 성능 게이트 설정에 대한 자세한 내용은 [프로덕션 파이프라인 구성](/help/using/production-pipelines.md) 문서를 참조하십시오.
