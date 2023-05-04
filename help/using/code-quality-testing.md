---
title: 코드 품질 테스트
description: 파이프라인의 코드 품질 테스트가 어떻게 작동하고 배포 품질을 어떻게 개선할 수 있는지 알아봅니다.
exl-id: 6a574858-a30e-4768-bafc-8fe79f928294
source-git-commit: 8c3b59ab9e00d6ee3b90b9255d025d9e19b3b89a
workflow-type: tm+mt
source-wordcount: '2867'
ht-degree: 100%

---


# 코드 품질 테스트 {#code-quality-testing}

파이프라인의 코드 품질 테스트가 어떻게 작동하고 배포 품질을 어떻게 개선할 수 있는지 알아보십시오.

## 소개 {#introduction}

파이프라인 실행 중에 여러 지표가 수집되어 비즈니스 소유자가 정의한 주요 성과 지표(KPI) 또는 Adobe Managed Services가 설정한 표준과 비교됩니다.

이는 3계층 등급 시스템을 사용하여 보고됩니다.

## 3계층 등급 {#three-tiered-ratings}

파이프라인에는 3개의 게이트가 있습니다.

* 코드 품질
* 성능 테스트
* 보안 테스트

각 게이트에는 게이트에 의해 식별되는 문제에 대한 3계층 구조가 있습니다.

