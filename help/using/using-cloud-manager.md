---
title: Cloud Manager 사용
seo-title: Adobe AEM Cloud Manager 사용
description: AEM Cloud Manager 사용자 인터페이스에 대해 설명
seo-description: Adobe AEM Cloud Manager 사용자 인터페이스에 대해 설명
page-status-flag: 활성화 안 함
uuid: cef44d35-75ed-44bb-9636-2de2bca5e458
contentOwner: jsyal
discoiquuid: c37566d5-0d1b-4c44-abd7-b271ea443c1a
translation-type: tm+mt
source-git-commit: 4c1c6786db9b8972f9315bd2f12fc1752881492f

---


# Cloud Manager 사용{#using-cloud-manager}

이 섹션에서는 프로그램 설정, 코드 배포, 품질 검사 등의 워크플로우에 대한 UI(사용자 인터페이스)에 대해 [!UICONTROL Cloud Manager] 설명하고 이에 대해 설명합니다.

## 전제 조건 {#prerequisites}

사용 세부 사항을 살펴보려면 먼저 다음 [!UICONTROL Cloud Manager]섹션으로 이동하는 것이 좋습니다.

* [[!UICONTROL Cloud Manager] 사용 전 개념 이해](understanding-concepts.md)
* [[!UICONTROL Cloud Manager]에 대한 일반 구성 설정](setting-configurations-for-cloud-manager.md)

## Getting Started with [!UICONTROL Cloud Manager] {#getting-started-with-cloud-manager}

에 대한 일반 구성을 설정하면 [!UICONTROL Cloud Manager]해당 구성을 사용할 수 [!UICONTROL Cloud Manager]있습니다.

1. Adobe에 로그인하면 솔루션 목록이 [!UICONTROL Experience Cloud] 표시됩니다.

   ![](assets/screen_shot_2018-04-22at92951am.png)

1. 프로그램을 선택하고 왼쪽 상단 아이콘을 클릭하여 엽니다 [!UICONTROL Cloud Manager].

   ![](assets/screen_shot_2018-04-22at93346am.png)

## 프로그램 설정 {#setting-up-program}

입사 후, 사업 소유자는 프로그램의 초기 설정을 수행해야 합니다. 여기에는 프로그램 설명을 설정하고 성능 테스트에 사용할 KPI를 정의하는 작업이 포함됩니다. 축소판을 업로드할 수도 있습니다.

정의된 KPI는 파이프라인이 실행될 때마다 전달되는 성능 테스트의 기준 요소로 사용됩니다.

>[!NOTE]
>
>정의된 KPI는 **단계** 환경에서 실행되는 테스트에서 측정됩니다. 일반적으로 이러한 KPI는 스테이지 환경의 기능에 맞게 축소됩니다.
>
>예를 들어 사용자는 제작 환경에서 분당 평균 1,000개의 페이지 보기를 기대하고 프로덕션 서버에서 4개의 `dispatcher/publish` 서버를 보유하고 있는 경우 이를 분당 250개의 페이지 뷰로 조정해야 합니다(스테이지 환경이 단일 `dispatcher/publish` 서버 쌍으로 구성된다고 가정함).
>
>또한 많은 사용자가 제작 환경 앞에 CDN(Akamai, CloudFront)을 갖게 됩니다. 스테이지 환경에 대해 직접 [!UICONTROL Cloud Manager] 테스트를 실시하므로 KPI는 CDN을 통과하는 예상 트래픽(즉, 캐시 누락)만 반영해야 합니다. 일반적으로 전체 프로덕션 트래픽의 비교적 작은 하위 세트가 됩니다.

### KPI [!UICONTROL Cloud Manager] 정의에 사용 {#using-cloud-manager-to-define-kpis}

아래 절차에 따라 프로그램을 설정하고 KPI를 정의합니다.

1. 설정 **프로그램을** 클릭하여 에서 설정 프로세스를 시작합니다 [!UICONTROL Cloud Manager].
1. [ **프로그램 정보 편집** ] 화면이 표시됩니다.

   축소판을 프로그램에 업로드합니다. 프로그램에 관련 설명을 추가하고 다음을 클릭할 수도 **있습니다**.

1. 사용자 **구성** 화면이 표시됩니다.

   팀 역할 및 사용자를 구성할 수 있습니다. **다음**&#x200B;을 클릭합니다.

