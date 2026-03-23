---
title: 비프로덕션 파이프라인 추가
description: Cloud Manager를 사용하여 코드를 배포할 비프로덕션 파이프라인을 만들고 구성하는 방법에 대해 알아보십시오.
exl-id: ccf4b4a2-6e29-4ede-821c-36318b568e5c
source-git-commit: 2a022c10ce64bb42d4bffd63bea01de25af0bd41
workflow-type: tm+mt
source-wordcount: '1992'
ht-degree: 27%

---

# 비프로덕션 파이프라인 추가 {#configuring-non-production-pipelines}

Cloud Manager를 사용하여 코드를 배포할 비프로덕션 파이프라인을 만들고 구성하는 방법에 대해 알아보십시오. 먼저 Cloud Manager에서 파이프라인이 작동하는 방식에 대한 보다 개념적인 개요를 원하는 경우 [CI/CD 파이프라인](/help/overview/ci-cd-pipelines.md) 문서를 참조하십시오.

## 개요 {#overview}

[!UICONTROL Cloud Manager]의 **파이프라인** 타일을 사용하여 **배포 관리자**&#x200B;는 두 가지 유형의 파이프라인을 만들 수 있습니다.

* **프로덕션 파이프라인** - 프로덕션 파이프라인은 프로덕션으로 소스 코드를 가져오기 위한 일련의 조정된 단계로 구성된 특별히 빌드된 파이프라인입니다.
* **비프로덕션 파이프라인** - 비프로덕션 파이프라인은 주로 코드 품질 검사를 실행하거나 소스 코드를 개발 환경에 배포하는 역할을 합니다.

이 문서는 비프로덕션 파이프라인에 초점을 맞춥니다. 프로덕션 파이프라인을 구성하는 방법에 대한 자세한 내용은 [프로덕션 파이프라인 구성](/help/using/production-pipelines.md) 문서를 참조하십시오.

비프로덕션 파이프라인에는 두 가지 유형이 있습니다.

* **코드 품질 파이프라인** - Git 분기의 코드에 대해 코드 품질 스캔을 실행하고 빌드 및 코드 품질 단계를 실행합니다.
* **배포 파이프라인** - 이러한 파이프라인은 코드 품질 파이프라인과 같은 빌드 및 코드 품질 단계를 실행하는 것 외에도 코드를 비프로덕션 환경에 배포합니다.

>[!NOTE]
>
>연결된 Git 저장소에 분기가 하나 이상 있고 [프로그램 설정](/help/getting-started/program-setup.md)이 완료될 때까지 파이프라인을 설정할 수 없습니다. Cloud Manager에서 저장소를 추가하고 관리하는 방법은 [Cloud Manager 저장소](/help/managing-code/managing-repositories.md)를 참조하십시오.

## 새 비프로덕션 파이프라인 추가 {#add-non-production-pipeline}

Cloud Manager UI에서 프로그램 및 하나 이상의 환경을 설정한 후 비프로덕션 파이프라인을 추가할 수 있습니다. 프로덕션 환경에 배포하기 전에 이러한 파이프라인을 사용하여 코드 품질을 테스트합니다.

1. [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com)에서 Cloud Manager에 로그인한 다음 적절한 조직과 프로그램을 선택합니다.

1. Cloud Manager 홈 화면에서 파이프라인 카드에 액세스합니다. **추가**&#x200B;를 클릭한 후 **비프로덕션 파이프라인 추가**&#x200B;를 선택합니다.

   ![비프로덕션 파이프라인 추가](/help/assets/configure-pipelines/nonprod-pipeline-add1.png)

1. **비프로덕션 파이프라인 추가** 대화 상자의 **구성** 탭에서 만들 파이프라인 유형 중 하나를 선택합니다.

   * **코드 품질 파이프라인** - 환경에 배포하지 않고 코드를 빌드하고 단위 테스트를 실행하고 코드 품질을 평가하는 파이프라인을 만듭니다.
   * **배포 파이프라인** - 코드를 빌드하고, 단위 테스트를 실행하고, 코드 품질을 평가하고, 환경에 배포하는 파이프라인을 만듭니다.

   ![파이프라인 유형 선택](/help/using/assets/add-non-production-pipeline-cm-ams.png)

>[!BEGINTABS]

>[!TAB 코드 품질 파이프라인 - 구성 탭]