* **심각** - 파이프라인의 즉각적인 실패를 초래하는 문제입니다.
* **중요** - 파이프라인을 일시 중지 상태로의 전환을 초래하는 문제입니다. 배포 관리자, 프로젝트 관리자 또는 비즈니스 소유자는 파이프라인이 진행되는 경우 문제를 재정의하거나 파이프라인이 오류로 중단되는 경우 문제를 수락할 수 있습니다. 중요한 오류의 재지정에는 [시간 초과](/help/using/code-deployment.md#timeouts)가 발생할 수 있습니다.
* **정보** - 순전히 정보 제공 목적으로 제공되며 파이프라인 실행에 영향을 미치지 않는 문제입니다.

>[!NOTE]
>
>코드 품질 전용 파이프라인에서는 코드 품질 테스트 단계가 파이프라인의 최종 단계이기 때문에 코드 품질 게이트의 중요 오류를 재정의할 수 없습니다.

## 코드 품질 테스트 {#code-quality-testing-step}

이 단계는 코드 품질 전용 파이프라인의 주요 목적인 애플리케이션 코드의 품질을 평가하고 비프로덕션 및 프로덕션 파이프라인의 빌드 단계에 이어 즉시 실행됩니다. 자세한 내용은 [비프로덕션 파이프라인 구성](/help/using/non-production-pipelines.md) 문서를 참조하십시오.

코드 품질 테스트는 소스 코드를 스캔하여 특정 품질 기준을 충족하는지 확인합니다. 이는 SonarQube 분석, OakPAL을 사용한 콘텐츠 패키지 수준 검사, Dispatcher 최적화 도구를 사용한 Dispatcher 유효성 검사의 조합으로 구현됩니다.

일반적인 Java 규칙과 AEM별 규칙을 결합한 100개 이상의 규칙이 있습니다. AEM별 규칙 중 일부는 AEM 엔지니어링의 모범 사례를 기반으로 생성되며 [사용자 정의 코드 품질 규칙](/help/using/custom-code-quality-rules.md)이라고 합니다.

>[!TIP]
>
>[이 링크를 사용](/help/assets/CodeQuality-rules-latest-AMS.xlsx)하여 전체 규칙 목록을 다운로드할 수 있습니다.

코드 품질 테스트 결과는 이 표에 요약된 등급으로 제공됩니다.

| 이름 | 정의 | 범주 | 오류 임계값 |
|--- |--- |--- |--- |
| 보안 등급 | A = 취약점 없음<br/>B = 1개 이상의 사소한 취약점<br/>C = 1개 이상의 주요 취약점<br/>D = 1개 이상의 심각한 취약점<br/>E = 1개 이상의 차단 취약점 | 심각 | &lt; B |
| 안정성 등급 | A = 버그 없음<br/>B = 1개 이상의 사소한 버그<br/>C = 1개 이상의 주요 버그<br/>D = 1개 이상의 심각한 버그<br/>E = 1개 이상의 차단 버그 | 중요 | &lt; C |
| 유지 가능성 등급 | 코드 스멜에 대한 미해결 교정 비용으로 정의되며, 애플리케이션에 이미 들어간 시간의 백분율입니다.<br/><ul><li>A = &lt;=5%</li><li>B = 6-10%</li><li>C = 11-20%</li><li>D = 21-50%</li><li>E = >50%</li></ul> | 중요 | &lt; A |
| 범위 | 다음 공식을 사용하여 단위 테스트 라인 범위와 조건 범위의 혼합으로 정의됩니다. <br/>`Coverage = (CT + CF + LC) / (2 * B + EL)`  <ul><li>`CT` = 단위 테스트를 실행하는 동안 한 번 이상 `true`로 평가된 조건</li><li>`CF` = 단위 테스트를 실행하는 동안 한 번 이상 `false`로 평가된 조건</li><li>`LC` = 적용 라인 = lines_to_cover - uncovered_lines</li><li>`B` = 총 조건 수</li><li>`EL` = 총 실행 가능한 라인 수 (lines_to_cover)</li></ul> | 중요 | &lt; 50% |
| 건너뛴 단위 테스트 | 건너뛴 단위 테스트 수 | 정보 | > 1 |
| 미해결 문제 | 전반적인 문제 유형 - 취약점, 버그 및 코드 스멜 | 정보 | > 0 |
| 중복 라인 | 중복된 블록과 관련된 라인의 수로 정의됩니다. 다음 조건에서는 코드 블록이 중복된 것으로 간주됩니다.<br>비 Java 프로젝트:<ul><li>연속 토큰과 중복 토큰이 100개 이상 있어야 합니다.</li><li>이러한 토큰은 최소한 다음과 같이 분산되어야 합니다. </li><li>COBOL의 경우 30개 코드 라인 </li><li>ABAP의 경우 20개 코드 라인 </li><li>기타 언어의 경우 10개 코드 라인</li></ul>Java 프로젝트:<ul></li><li> 토큰과 라인 수에 관계없이 연속적이고 중복된 문이 10개 이상 있어야 합니다.</li></ul>중복을 감지할 때 들여쓰기 및 문자열 리터럴의 차이는 무시됩니다. | 정보 | > 1% |
| Cloud Service 호환성 | 식별된 Cloud Service 호환성 문제 수 | 정보 | > 0 |

>[!NOTE]
>
>자세한 정보는 [SonarQube의 지표 정의](https://docs.sonarqube.org/latest/user-guide/metric-definitions/)를 참조하십시오.

>[!NOTE]
>
>[!UICONTROL Cloud Manager]에서 실행한 [사용자 정의 코드 품질 규칙](custom-code-quality-rules.md)에 대한 자세한 내용은 사용자 정의 코드 품질 규칙 문서를 참조하십시오.

### 긍정 오류 처리 {#dealing-with-false-positives}

품질 검사 프로세스는 완벽하지 않으며 실제로 문제가 아닌 문제를 잘못 식별하기도 합니다. 이를 긍정 오류(false positive)라고 합니다.

이러한 경우 소스 코드는 규칙 ID를 주석 속성으로 지정하는 표준 Java `@SuppressWarnings` 주석으로 추가할 수 있습니다. 예를 들어 한 가지 일반적인 긍정 오류는 하드코딩된 암호를 탐지하는 SonarQube 규칙이 하드코딩된 암호를 식별하는 방법에 대해 공격적일 수 있다는 것입니다.

다음 코드는 일부 외부 서비스에 연결하는 코드가 있는 AEM 프로젝트에서 상당히 일반적입니다.

```java
@Property(label = "Service Password")
private static final String PROP_SERVICE_PASSWORD = "password";
```

그러면 SonarQube에 차단 취약점이 발생합니다. 그러나 코드를 검토한 후 이것이 취약점이 아니며 적절한 규칙 ID로 코드에 주석을 달 수 있다는 것을 알게 됩니다.

```java
@SuppressWarnings("squid:S2068")
@Property(label = "Service Password")
private static final String PROP_SERVICE_PASSWORD = "password";
```

그러나 코드가 실제로 다음과 같은 경우:

```java
@Property(label = "Service Password", value = "mysecretpassword")
private static final String PROP_SERVICE_PASSWORD = "password";
```

이때 하드 코딩된 암호를 제거하는 것이 올바른 해결 방법입니다.

>[!NOTE]
>
>`@SuppressWarnings` 주석을 가능한 구체적으로 만드는 것이 모범 사례이지만(즉, 문제를 일으키는 특정 문이나 블록에만 주석 추가), 클래스 수준에서 주석을 추가하는 것은 가능합니다.

## 보안 테스트 {#security-testing}

[!UICONTROL Cloud Manager]는 배포 후 스테이징 환경에서 기존 AEM 보안 상태 검사를 실행하고 UI를 통해 상태를 보고합니다. 결과는 환경의 모든 AEM 인스턴스에서 집계됩니다.

웹 콘솔 또는 작업 대시보드를 통해 언제든지 동일한 상태 검사를 실행할 수 있습니다.

특정 상태 검사에 대해 오류를 보고하는 인스턴스가 하나라도 있으면 전체 환경이 해당 상태 검사에 실패합니다. 코드 품질 및 성능 테스트와 마찬가지로 이러한 상태 검사는 범주로 구성되며 3계층 게이트 시스템을 사용하여 보고됩니다. 유일한 차이점은 보안 테스트의 경우 임계값이 없다는 것입니다. 모든 상태 검사는 통과 또는 실패입니다.

다음 표에는 상태 검사 목록이 나와 있습니다.

| 이름 | 상태 검사 구현 | 범주 |
|---|---|---|
| Deserialization firewall Attach API Readiness가 허용 가능한 상태입니다. | [Deserialization Firewall Attach API Readiness](https://experienceleague.adobe.com/docs/experience-manager-65/administering/security/mitigating-serialization-issues.html#security) | 심각 |
| 역직렬화 방화벽이 작동합니다. | [Deserialization Firewall Functional](https://experienceleague.adobe.com/docs/experience-manager-65/administering/security/mitigating-serialization-issues.html#security) | 심각 |
| 역직렬화 방화벽이 로드되었습니다. | [Deserialization Firewall Loaded](https://experienceleague.adobe.com/docs/experience-manager-65/administering/security/mitigating-serialization-issues.html#security) | 심각 |
| `AuthorizableNodeName` 구현이 노드 이름/경로에 인증 가능한 ID가 표시되지 않습니다. | [승인 가능한 노드 이름 생성](https://experienceleague.adobe.com/docs/experience-manager-65/administering/security/security-checklist.html#security) | 심각 |
| 기본 암호가 변경되었습니다. | [기본 로그인 계정](https://experienceleague.adobe.com/docs/experience-manager-65/administering/security/security.html#users-and-groups-in-aem) | 심각 |
| Sling 기본 GET 서블릿이 DOS 공격으로부터 보호됩니다. | Sling Get Servlet | 심각 |
| Sling Java Script 핸들러가 적절히 구성되었습니다. | Sling Java Script Handler | 심각 |
| Sling JSP Script 핸들러가 적절히 구성되었습니다. | Sling JSP Script Handler | 심각 |
| SSL이 올바르게 구성되었습니다. | SSL 구성 | 심각 |
| 명확하게 안전하지 않은 사용자 프로필 정책을 찾을 수 없습니다. | 사용자 프로필 기본 액세스 | 심각 |
| Sling Referrer 필터가 CSRF 공격을 방지하기 위해 구성되었습니다. | [Sling Referrer Filter](https://experienceleague.adobe.com/docs/experience-manager-65/administering/security/security-checklist.html#security) | 중요 |
| Adobe Granite HTML 라이브러리 관리자가 적절히 구성되었습니다. | CQ HTML 라이브러리 관리자 구성 | 중요 |
| CRXDE 지원 번들이 비활성화되었습니다. | CRXDE 지원 | 중요 |
| Sling DavEx 번들 및 서블릿이 비활성화되었습니다. | DavEx 상태 검사 | 중요 |
| 샘플 콘텐츠가 설치되지 않았습니다. | 콘텐츠 패키지 예 | 중요 |
| WCM 요청 필터 및 WCM 디버그 필터가 모두 비활성화되었습니다. | [WCM 필터 구성](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/configuring/osgi-configuration-settings.html#configuring) | 중요 |
| Sling WebDAV 번들 및 서블릿이 적절히 구성되었습니다. | WebDAV 상태 검사 | 중요 |
| 웹 서버가 클릭재킹을 방지하도록 구성되었습니다. | 웹 서버 구성 | 중요 |
| 복제에서 `admin` 사용자를 사용하고 있지 않습니다. | 복제 및 전송 사용자 | 정보 |

## 성능 테스트 {#performance-testing}

### AEM Sites {#aem-sites}

Cloud Manager는 AEM Sites 프로그램에 대한 성능 테스트를 실행합니다. 성능 테스트는 실제 사용자를 시뮬레이션하는 가상 사용자(컨테이너)를 회전시켜 트래픽을 시뮬레이션하는 스테이징 환경의 페이지에 액세스함으로써 약 30분간 실행됩니다. 이러한 페이지는 크롤러를 사용하여 발견됩니다.

#### 가상 사용자 {#virtual-users}

Cloud Manager에서 스핀업하는 가상 사용자 또는 컨테이너의 수는 사용자가 프로그램을 [생성하거나 편집할 때 **비즈니스 소유자** 역할을 가진 KPI(응답 시간 및 페이지 뷰/분)에 의해 결정됩니다.](/help/getting-started/program-setup.md) 정의된 KPI를 기준으로 실제 사용자를 시뮬레이션하는 컨테이너는 최대 10개까지 스핀업됩니다. 테스트를 위해 선택된 페이지는 분할되어 각 가상 사용자에게 할당됩니다.

#### 크롤러 {#crawler}

30분간의 테스트 기간이 시작되기 전에 Cloud Manager는 고객 성공 엔지니어가 구성한 하나 이상의 시드 URL 세트를 사용하여 스테이징 환경을 크롤합니다. 이러한 URL에서 시작하여 각 페이지의 HTML을 검사하고 링크를 폭 우선 방식으로 이동됩니다.

* 이 크롤링 프로세스는 기본적으로 최대 5000페이지로 제한됩니다.
* 테스트할 최대 페이지 수는 [환경 변수 ](/help/getting-started/build-environment.md#environment-variables) `CM_PERF_TEST_CRAWLER_MAX_PAGES`를 설정하여 덮어쓸 수 있습니다.
   * 허용되는 값은 `2000` - `7000`입니다.
* 크롤러의 요청에는 10초의 고정 시간 초과가 있습니다.

#### 테스트를 위한 페이지 세트 {#page-sets}

페이지는 3개의 페이지 세트로 선택됩니다. Cloud Manager는 프로덕션 및 스테이징 환경에서 AEM 인스턴스의 액세스 로그를 사용하여 다음 버킷을 결정합니다.

* **방문 빈도가 높은 라이브 페이지** - 이 옵션은 라이브 고객이 액세스하는 가장 방문 빈도가 높은 페이지를 테스트하기 위해 선택합니다. Cloud Manager는 액세스 로그를 읽고 라이브 고객이 가장 많이 액세스하는 상위 25개 페이지를 확인하여 상위 `Popular Live Pages` 목록을 생성합니다. 그런 다음 스테이징 환경에도 존재하는 이러한 교차 지점이 스테이징 환경에서도 크롤됩니다.

* **기타 라이브 페이지** - 이 옵션은 방문 빈도가 높은 라이브 페이지 상위 25개 밖에 있어 인기 항목이 아닐 수 있지만 테스트에 중요한 페이지를 테스트하기 위해 선택합니다. 방문 빈도가 높은 라이브 페이지와 유사하게, 이 페이지는 액세스 로그에서 추출되며 스테이징 환경에도 존재해야 합니다.

* **새 페이지** - 이 옵션은 스테이징에만 배포되고 아직 프로덕션으로 배포되지 않았지만 반드시 테스트해야 하는 새 페이지를 테스트하기 위해 선택됩니다.

##### 선택한 페이지 세트에 걸친 트래픽 분포 {#distribution-of-traffic}

[파이프라인 구성의 **테스트** 탭에서 한 세트에서 세 세트까지 선택할 수 있습니다.](/help/using/production-pipelines.md) 트래픽의 분포는 선택한 세트의 수를 기반으로 합니다. 즉, 세 가지 모두를 선택한 경우, 전체 페이지 조회수의 33%가 각 세트에 할당됩니다. 두 개를 선택하면 50%가 각 세트에 할당됩니다. 하나를 선택하면 트래픽의 100%가 해당 세트로 이동합니다.

이 예제를 생각해 보겠습니다.

* 방문 빈도가 높은 라이브 페이지와 새 페이지 세트 사이에 50/50으로 분할됩니다.
* 다른 라이브 페이지는 사용되지 않습니다.
* 새 페이지 세트에는 3000페이지가 포함되어 있습니다.
* 분당 페이지 조회수 KPI는 200으로 설정되어 있습니다.

30분 이상의 테스트 기간:

* 방문 빈도가 높은 라이브 페이지 세트의 각 25 페이지는 120번 히트됩니다. `((200 * 0.5) / 25) * 30 = 120`
* 새 페이지 세트의 각 3000 페이지는 한 번 히트됩니다. `((200 * 0.5) / 3000) * 30 = 1`

#### 테스트 및 보고 {#testing-reporting}

Cloud Manager는 30분 테스트 기간 동안 스테이징 게시 서버에서 기본적으로 페이지를 인증되지 않은 사용자로 요청하여 AEM Sites 프로그램에 대한 성능 테스트를 실행합니다. 사용자가 생성한 가상 지표(응답 시간, 오류율, 분당 조회수 등)를 측정합니다. 각 페이지 및 모든 인스턴스에 대한 다양한 시스템 수준 지표(CPU, 메모리, 네트워킹 데이터)를 제공합니다.

다음 표에는 3계층 게이트 시스템을 사용한 성능 테스트 지표가 요약되어 있습니다.

| 지표 | 범주 | 오류 임계값 |
|---|---|---|
| 페이지 요청 오류율 | 심각 | >= 2% |
| CPU 활용 비율 | 심각 | >= 80% |
| 디스크 IO 대기 시간 | 심각 | >= 50% |
| 95번째 백분위수 응답 시간 | 중요 | >= 프로그램 수준 KPI |
| 피크 응답 시간 | 중요 | >= 18초 |
| 분당 페이지 뷰 | 중요 | &lt; 프로그램 수준 KPI |
| 디스크 대역폭 활용 | 중요 | >= 90% |
| 네트워크 대역폭 활용 | 중요 | >= 90% |
| 분당 요청 | 정보 | >= 6000 |

Sites 및 Assets에 대한 성능 테스트에 기본 인증을 사용하는 방법에 대한 자세한 내용은 [인증된 성능 테스트](#authenticated-performance-testing) 섹션을 참조하십시오.

>[!NOTE]
>
>작성자 및 게시 인스턴스는 모두 테스트 기간 동안 모니터링됩니다. 한 인스턴스에 대한 지표를 얻지 못하면 해당 지표가 알 수 없는 것으로 보고되고 해당 단계가 실패합니다.

#### 인증된 성능 테스트 {#authenticated-performance-testing}

필요한 경우 인증된 사이트를 보유한 AMS 고객은 사이트 성능 테스트 중에 Cloud Manager가 웹 사이트에 액세스하는 데 사용할 사용자 이름과 암호를 지정할 수 있습니다.

사용자 이름과 암호는 `CM_PERF_TEST_BASIC_USERNAME` 및 `CM_PERF_TEST_BASIC_PASSWORD`라는 이름의 파이프라인 변수로 지정됩니다.

사용자 이름은 `string` 변수에 저장해야 하고 암호는 `secretString` 변수에 저장해야 합니다. 이 두 가지가 모두 지정된 경우 성능 테스트 크롤러 및 테스트 가상 사용자의 모든 요청은 이러한 자격 증명을 HTTP 기본 인증으로 포함합니다.

Cloud Manager CLI를 사용하여 이러한 변수를 설정하려면 다음을 실행합니다.

```shell
$ aio cloudmanager:set-pipeline-variables <pipeline id> --variable CM_PERF_TEST_BASIC_USERNAME <username> --secret CM_PERF_TEST_BASIC_PASSWORD <password>
```

API 사용 방법에 대한 자세한 내용은 [패치 사용자 파이프라인 변수](https://developer.adobe.com/experience-cloud/cloud-manager/reference/api/#operation/patchPipelineVariables) API 설명서를 참조하십시오.

### AEM Assets {#aem-assets}

Cloud Manager는 30분 테스트 기간 동안 반복적으로 에셋을 업로드하여 AEM Assets 프로그램에 대한 성능 테스트를 실행합니다.

#### 온보딩 요구 사항 {#onboarding-requirement}

Assets 성능 테스트를 위해 고객 성공 엔지니어는 작성자가 스테이징 환경에 온보딩하는 동안 `cloudmanager` 사용자 및 암호를 생성합니다. 성능 테스트 단계를 수행하려면 `cloudmanager`라는 사용자와 CSE에서 설정한 관련 암호가 필요합니다. 작성자 인스턴스에서 이를 제거하거나 그 권한을 변경해서는 안 됩니다. 이렇게 하면 Assets 성능 테스트에 실패할 수 있습니다.

#### 테스트를 위한 이미지 및 Assets {#assets-for-testing}

고객은 테스트를 위해 자신의 에셋을 업로드할 수 있습니다. 이 작업은 **파이프라인 설정** 또는 **편집** 화면에서 수행할 수 있습니다. JPEG, PNG, GIF, BMP와 같은 일반적인 이미지 형식은 Photoshop, Illustrator 및 Postscript 파일과 함께 지원됩니다.

이미지가 업로드되지 않으면 Cloud Manager는 테스트를 위해 기본 이미지와 PDF 문서를 사용합니다.

#### 테스트를 위한 에셋 분포 {#distribution-of-assets}

분당 업로드되는 각 유형의 에셋 수에 대한 분포는 **파이프라인 설정** 또는 **편집** 화면에서 설정됩니다.

예를 들어 70/30 분할을 사용하고 분당 10개의 에셋이 업로드된 경우 분당 7개의 이미지와 3개의 문서가 업로드됩니다.

#### 테스트 및 보고 {#testing-and-reporting}

Cloud Manager는 CSE가 설정한 사용자 이름과 암호를 사용하여 작성자 인스턴스에 폴더를 만듭니다. 그런 다음 에셋이 오픈 소스 라이브러리를 사용하여 폴더로 업로드됩니다. Assets 테스트 단계에서 실행되는 테스트는 [오픈 소스 라이브러리를 사용하여 작성됩니다.](https://github.com/adobe/toughday2) 각 에셋의 처리 시간은 물론 다양한 시스템 수준 지표도 30분 테스트 기간 동안 측정됩니다. 이 기능은 이미지와 PDF 문서를 모두 업로드할 수 있습니다.

>[!TIP]
>
>자세한 내용은 [프로덕션 파이프라인 구성](/help/using/production-pipelines.md) 문서를 참조하십시오. 프로그램을 설정하고 KPI를 정의하는 방법은 [프로그램 설정](/help/getting-started/program-setup.md) 문서를 참조하십시오.

### 성능 테스트 결과 그래프 {#performance-testing-results-graphs}

**성능 테스트 대화 상자**&#x200B;에서 여러 지표를 사용할 수 있습니다.

![지표 목록](/help/assets/understand_test-results-screen1.png)

지표 패널을 확장하여 그래프를 표시하거나 다운로드 링크를 제공하거나 둘 다 표시할 수 있습니다.

![그래프로 확장된 지표](/help/assets/screen_shot_2018-09-05at83933pm.png)

이 기능은 다음 지표에 사용할 수 있습니다.

* **CPU 사용률** - 테스트 기간 동안의 CPU 사용률 그래프

* **디스크 I/O 대기 시간** - 테스트 기간 동안의 디스크 I/O 대기 시간 그래프

* **페이지 오류율** - 테스트 기간 동안 분당 페이지 오류 그래프
   * 테스트 동안 오류가 발생한 페이지를 나열하는 CSV 파일

* **디스크 대역폭 사용률** - 테스트 기간 동안의 디스크 대역폭 사용률 그래프

* **네트워크 대역폭 사용률** - 테스트 기간 동안의 네트워크 대역폭 사용률 그래프

* **피크 응답 시간** - 테스트 기간 동안 분당 피크 응답 시간 그래프

* **95번째 백분위수 응답 시간** - 테스트 기간 동안 분당 95번째 백분위수 응답 시간 그래프
   * 95번째 백분위수 응답 시간이 정의된 KPI를 초과한 페이지를 나열하는 CSV 파일

## 콘텐츠 패키지 검색 최적화 {#content-package-scanning-optimization}

품질 분석 프로세스의 일환으로 Cloud Manager는 Maven 빌드에서 생성된 콘텐츠 패키지에 대한 분석을 수행합니다. Cloud Manager는 이 프로세스를 가속화하기 위한 최적화를 제공하며, 이는 특정 패키징 제한이 관찰될 때 효과적입니다. 가장 중요한 것은 일반적으로 “모든” 패키지라고 하는 단일 콘텐츠 패키지를 출력하는 프로젝트에 대해 수행되는 최적화입니다. 이 패키지에는 빌드에 의해 생성된 여러 다른 콘텐츠 패키지가 포함되어 있으며, 이 패키지는 건너뛰기로 표시됩니다. Cloud Manager가 이 시나리오를 감지하면 “모든” 패키지의 압축을 푸는 대신 개별 콘텐츠 패키지가 직접 스캔되고 종속성에 따라 정렬됩니다. 예를 들어 다음 빌드 출력을 고려해 보십시오.

* `all/myco-all-1.0.0-SNAPSHOT.zip` (content-package)
* `ui.apps/myco-ui.apps-1.0.0-SNAPSHOT.zip` (skipped-content-package)
* `ui.content/myco-ui.content-1.0.0-SNAPSHOT.zip` (skipped-content-package)

`myco-all-1.0.0-SNAPSHOT.zip` 내에 있는 항목만 건너뛴 두 개의 콘텐츠 패키지인 경우 “모든” 콘텐츠 패키지 대신 두 개의 임베드된 패키지가 스캔됩니다.

수십 개의 임베드된 패키지를 생성하는 프로젝트의 경우, 이 최적화는 파이프라인 실행당 10분 이상 절약되는 것으로 나타났습니다.

“모든” 콘텐츠 패키지에 건너뛴 콘텐츠 패키지와 OSGi 번들의 조합이 포함된 경우 특별한 경우가 발생할 수 있습니다. 예를 들어 `myco-all-1.0.0-SNAPSHOT.zip`에 앞서 언급한 두 개의 임베드된 패키지가 포함된 경우 하나 이상의 OSGi 번들로만 구성된 새로운 최소 콘텐츠 패키지가 구성됩니다. 이 패키지의 이름은 항상 `cloudmanager-synthetic-jar-package`이고 포함된 번들은 `/apps/cloudmanager-synthetic-installer/install`에 배치됩니다.

>[!NOTE]
>
>* 이 최적화는 AEM에 배포된 패키지에 영향을 주지 않습니다.
>* 임베드된 콘텐츠 패키지와 건너뛴 콘텐츠 패키지 간의 일치는 파일 이름을 기반으로 하므로 여러 건너뛴 콘텐츠 패키지의 파일 이름이 정확히 동일하거나 임베드하는 동안 파일 이름이 변경된 경우에는 이 최적화를 수행할 수 없습니다.