1. 일반 **비즈니스 KPI 구성** 화면이 표시됩니다.

   두 개의 KPI를 정의할 수 있습니다(각 배포에 대한 기대).

   1. 허용되는 95번째 백분위수 응답 시간은 어떻게 됩니까?

      1. 권장 값 - 3초
   1. 최대 로드 시 분당 페이지 보기 수는 얼마나 됩니까?

      1. 권장 값 - 200pv/m


1. 제출을 **클릭하여** 설치 마법사를 완료합니다.

   [배포]로 [!UICONTROL Cloud Manager] 변경할 홈 화면이 **표시됩니다**.

## 사용 가능한 환경 {#available-environments}

사용 **가능한 환경은** 관리되는 모든 AEM 환경을 [!UICONTROL Cloud Manager] 나열합니다.

나열된 각 환경에는 연결된 상태가 있습니다.

## 파이프라인 구성 {#configuring-pipeline}

### 파이프라인 설정 {#setting-up-pipeline}

>[!CAUTION]
>
>git 리포지토리에 하나 이상의 분기가 있을 때까지 파이프라인을 설정할 수 없습니다.

코드를 배포하기 전에 에서 파이프라인 설정을 구성해야 합니다 [!UICONTROL Cloud Manager].

파이프라인 구성에 대한 자세한 내용은 [!UICONTROL Cloud Manager **사용** 전 **의 파이프라인 개요 [](understanding-concepts.md)섹션을 참조하십시오.*

>[!NOTE]
>
>초기 설정 후 파이프라인 설정을 변경할 수 있습니다.

### Configuring Pipeline Settings from the [!UICONTROL Cloud Manager]{#configuring-pipeline-settings-from-the-cloud-manager}

아래의 단계에 따라 파이프라인의 [!UICONTROL Cloud Manager] 배너 및 환경 설정을 구성합니다.

1. 분기 **탭에** 액세스하여 애플리케이션 분기를 설정합니다.

   설정할 git 분기를 선택합니다.

   >[!NOTE]
   >
   >Git 리포지토리에 있는 분기는 프로그램에 연결됩니다.

   ![](assets/screen_shot_2018-05-06at73604pm.png)

1. 환경 **탭에** 액세스하여 스테이지 및 프로덕션 **옵션을** **** 선택할 수있습니다.

   파이프라인을 시작할 트리거를 정의할 수 있습니다.

   * **수동** - 파이프라인을 시작하려면 UI에서 수동으로 클릭해야 합니다.
   이제 프로덕션 배포를 제어하는 매개 변수를 정의합니다. 사용 가능한 세 가지 옵션은 다음과 같습니다.

   * **실시간 승인 사용**- 배포는 UI를 통해 비즈니스 소유자, 프로젝트 관리자 또는 배포 관리자가 수동으로 승인해야 [!UICONTROL Cloud Manager] 합니다.
   * **CSE 감독** 사용 - CSE가 실제로 배포를 시작하기 위해 개입합니다.
   ![](assets/screen_shot_2018-05-06at73715pm.png)

1. 테스트 **탭에** 액세스하여 프로그램의 테스트 기준을 정의합니다.

   이제 성능 테스트 매개 변수를 구성할 수 있습니다.

   ![](assets/screen_shot_2018-05-06at73750pm.png)

## 코드 배포 {#deploying-code}

파이프라인(저장소, 환경 및 테스트 환경)을 구성하면 코드를 배포할 수 있습니다.

### 코드 배포 위치 [!UICONTROL Cloud Manager]{#deploying-code-from-cloud-manager}

아래 절차에 따라 프로덕션 환경에 코드를 배포하십시오.

1. 배포 **프로세스를** 시작하려면 [!UICONTROL Cloud Manager] 에서 배포를클릭합니다.
1. [ **스테이지 배포** ] 화면이 표시됩니다.

   빌드를 **클릭하여** 프로세스를 시작합니다.

1. 전체 빌드 프로세스에서는 코드를 확인하고 배포하기 위해 여러 매개 변수를 고려합니다.

   다음 매개 변수는 다음과 같습니다.

   **스테이지 배포**

   * 보관소
   * 단위 테스트
   * 코드 스캔
   * 스테이지 환경에 배포
   **프리 프로덕션 테스트**

   * 보안 테스트
   * 성능 테스트
   >[!NOTE]
   >
   >또한 위에 언급된 테스트 기준에 대한 로그를 보거나 결과를 검토할 수 있습니다.

## 품질 검사 결과 {#results-from-quality-checks}

파이프라인에는 세 개의 문이 있습니다.코드 품질, 성능 테스트 및 보안 테스트.

각 게이트에 대해 게이트로 확인된 문제에 대해 3단계 구조가 있습니다.

* **위험** - 게이트에서 확인된 문제로 파이프라인의 즉각적인 장애가 발생합니다.
* **중요** - 이 문제는 파이프라인이 일시 중지 상태로 전환되는 게이트로 식별되는 문제입니다. 배포 관리자, 프로젝트 관리자 또는 비즈니스 소유자는 파이프라인이 진행되는 경우 문제를 무시하거나 문제를 수락할 수 있습니다. 이 경우 파이프라인이 실패로 중지됩니다.
* **정보** - 이러한 문제는 단지 정보 제공용으로만 제공된 게이트에서 식별되며 파이프라인 실행에 영향을 주지 않는 문제입니다.

### 코드 스캔 {#code-scanning}

![](assets/screen_shot_2018-04-22at101443am.png)

### 성능 테스트 {#performance-testing}

*에서 성능 테스트는* 30분 동안 테스트를 사용하여 구현됩니다 [!UICONTROL Cloud Manager] .

배포 관리자는 파이프라인을 설정하는 동안 각 버킷으로 이동할 트래픽을 결정할 수 있습니다. 양식은 한 양에서 세 개의 버킷 중 어느 것이든 선택할 수 있습니다. 트래픽 분배는 선택된 버킷 수를 기반으로 합니다. 즉, 세 개를 모두 선택한 경우 전체 페이지 보기의 33%가 각 버킷에 배치됩니다.두 개를 선택하면 50%가 각 세트로 이동합니다.하나를 선택하면 트래픽의 100%가 해당 세트로 이동합니다.

예를 들어, 인기 있는 라이브 페이지와 새 페이지 세트(이 예에서는 다른 라이브 페이지가 사용되지 않음) 사이에 50%/50%가 분할되었고 새 페이지 세트에 3000페이지가 포함되어 있다고 가정해 봅시다. 분당 페이지 뷰 수 KPI는 200으로 설정됩니다. 30분 이상의 테스트 기간:

* 인기 있는 라이브 페이지 세트의 25개 페이지 각각은 240회 히트 - `((200 &#42; 0.5) / 25) &#42; 30 = 120`
* 새 페이지 세트의 3000개 페이지 각각은 한 번 히트하게 됩니다. - `((200 &#42; 0.5) / 3000) &#42; 30 = 1`

![](assets/image2018-3-14_16-23-56.png)

### 성능 테스트 지표 {#performance-test-metrics}

테스트 기간 동안 많은 지표가 캡처되어 비즈니스 소유자가 정의한 KPI 또는 AMS가 설정한 표준과 비교됩니다.

이러한 항목은 다음과 같이 3계층 게이팅 시스템을 사용하여 보고됩니다.

### 파이프라인을 실행하는 동안 3층 게이트 {#three-tier-gates-while-running-a-pipeline}

코드 품질, 성능 테스트 및 보안 테스트로 파이프라인에는 세 개의 게이트가 있습니다.

각 게이트에 대해 게이트로 식별된 문제에 대해 세 가지 구조가 있습니다.

* **중요**:이러한 문제는 게이트에서 확인한 문제로서 파이프라인의 즉각적인 실패를 야기합니다.
* **중요**:이 문제는 파이프라인이 일시 중지 상태로 전환되는 게이트로 식별되는 문제입니다. 배포 관리자, 프로젝트 관리자 또는 비즈니스 소유자는 파이프라인이 진행되는 경우 문제를 무시하거나 문제를 수락할 수 있습니다. 이 경우 파이프라인이 실패로 중지됩니다.
* **정보**:이러한 문제는 단지 정보 제공만을 위해 제공된 게이트에서 식별되며 파이프라인 실행에 영향을 주지 않는 문제입니다.

다음 표에는 3계층 게이팅 시스템을 사용하는 성능 테스트 매트릭스가 요약되어 있습니다.

| **지표** | **카테고리** | **실패 임계값** |
|---|---|---|
| 페이지 요청 오류 비율 % | 중요 | &gt;= 2% |
| CPU 사용률 | 중요 | &gt;= 80% |
| 디스크 IO 대기 시간 | 중요 | &gt;= 50% |
| 95 백분위수 응답 시간 | 중요 사항 | &gt;= 프로그램 수준 KPI |
| 최대 응답 시간 | 중요 사항 | &gt;= 18초 |
| 분당 페이지 보기 횟수 | 중요 사항 | &lt; 프로그램 수준 KPI |
| 디스크 대역폭 사용 | 중요 사항 | &gt;= 90% |
| 네트워크 대역폭 사용 | 중요 사항 | &gt;= 90% |
| 분당 요청 수 | 정보 | &lt; 6000 |

### 보안 테스트 {#security-testing}

[!UICONTROL Cloud Manager] 배포 후 스테이지에서 기존 *AEM 보안* 상태 검사를 실행하고 UI를 통해 상태를 보고합니다. 결과는 환경의 모든 AEM 인스턴스에서 집계됩니다.

인스턴스 중 하나라도 특정 상태 확인에 대한 실패를 보고하는 경우 전체 환경이 해당 상태 확인에 실패합니다. 코드 품질 및 성능 테스트와 마찬가지로 이러한 상태 검사는 카테고리로 분류되어 3계층 게이팅 시스템을 사용하여 보고됩니다. 유일한 차이점은 보안 테스트의 경우 임계값이 없다는 것입니다. 모든 건강검진은 그냥 통과되거나 실패한다.

현재 확인은 다음과 같습니다.

| **상태 확인** | **카테고리** |
|---|---|
| Deserialization Firewall Attach API Readiness | 중요 |
| Deserialization Firewall Functional | 중요 |
| Deserialization Firewall Loaded | 중요 |
| 승인 가능한 노드 이름 생성 | 중요 |
| 기본 로그인 계정 | 중요 |
| Sling Get Servlet | 중요 |
| CQ Dispatcher 구성 | 중요 |
| CQ HTML 라이브러리 관리자 구성 | 중요 |
| Sling Java Script Handler | 중요 |
| Sling Jsp Script Handler | 중요 |
| Sling Referrer Filter | 중요 |
| SSL 구성 | 중요 |
| 사용자 프로필 기본 액세스 | 중요 |
| CRXDE 지원 | 중요 사항 |
| DavEx 상태 검사 | 중요 사항 |
| 컨텐츠 패키지 예 | 중요 사항 |
| WCM 필터 구성 | 중요 사항 |
| WebDAV 상태 검사 | 중요 사항 |
| 웹 서버 구성 | 중요 사항 |
| 복제 및 전송 사용자 | 정보 |

### SonarQube의 품질 확인 구현 {#quality-check-implementation-by-sonarqube}

위에 설명된 것처럼 파이프라인의 일부로 코드는 스캔됩니다. 현재, 이것은 SonarQube에 의해 구현됩니다. 일반 Java 규칙과 AEM 특정 규칙의 조합인 93개의 규칙이 있습니다(In의 기존 규칙 세트의 일부 포함). 다음 규칙 목록은 여기에서 찾을 수 있습니다. [code-quality-rules.xlsx](/help/using/assets/code-quality-rules.xlsx)

이러한 규칙에서 다양한 지표가 계산됩니다. 이 중 일부는 스테이지 환경에 배포를 허용하기 전에 품질 게이트로 사용됩니다.

다음은 현재 임계값입니다.

| 이름 | 정의 | 카테고리 | 실패 임계값 |
|--- |--- |--- |--- |
| 보안 등급 | A = 0 취약점 <br/>B = 최소 1개의 작은 취약점<br/> C = 최소 1개의 주요 취약점 D = 최소 1 <br/>개의 치명적인 취약점 <br/>E = 최소 1개의 차단기 취약점 | 중요 | &lt; B |
| 신뢰성 등급 | A = 0 버그 <br/>B = 최소 1개의 보조 버그 <br/>C = 최소 1개의 주요 버그 D = <br/>최소 1개의 중요 버그 E = 최소 1개의 차단기 버그 | 중요 사항 | &lt; C |
| 유지 관리 등급 | 코드 냄새에 대한 뛰어난 교정 비용은 다음과 같습니다. <br/><ul><li>&lt;=5%의 시간이 이미 애플리케이션에 들어갔지만, 등급은 A입니다. </li><li>평점은 6-10% 사이입니다. </li><li>평점은 11~20% 사이입니다. </li><li>평점은 21-50% 사이입니다.</li><li>50% 이상이 E입니다.</li></ul> | 중요 사항 | &lt; A |
| 범위 | 이 공식을 사용한 라인 적용 범위와 조건 적용 범위의 혼합: <br/>`Coverage = (CT + CF + LC)/(2*B + EL)` <br/>위치:CT = 최소 한 번 'true'로 평가된 조건 <br/>= CF = 'false'로 평가된 조건 <br/>LC = 적용 라인 = lines_to_cover - indexed_lines <br/><br/> B = 총 조건 수 EL <br/>= 총 실행 라인 수(lines_to_cover) | 중요 사항 | &lt; 50% |
| 건너뛴 단위 테스트 | 건너뛴 단위 테스트 수입니다. | 정보 | &gt; 1 |
| 미해결 문제 | 전체 문제 유형 - 취약점, 버그 및 코드 냄새 | 정보 | &gt; 1 |
| 중복된 라인 | 중복된 블록에 포함된 라인 수입니다. <br/>코드 블록을 중복으로 간주하는 경우: <ul><li> **Java가 아닌 프로젝트:**</li><li>연속 토큰과 중복 토큰이 100개 이상 있어야 합니다.</li><li>이러한 토큰은 최소 다음 항목에 대해 분산되어야 합니다. </li><li>COBOL을 위한 코드 줄 30개 </li><li>ABAP용 20줄의 코드 </li><li>다른 언어용 코드 10줄</li></ul><ul><li>**Java 프로젝트:**</li><li> 토큰 수와 줄 수에 관계없이 연속 문을 10개 이상 포함해야 합니다.</li></ul>중복 여부를 검색하는 동안 들여쓰기 및 문자열 리터럴의 차이는 무시됩니다. | 정보 | &gt; 1% |

### 잘못된 양조 {#false-positives}

품질 스캔 프로세스는 완벽하지 않으며 실제로 문제가 되지 않는 문제를 잘못 식별하기도 합니다. 이 값을 *거짓 긍정이라고* 합니다( *false 음수가* 보다 의미상 정확할 수 있지만). 이러한 경우, 소스 코드에 주석 속성으로 규칙 ID를 지정하는 표준 Java `@SuppressWarnings` 주석으로 주석을 달 수 있습니다. 예를 들어, 하나의 일반적인 문제는 하드코딩된 암호를 감지하는 SonarQube 규칙이 하드 코딩된 암호로 간주하는 것에 대해 매우 자유롭다는 것입니다.

특정 예를 보려면 이 코드가 일부 외부 서비스에 연결할 코드가 있는 AEM 프로젝트에서 매우 일반적입니다.

```java
@Property(label = "Service Password")
private static final String SERVICE_PASSWORD = "password";
```

SonarQube는 이것을 차단기 취약점으로 만들 것입니다. 이 경우, 고객은 이 취약점이 아님을 확인하고 적절한 규칙 ID로 여기에 주석을 달 수 있습니다.

```java
@SuppressWarnings("squid:S2068")
@Property(label = "Service Password")
private static final String SERVICE_PASSWORD = "password";
```

그러나, 반면에 코드가 실제로 다음과 같은 경우:

```java
@Property(label = "Service Password", value = "mysecretpassword")
private static final String SERVICE_PASSWORD = "password";
```

그런 다음 고객은 SonarQube의 경고를 마음에 두고 하드 코딩된 암호를 제거해야 합니다. 그러나 SonarQube 규칙이 실제로 그 용어에 의해 트리거되고 있기 때문에 그들은 여전히 `@SuppressWarnings` 주석을 추가할 필요가 `password`있습니다.

>[!NOTE]
>
>주석을 가능한 구체적으로 설정하는 것이 좋습니다. 예를 들어 문제를 일으키는 특정 문이나 블록에만 주석을 달고 클래스 수준에서 주석을 달 수 있습니다. `@SuppressWarnings`