| 섹션 | 옵션 | 설명 |
| --- | --- | --- |
| **파이프라인 구성** | **비프로덕션 파이프라인 이름** | **비프로덕션 파이프라인 이름** 필드에 파이프라인에 대한 설명을 입력합니다. |
|  | **테스트** | 비프로덕션 파이프라인을 편집할 때만 표시됩니다.<br>UI는 코드 품질 유효성 검사의 일부로 파이프라인이 실행하는 테스트 범주를 표시합니다.<ul><li>**정적 코드 테스트** - 품질 및 수정 문제에 대한 코드를 분석합니다.<li>**로드/성능 테스트** - 파이프라인 테스트의 일부로 성능 관련 동작을 평가합니다.<li>**보안 테스트** - 코드 및 파이프라인 출력에 보안 관련 문제가 있는지 확인합니다. |
| **배포 옵션** | **배포 트리거** | <ul><li>**수동** - 파이프라인을 수동으로 시작할 수 있습니다.<li>**Git 변경 시** - 구성된 Git 분기에 커밋이 추가될 때 파이프라인을 시작합니다. 이 옵션을 사용하면 필요에 따라 파이프라인을 수동으로 시작할 수 있습니다. |
|  | **중요한 지표 오류 동작** | <ul><li>**매번 묻기** - 이 비헤이비어는 기본 설정이며 중요한 장애에 대해 수동 개입이 필요합니다.<li>**즉시 실패** - 이 옵션을 선택하면 중요한 오류가 발생할 때마다 파이프라인이 취소됩니다. 각 실패를 수동으로 거부하는 사용자를 에뮬레이션합니다.<li>**즉시 계속** - 이 옵션을 선택하면 중요한 오류가 발생할 때마다 파이프라인이 자동으로 진행됩니다. 기본적으로 각 실패를 수동으로 승인하는 사용자를 에뮬레이션합니다.</li></ul> |
|  | **단계 배포 후 승인** 확인란 | 비프로덕션 파이프라인을 편집할 때만 표시됩니다.<br>파이프라인을 계속하려면 스테이징 환경으로 배포한 후 승인을 요구하려면 이 옵션을 선택하십시오. 이 옵션을 선택하지 않으면 구성된 동작에 따라 파이프라인이 계속 진행됩니다. |

>[!TAB 배포 파이프라인 - 구성 탭]

| 섹션 | 옵션 | 설명 |
| --- | --- | --- |
| **파이프라인 구성** | **비프로덕션 파이프라인 이름** | **비프로덕션 파이프라인 이름** 필드에 파이프라인에 대한 설명을 입력합니다. |
|   | **적합한 배포 환경** | 파이프라인이 배포 파이프라인인 경우 Cloud Manager에서 코드를 배포하는 환경을 선택해야 합니다. |
|   | **테스트** | 비프로덕션 파이프라인을 편집할 때만 표시됩니다.<br>UI는 코드 품질 유효성 검사의 일부로 파이프라인이 실행하는 테스트 범주를 표시합니다.<ul><li>**정적 코드 테스트** - 품질 및 수정 문제에 대한 코드를 분석합니다.<li>**로드/성능 테스트** - 파이프라인 테스트의 일부로 성능 관련 동작을 평가합니다.<li>**보안 테스트** - 코드 및 파이프라인 출력에 보안 관련 문제가 있는지 확인합니다.</li></ul> |
| **배포 옵션** | **배포 트리거** | <ul><li>**수동** - 파이프라인을 수동으로 시작할 수 있습니다.<li>**Git 변경 시** - 구성된 Git 분기에 커밋이 추가될 때 파이프라인을 시작합니다. 이 옵션을 사용하면 필요에 따라 파이프라인을 수동으로 시작할 수 있습니다. |
|   | **중요한 지표 오류 동작** | <ul><li>**매번 묻기** - 기본 설정이며 중요한 지표가 실패하면 진행 방법을 결정하라는 메시지를 표시합니다.<li>**즉시 실패** - 중요한 지표가 실패할 때마다 파이프라인이 취소됩니다. 이는 본질적으로 각 실패를 수동으로 거부하는 사용자를 에뮬레이션하는 것입니다.<li>**즉시 계속** - 중요한 지표가 실패할 때마다 파이프라인이 자동으로 진행됩니다. 이는 본질적으로 각 실패를 수동으로 승인하는 사용자를 에뮬레이션하는 것입니다.</li></ul> |
|  | **단계 배포 후 승인** 확인란 | 비프로덕션 파이프라인을 편집할 때만 표시됩니다.<br>파이프라인을 계속하려면 스테이징 환경으로 배포한 후 승인을 요구하려면 이 옵션을 선택하십시오. 이 옵션을 선택하지 않으면 구성된 동작에 따라 파이프라인이 계속 진행됩니다. |
|  | **부하 분산 장치 변경 건너뛰기** 확인란 | 배포 중에 파이프라인이 로드 밸런서를 변경하지 않도록 하려면 이 옵션을 선택합니다. |
|  | **Dispatcher 구성** | **배포 관리자** 역할은 파이프라인이 실행될 때 AEM Dispatcher 캐시에서 무효화되거나 플러시된 콘텐츠 경로 집합을 구성할 수 있습니다. 이러한 캐시 액션은 콘텐츠 패키지가 배포된 직후에 배포 파이프라인 단계의 일부로 수행됩니다. 이러한 설정은 표준 AEM Dispatcher 비헤이비어를 사용합니다. `Dispatcher`을(를) 구성하려면 다음 작업을 수행하십시오.<ul><li>**PATH**&#x200B;에서 파이프라인을 초기화하거나 무효화할 콘텐츠 경로를 제공하십시오.<li>**유형** 아래에서 해당 경로에 대해 수행할 액션을 선택합니다.<ul><li>**플러시** - 지정된 경로에서 캐시 삭제를 수행합니다.</li><li>**무효화** - 저작 인스턴스에서 게시 인스턴스로 콘텐츠가 활성화된 경우와 유사하게 캐시 무효화를 수행합니다.</li><li>**경로 추가**&#x200B;를 클릭하여 지정된 경로를 추가합니다. 환경당 최대 100개의 경로를 추가할 수 있습니다.</li></ul> |
| **파이프라인** | **경험 감사** 확인란 | 파이프라인에 경험 감사 단계를 포함하려면 이 옵션을 선택합니다. 활성화되면 Source 코드 탭 뒤에 파이프라인에 경험 감사 단계가 포함됩니다. |

>[!ENDTABS]

1. **비프로덕션 파이프라인 추가** 대화 상자의 오른쪽 아래 모서리에서 **계속**&#x200B;을 클릭합니다.
1. 파이프라인이 빌드하고 배포하도록 구성된 코드 유형을 선택합니다.

>[!BEGINTABS]

>[!TAB Source 코드 탭 - 전체 스택 코드]

애플리케이션 코드 및 기본적으로 웹 계층 구성을 포함한 전체 AEM 애플리케이션을 배포합니다.

| 섹션 | 옵션 | 설명 |
| --- | --- | --- |
| **Source 코드** | **저장소** | 드롭다운 목록에서 파이프라인이 소스로 사용하는 Git 저장소를 선택합니다. Cloud Manager은 여기에서 선택한 저장소에서 코드를 빌드합니다. |
|   | **Git 분기** | 드롭다운 목록에서 선택한 저장소에서 파이프라인을 빌드할 분기를 선택합니다. 기본값은 `main`입니다. 파이프라인은 선택한 분기를 빌드 및 배포의 소스로 사용합니다. 필요한 경우 **새로 고침**&#x200B;을 클릭하여 선택한 저장소에 대해 사용 가능한 분기 목록을 업데이트합니다. 최근에 만든 분기가 목록에 표시되지 않는 경우 이 옵션을 사용합니다. |
|   | **전략 작성** | <ul><li>**전체 빌드** - 매번 저장소의 모든 모듈을 빌드합니다.<li>BETA **스마트 빌드** - 마지막 커밋 이후 변경된 모듈만 빌드합니다.<br>비프로덕션 파이프라인에서 [스마트 빌드 사용에 대해 자세히 알아보세요](#about-smart-build).</li></ol>**중요**: 스마트 빌드는 코드 품질 파이프라인 및 개발 전체 스택 코드 배포 파이프라인에만 사용할 수 있습니다. |
|   | **웹 계층 구성 무시** 확인란 | 전체 스택 코드 파이프라인에서 웹 계층 구성의 배포를 건너뛰려면 이 옵션을 선택합니다. 파이프라인 코드와 함께 웹 계층 구성을 배포하려면 옵션을 선택하지 않은 상태로 두십시오. |
| **파이프라인** | **경험 감사** 확인란 | 파이프라인에 경험 감사 단계를 포함하려면 이 옵션을 선택합니다. 활성화되면 Source 코드 탭 뒤에 파이프라인에 경험 감사 단계가 포함됩니다. |

>[!TAB Source 코드 - 웹 계층 구성]

웹 페이지를 저장, 처리 및 클라이언트에 전달하는 데 사용되는 Dispatcher 속성과 같은 웹 계층 구성만 배포합니다. **웹 계층 구성**&#x200B;을 선택하면 Cloud Manager에서 웹 계층 구성 배포 전용 파이프라인을 만듭니다.

전체 스택 파이프라인이 이미 있는 경우 Cloud Manager은 웹 계층 구성 파이프라인을 생성하면 기존 전체 스택 파이프라인이 웹 계층 구성을 무시한다는 알림을 표시합니다. 웹 계층 구성 파이프라인을 만든 후 Cloud Manager은 전체 스택 파이프라인 대신 해당 파이프라인을 통해 웹 계층 구성 배포를 관리합니다.

| 섹션 | 옵션 | 설명 |
| --- | --- | --- |
| **Source 코드** | **저장소** | 드롭다운 목록에서 웹 계층 구성이 포함된 Git 저장소를 선택합니다. |
|   | **Git 분기** | 선택한 저장소에서 Cloud Manager이 배포에 사용하는 분기를 선택합니다. 필요한 경우 **새로 고침**&#x200B;을 클릭하여 선택한 저장소에 대해 사용 가능한 분기 목록을 업데이트합니다. 최근에 만든 분기가 목록에 표시되지 않는 경우 이 옵션을 사용합니다. |
|   | **코드 위치** | 배포할 웹 계층 구성이 포함된 선택한 저장소의 경로를 입력합니다. 기본 위치는 저장소 루트(`/`)입니다. |

>[!ENDTABS]

1. **저장**&#x200B;을 클릭합니다.

## 비프로덕션 파이프라인에서의 Smart Build 사용 정보{#about-smart-build}

Cloud Manager의 **스마트 빌드**&#x200B;는 비프로덕션 파이프라인에 최적화된 빌드 전략입니다. 스마트 빌드는 모듈을 캐시하고 마지막으로 성공한 실행 이후 변경된 모듈만 다시 빌드하여 빌드 시간을 줄입니다. 변경되지 않은 모듈은 캐시에서 재사용되는 반면 수정된 모듈 및 그 의존성만 재구축되므로 반복적인 개발 워크플로의 효율성을 향상시킵니다.

스마트 빌드는 현재 다음에 대해서만 사용할 수 있습니다.

* 코드 품질 파이프라인.
* 개발 전체 스택 배포 파이프라인.

>[!NOTE]
>
>Smart Build를 활성화한 후 첫 번째 실행은 캐시가 비어 있으므로 전체 빌드와 같이 작동합니다.

다음과 같은 경우에는 스마트 빌드를 사용하는 것이 좋습니다.
* 빈번한 증분 변경을 적극적으로 개발하고 커밋하고 있습니다.
* 프로젝트에 여러 Maven 모듈이 포함되어 있습니다.
* 전체 빌드는 시간이 오래 걸립니다.

다음과 같은 경우에는 스마트 빌드가 항상 이상적이지 않습니다.
* 빌드는 Maven의 종속성 그래프 외부에서 작업을 수행하는 플러그인에 크게 의존합니다.
* 모든 실행 시 전체 재구축 유효성 검사가 필요합니다.

### 빌드 성능 이해{#smart-build-performance}

Smart Build를 사용하여 얻을 수 있는 성능 이익은 다음을 포함한 몇 가지 요인에 따라 달라집니다.

* 프로젝트의 모듈 수입니다.
* 코드 변경 빈도 및 범위입니다.
* 모듈 간 종속성 분포.

일반적으로 많은 독립 모듈이 있는 프로젝트는 가장 큰 개선 효과를 볼 수 있습니다.

### 모듈별 캐시 옵트아웃{#smart-build-cache-optout}

Smart Build에서는 특정 모듈에 대한 캐싱을 비활성화할 수 있는 세분화된 제어를 제공합니다. 이 기능은 특정 모듈이 다음과 같은 경우 유용합니다.

* `exec-maven-plugin` 또는 `maven-antrun-plugin`과(와) 같은 플러그인을 사용합니다.
* Maven 종속성으로 추적되지 않는 파일 작업을 수행합니다.
* 캐시될 때 일관되지 않은 결과를 생성합니다.

### 모듈에 대한 캐싱 비활성화{#smart-build-disable-caching}

영향을 받는 모듈의 `pom.xml`에 다음 속성을 추가할 수 있습니다.

```xml
<properties>
  <maven.build.cache.enabled>false</maven.build.cache.enabled>
</properties>
```

이 구문은 모듈이 모든 파이프라인 실행에 대해 다시 빌드되도록 하는 반면 다른 모듈은 캐싱의 이점을 계속 사용합니다.

### Smart Build 사용 시 제한 사항 및 고려 사항{#smart-build-limitations}

Smart Build를 사용할 때는 다음 사항에 유의하십시오.

* Smart Build는 Maven 종속성 분석을 사용합니다.
* 종속성 그래프 외부의 변경 사항은 재빌드를 트리거하지 않을 수 있습니다.
* 일부 플러그인은 캐싱과 완전히 호환되지 않을 수 있습니다.
* 비프로덕션 파이프라인을 편집하여 언제든지 **전체 빌드**(으)로 다시 전환할 수 있습니다.

예기치 않은 빌드 동작이 발생하면 특정 모듈에 대해 캐싱을 사용하지 않도록 설정하거나 빌드 전략을 **전체 빌드**(으)로 일시적으로 전환해 보십시오.

### 스마트 빌드 문제 해결{#smart-build-troubleshoot}

| 문제 | 제안된 해결 방법 |
| --- | --- |
| 빌드 결과가 일관되지 않음 | · 영향을 받는 모듈에 대한 캐싱을 비활성화합니다.<br>· 플러그 인 동작(특히 `exec`/`antrun` 플러그 인)을 확인합니다. |
| 성능 향상 없음 | · 여러 번 실행되었는지 확인합니다(캐시 준비).<br>· 대부분의 모듈이 자주 변경되는지 확인합니다. |
| 예기치 않은 아티팩트 또는 누락된 변경 사항 | · 변경 내용이 Maven 종속성 추적을 벗어나는지 확인하십시오.<br>· 확인에는 **전체 빌드**&#x200B;를 사용하십시오. |

스마트 빌드를 사용하려면 [비프로덕션 파이프라인 추가](#add-non-production-pipeline)를 참조하십시오.



<!-- 
1. If you chose to add a **Deployment Pipeline**, select the target deployment environment from the **Eligible Deployment Environments** dropdown.

1. Provide the repository where the pipeline should retrieve the code.

   * **Repository** - Defines from which Git repo that the pipeline should retrieve the code.
   * **Git Branch** - Defines from which branch in Git that the selected pipeline should retrieve the code.

1. Define your deployment options.

   1. Under **Deployment Trigger**, define what event activates the pipeline.

      * **Manual** - Lets you manually start the pipeline.
      * **On Git Changes** - Starts the pipeline when commits are added to the configured Git branch. With this option, you can still start the pipeline manually, as required.

   1. For deployment pipelines, under **Important Metric Failures Behavior**, define the behavior of the pipeline when an important failure is encountered in any of the quality gates.

       * **Ask every time** - The default setting and requires manual intervention on any important failure.
       * **Fail Immediately** - The pipeline is canceled whenever an important failure occurs. It is essentially emulating a user manually rejecting each failure.
       * **Continue Immediately** - The pipeline proceeds automatically whenever an important failure occurs. It is essentially emulating a user manually approving each failure.

   1. **Dispatcher Configuration** - The **Deployment Manager** role can configure a set of content paths that are either invalidated or flushed from the AEM Dispatcher cache when a pipeline is run. These cache actions are performed as part of the deployment pipeline step, just after any content packages are deployed. These settings use standard AEM Dispatcher behavior. To configure:

      1. Under **PATH** provide a content path.
      1. Under **TYPE**, select the action to be taken on that path.

         * **Flush** - Perform a cache deletion.
         * **Invalidate** - Perform a cache invalidation, similar to when content is activated from an authoring instance to a publishing instance.
         
      1. Click **Add Path** to add your specified path. You can add up to 100 paths per environment.

1. Click **Save**.
-->

## 다음 단계 {#the-next-steps}

파이프라인을 구성하면 코드를 배포할 수 있습니다. 자세한 내용은 [코드 배포](/help/using/code-deployment.md)를 참조하십시오.

## 비디오 튜토리얼 {#video-tutorial}

이 비디오에서는 이 문서에 자세히 설명된 파이프라인 생성 프로세스에 대한 개요를 제공합니다.

>[!VIDEO](https://video.tv.adobe.com/v/26316/)
