---
title: 테스트 결과 이해
description: 파이프라인의 코드 품질 테스트 작동 방식과 배포 품질을 향상시키는 방법을 알아봅니다.
uuid: 93caa01f-0df2-4a6f-81dc-23dfee24dc93
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: using
discoiquuid: 83299ed8-4b7a-4b1c-bd56-1bfc7e7318d4
feature: CI-CD Pipeline, Test Results
exl-id: 6a574858-a30e-4768-bafc-8fe79f928294
source-git-commit: bfcb0fb5b9cf8317eb75e3b7b46455b14cd9d7b7
workflow-type: tm+mt
source-wordcount: '2896'
ht-degree: 3%

---

# 테스트 결과 이해 {#understand-your-test-results}

파이프라인의 코드 품질 테스트 작동 방식과 배포 품질을 향상시키는 방법을 알아봅니다.

## 소개 {#introduction}

파이프라인 실행 중에 많은 지표가 비즈니스 소유자가 정의한 주요 성과 지표(KPI) 또는 Adobe Managed Services에서 설정한 표준에 대해 캡처되고 비교됩니다.

다음 섹션에 정의된 대로 3단계 등급 시스템을 사용하여 보고됩니다

>[!NOTE]
>
>AEM as a Cloud Service용 Cloud Manager에서 지원하는 테스트에 대해 알아보려면 [AEM as a Cloud Service 설명서](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/test-results/overview-test-results.html).


## 3층 등급  {#three-tier-gates-while-running-a-pipeline}

파이프라인에는 세 개의 게이트가 있습니다.

* 코드 품질
* 성능 테스트
* 보안 테스트

이러한 각 게이트에 대해 게이트로 식별되는 문제에 대한 3층 구조가 있습니다.

* **중요** - 이는 파이프라인의 즉각적인 실패를 야기하는 문제입니다.
* **중요 사항** - 파이프라인이 일시 중지 상태로 전환되는 문제입니다. 배포 관리자, 프로젝트 관리자 또는 비즈니스 소유자는 파이프라인이 진행되는 경우 문제를 무시하거나 문제를 수락할 수 있습니다. 이 경우 파이프라인이 오류로 중단됩니다. 중요한 실패의 재정의는 [시간 제한.](deploying-code.md#timeouts)
* **정보** - 정보 제공용으로만 제공되며 파이프라인 실행에 영향을 주지 않는 문제입니다.

>[!NOTE]
>
>코드 품질 전용 파이프라인에서 코드 품질 테스트 단계가 파이프라인의 마지막 단계이므로 코드 품질 게이트에서의 중요한 오류를 무시할 수 없습니다.

## 코드 품질 테스트 {#code-quality-testing}

이 단계는 코드 품질 전용 파이프라인의 주요 목적인 애플리케이션 코드의 품질을 평가하고 모든 비프로덕션 및 프로덕션 파이프라인에서 빌드 단계 바로 다음에 실행됩니다. 문서를 참조하십시오 [비프로덕션 파이프라인 구성](configuring-non-production-pipelines.md) 추가 정보

### 코드 품질 테스트 이해 {#understanding-code-quality-testing}

코드 품질 테스트는 소스 코드를 스캔하여 특정 품질 기준을 충족하는지 확인합니다. SonarQube 분석, OakPAL을 사용하는 컨텐츠 패키지 수준 검사 및 Dispatcher 최적화 도구를 사용하는 디스패처 유효성 검사의 조합에 의해 구현됩니다.

일반 Java 규칙과 AEM 관련 규칙을 결합하는 규칙이 100개 이상 있습니다. 일부 AEM 관련 규칙은 AEM Engineering의 우수 사례를 기반으로 작성되며, 다음과 같이 부릅니다 [사용자 지정 코드 품질 규칙.](/help/using/custom-code-quality-rules.md)

>[!NOTE]
>
>전체 규칙 목록을 다운로드할 수 있습니다 [이 링크 사용.](/help/using/assets/CodeQuality-rules-latest-AMS.xlsx)

코드 품질 테스트 결과는 다음과 같이 전달됩니다. **등급**. 다음 표에는 다양한 테스트 기준에 대한 등급이 요약되어 있습니다.

| 이름 | 정의 | 카테고리 | 실패 임계값 |
|--- |--- |--- |--- |
| 보안 등급 | A = 취약점 없음<br/>B = 최소 1개의 작은 취약성<br/>C = 최소 1개의 주요 취약성<br/>D = 1개 이상의 중요 취약성<br/>E = 1개 이상의 차단기 취약성 | 중요 | &lt; B |
| 신뢰성 등급 | A = 버그 없음<br/>B = 최소 1개의 작은 버그 <br/>C = 최소 1개의 주요 버그<br/>D = 1개 이상의 중요한 버그<br/>E = 1개 이상의 차단기 버그 | 중요 사항 | &lt; C |
| 유지 관리 등급 | 코드 냄새에 대한 해결되지 않은 수정 비용으로 정의된 값은 이미 애플리케이션에 들어온 시간의 백분율로 정의됩니다<br/><ul><li>A = &lt;=5%</li><li>B = 6-10%</li><li>C = 11-20%</li><li>D = 21-50%</li><li>E = 50% 이상</li></ul> | 중요 사항 | &lt; A |
| 범위 | 공식을 사용하여 단위 테스트 라인 커버리지 및 조건 커버리지의 혼합으로 정의됩니다. <br/>`Coverage = (CT + CF + LC) / (2 * B + EL)`  <ul><li>`CT` = 로 평가된 조건 `true` 단위 테스트를 실행하는 동안 한 번 이상</li><li>`CF` = 로 평가된 조건 `false` 단위 테스트를 실행하는 동안 한 번 이상</li><li>`LC` = 덮힌 라인 = lines_to_cover - indexed_lines</li><li>`B` = 총 조건 수</li><li>`EL` = 총 실행 줄 수(lines_to_cover)</li></ul> | 중요 사항 | &lt; 50% |
| 건너뛴 단위 테스트 | 건너뛴 단위 테스트 수 | 정보 | > 1 |
| 열린 문제 | 전체 문제 유형 - 취약점, 버그 및 코드 냄새 | 정보 | > 0 |
| 중복된 선 | 중복 블록에 포함된 라인의 수로 정의됩니다. 코드 블록은 다음 조건에서 중복되는 것으로 간주됩니다.<br>비 Java 프로젝트:<ul><li>연속되는 토큰이 100개 이상 있어야 합니다.</li><li>이러한 토큰은 적어도 다음 항목에 분산되어야 합니다. </li><li>COBOL용 코드 30줄 </li><li>ABAP용 20줄의 코드 </li><li>다른 언어용 코드 10줄</li></ul>Java 프로젝트:<ul></li><li> 토큰 및 줄 수에 관계없이 10개 이상의 연속문과 중복되는 문이 있어야 합니다.</li></ul>중복을 감지할 때 들여쓰기 및 문자열 리터럴의 차이는 무시됩니다. | 정보 | > 1% |
| Cloud Service 호환성 | 식별된 Cloud Service 호환성 문제 수 | 정보 | > 0 |

>[!NOTE]
>
>을(를) 참조하십시오. [SonarQube의 지표 정의](https://docs.sonarqube.org/latest/user-guide/metric-definitions/) 를 참조하십시오.

>[!NOTE]
>
>에서 실행되는 사용자 지정 코드 품질 규칙에 대해 자세히 알아보려면 [!UICONTROL Cloud Manager]을(를) 참조하십시오. [사용자 지정 코드 품질 규칙.](custom-code-quality-rules.md)

### 긍정 오류 처리 {#dealing-with-false-positives}

품질 스캔 프로세스는 완벽하지 않으며, 실제로 문제가 되지 않는 문제를 잘못 식별하기도 합니다. 이를 **긍정 오류**.

이러한 경우 소스 코드에 표준 Java로 주석을 달 수 있습니다 `@SuppressWarnings` 규칙 ID를 주석 속성으로 지정하는 주석. 예를 들어, 하나의 일반적인 긍정 오류(false positive)는 하드코딩된 암호를 검색하는 SonarQube 규칙이 하드코딩된 암호가 식별되는 방식에 대해 공격적일 수 있다는 것입니다.

다음 코드는 일부 외부 서비스에 연결할 코드가 있는 AEM 프로젝트에서 매우 일반적입니다.

```java
@Property(label = "Service Password")
private static final String PROP_SERVICE_PASSWORD = "password";
```

SonarQube는 그러면 차단제 취약성을 일으킬 것입니다. 그러나 코드를 검토한 후에는 취약성이 아니라는 것을 인식하고 적절한 규칙 ID로 코드에 주석을 달 수 있습니다.

```java
@SuppressWarnings("squid:S2068")
@Property(label = "Service Password")
private static final String PROP_SERVICE_PASSWORD = "password";
```

그러나 코드가 실제로 다음과 같은 경우

```java
@Property(label = "Service Password", value = "mysecretpassword")
private static final String PROP_SERVICE_PASSWORD = "password";
```

그런 다음 하드코딩된 암호를 제거하는 것이 올바른 방법입니다.

>[!NOTE]
>
>반면에, 이것은 `@SuppressWarnings` 가능한 한 구체적이고, 예를 들어 문제를 일으키는 특정 문이나 블록에만 주석을 달고, 클래스 수준에서 주석을 달 수 있습니다.

## 보안 테스트 {#security-testing}

[!UICONTROL Cloud Manager] 기존 **AEM 보안 상태 검사** 배포 후 스테이징 환경에서 를 확인하고 UI를 통해 상태를 보고합니다. 결과는 환경의 모든 AEM 인스턴스에서 집계됩니다.

이러한 상태 확인은 웹 콘솔 또는 작업 대시보드를 통해 언제든지 실행할 수 있습니다.

인스턴스 중 하나라도 주어진 상태 검사에 대한 오류를 보고하면 전체 환경에서 해당 상태 확인에 실패합니다. 코드 품질 및 성능 테스트와 마찬가지로, 이러한 상태 검사는 카테고리로 구성되어 있으며 3단계 게이팅 시스템을 사용하여 보고됩니다. 유일한 차이점은 보안 테스트의 경우 임계값이 없다는 것입니다. 모든 상태 검사는 통과 또는 실패합니다.

다음 표에는 상태 검사가 나와 있습니다.

| 이름 | 상태 확인 구현 | 카테고리 |
|---|---|---|
| Deserialization 방화벽 연결 API 준비 상태가 허용 가능한 상태입니다. | [Deserialization Firewall Attach API Readiness](https://experienceleague.adobe.com/docs/experience-manager-65/administering/security/mitigating-serialization-issues.html#security) | 중요 |
| 역직렬화 방화벽이 작동합니다. | [Deserialization Firewall Functional](https://experienceleague.adobe.com/docs/experience-manager-65/administering/security/mitigating-serialization-issues.html#security) | 중요 |
| deserialization 방화벽이 로드되었습니다. | [Deserialization Firewall Loaded](https://experienceleague.adobe.com/docs/experience-manager-65/administering/security/mitigating-serialization-issues.html#security) | 중요 |
| `AuthorizableNodeName` 구현에서는 노드 이름/경로에 작성 가능한 ID를 표시하지 않습니다. | [승인 가능한 노드 이름 생성](https://experienceleague.adobe.com/docs/experience-manager-65/administering/security/security-checklist.html#security) | 중요 |
| 기본 암호가 변경되었습니다. | [기본 로그인 계정](https://experienceleague.adobe.com/docs/experience-manager-65/administering/security/security.html#users-and-groups-in-aem) | 중요 |
| Sling 기본 GET 서블릿은 DOS 공격으로부터 보호됩니다. | Sling Get Servlet | 중요 |
| Sling Java 스크립트 핸들러가 적절하게 구성되어 있습니다. | Sling Java Script Handler | 중요 |
| Sling JSP 스크립트 핸들러가 적절하게 구성됩니다. | Sling JSP 스크립트 처리기 | 중요 |
| SSL이 올바르게 구성되었습니다. | SSL 구성 | 중요 |
| 안전하지 않은 사용자 프로필 정책을 찾을 수 없습니다. | 사용자 프로필 기본 액세스 | 중요 |
| Sling 레퍼러 필터는 CSRF 공격을 방지하도록 구성되어 있습니다. | [Sling Referrer Filter](https://experienceleague.adobe.com/docs/experience-manager-65/administering/security/security-checklist.html#security) | 중요 사항 |
| Adobe Granite HTML 라이브러리 관리자는 적절하게 구성됩니다. | CQ HTML 라이브러리 관리자 구성 | 중요 사항 |
| CRXDE 지원 번들을 사용할 수 없습니다. | CRXDE 지원 | 중요 사항 |
| Sling DavEx 번들 및 서블릿은 비활성화됩니다. | DavEx 상태 검사 | 중요 사항 |
| 샘플 콘텐츠가 설치되어 있지 않습니다. | 컨텐츠 패키지 예 | 중요 사항 |
| WCM 요청 필터와 WCM 디버그 필터가 모두 비활성화됩니다. | [WCM 필터 구성](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/configuring/osgi-configuration-settings.html#configuring) | 중요 사항 |
| Sling WebDAV 번들 및 서블릿은 적절히 구성됩니다. | WebDAV 상태 검사 | 중요 사항 |
| 웹 서버는 클릭 추적을 방지하도록 구성되어 있습니다. | 웹 서버 구성 | 중요 사항 |
| 복제가 `admin` 사용자. | 복제 및 전송 사용자 | 정보 |

## 성능 테스트 {#performance-testing}

### AEM Sites {#aem-sites}

Cloud Manager는 AEM Sites 프로그램에 대한 성능 테스트를 실행합니다. 성능 테스트는 실제 사용자를 시뮬레이션하여 스테이징 환경에서 페이지에 액세스하여 트래픽을 시뮬레이션하는 가상 사용자(컨테이너)를 방사하여 약 30분 동안 실행됩니다. 이 페이지는 Crawler를 사용하여 찾습니다.

#### 가상 사용자 {#virtual-users}

Cloud Manager에서 분리된 가상 사용자 또는 컨테이너의 수는 와 함께 사용자가 정의한 KPI(응답 시간 및 페이지 보기 수/분)에 의해 파생됩니다 **비즈니스 소유자** 역할 기간 [프로그램을 만들거나 편집합니다.](setting-up-program.md) 정의된 KPI를 기준으로 실제 사용자를 시뮬레이션하는 최대 10개의 컨테이너가 분할됩니다. 테스트를 위해 선택한 페이지는 분할되어 각 가상 사용자에게 할당됩니다.

#### 크롤러 {#crawler}

30분 테스트 기간이 시작되기 전에 Cloud Manager는 고객 성공 엔지니어가 구성한 하나 이상의 시드 URL을 사용하여 스테이징 환경을 크롤링합니다. 이 URL부터 각 페이지의 HTML이 검사되고 링크가 폭 우선 탐색 됩니다. 이 크롤링 프로세스는 최대 5000페이지로 제한됩니다. Crawler의 요청에는 10초의 고정 시간 제한이 있습니다.

#### 테스트를 위한 페이지 세트 {#page-sets}

페이지는 세 개의 페이지 세트로 선택됩니다. Cloud Manager는 프로덕션 및 스테이징 환경에서 AEM 인스턴스의 액세스 로그를 사용하여 다음 버킷을 결정합니다.

* **인기 있는 라이브 페이지** - 이 옵션은 라이브 고객이 액세스하는 가장 방문 빈도가 높은 페이지를 테스트하도록 선택합니다. Cloud Manager는 액세스 로그를 읽고 라이브 고객이 가장 많이 액세스한 상위 25개 페이지를 확인하여 상단 목록을 생성합니다 `Popular Live Pages`. 스테이징 환경에도 있는 이러한 교차 지점은 스테이징 환경에서 크롤링됩니다.

* **기타 라이브 페이지** - 이 옵션은 인기 있는 상위 25개 라이브 페이지를 벗어나지만 테스트하는 것이 중요한 페이지를 벗어나도록 선택합니다. 인기 있는 라이브 페이지와 유사하며 액세스 로그에서 추출되며 스테이징 환경에도 있어야 합니다.

* **새 페이지** - 이 옵션은 스테이징에 배포되었을 수 있고 아직 프로덕션에 배포되지 않았지만 테스트해야 하는 새 페이지를 테스트하기 위해 선택합니다.

##### 선택한 페이지 세트 간 트래픽 배포 {#distribution-of-traffic}

의 1세트에서 3세트까지 어느 곳에서든 선택할 수 있습니다 **테스트** 탭 [파이프라인 구성.](configuring-production-pipelines.md) 트래픽 분배는 선택한 집합 수를 기반으로 합니다. 즉, 세 개 모두 선택한 경우 총 페이지 보기 수의 33%가 각 집합에 배치됩니다. 두 개를 선택하면 50%가 각 세트로 이동합니다. 하나를 선택하면 트래픽의 100%가 해당 세트로 이동합니다.

이 예를 생각해 보겠습니다.

* 인기 있는 라이브 페이지와 새 페이지 세트 간에 50/50이 있습니다.
* 다른 라이브 페이지는 사용되지 않습니다.
* 새 페이지 세트는 3,000페이지를 포함합니다.
* 분당 페이지 보기 수 KPI는 200로 설정됩니다.

30분 테스트 기간:

* 인기 있는 라이브 페이지 세트의 25개 각 페이지가 120번 히트합니다. `((200 * 0.5) / 25) * 30 = 120`
* 새 페이지 세트의 3000개 각 페이지가 한 번 히트됩니다. `((200 * 0.5) / 3000) * 30 = 1`

#### 테스트 및 보고 {#testing-reporting}

Cloud Manager는 기본적으로 스테이징 게시 서버에서 30분 테스트 기간 동안 페이지를 인증되지 않은 사용자로 요청하여 AEM Sites 프로그램에 대한 성능 테스트를 실행합니다. 가상 사용자가 생성한 지표(응답 시간, 오류율, 분당 보기 등)를 측정합니다. 모든 인스턴스에 대한 다양한 시스템 수준 지표(CPU, 메모리, 네트워킹 데이터)는 물론 각 페이지마다 다릅니다.

다음 표에는 3단계 게이팅 시스템을 사용하는 성능 테스트 매트릭스가 요약되어 있습니다.

| 지표 | 카테고리 | 실패 임계값 |
|---|---|---|
| 페이지 요청 오류율 | 중요 | >= 2% |
| CPU 사용률 | 중요 | >= 80% |
| 디스크 IO 대기 시간 | 중요 | >= 50% |
| 95번째 백분위수 응답 시간 | 중요 사항 | >= 프로그램 수준 KPI |
| 최대 응답 시간 | 중요 사항 | >= 18초 |
| 분당 페이지 보기 수 | 중요 사항 | &lt; 프로그램 수준 KPI |
| 디스크 대역폭 사용률 | 중요 사항 | >= 90% |
| 네트워크 대역폭 사용률 | 중요 사항 | >= 90% |
| 분당 요청 수 | 정보 | >= 6000 |

섹션을 참조하십시오 [인증된 성능 테스트](#authenticated-performance-testing) sites 및 Assets에 대한 성능 테스트를 위한 기본 인증 사용에 대한 자세한 내용을 확인하십시오.

>[!NOTE]
>
>테스트 기간 동안 작성자 및 게시 인스턴스가 모두 모니터링됩니다. 한 인스턴스에 대한 지표를 얻을 수 없는 경우 해당 지표는 알 수 없음으로 보고되며 해당 단계가 실패합니다.

#### 선택 사항 - 인증된 성능 테스트 {#authenticated-performance-testing}

필요한 경우 인증된 사이트를 보유한 AMS 고객은 Cloud Manager가 사이트 성능 테스트 중에 웹 사이트에 액세스하는 데 사용할 사용자 이름과 암호를 지정할 수 있습니다.

사용자 이름과 암호는 이름이 인 파이프라인 변수로 지정됩니다 `CM_PERF_TEST_BASIC_USERNAME` 및 `CM_PERF_TEST_BASIC_PASSWORD`.

사용자 이름은 `string` 변수와 암호는 `secretString` 변수를 채우는 방법을 설명합니다. 이 두 항목이 모두 지정되면 성능 테스트 Crawler 및 테스트 가상 사용자의 모든 요청에 이러한 자격 증명이 HTTP Basic 인증으로 포함됩니다.

Cloud Manager CLI를 사용하여 이러한 변수를 설정하려면 다음을 실행하십시오.

```shell
$ aio cloudmanager:set-pipeline-variables <pipeline id> --variable CM_PERF_TEST_BASIC_USERNAME <username> --secret CM_PERF_TEST_BASIC_PASSWORD <password>
```

문서를 참조하십시오 [패치 사용자 파이프라인 변수](https://www.adobe.io/apis/experiencecloud/cloud-manager/api-reference.html#/Variables/patchPipelineVariables) api 사용 방법을 알아보십시오.

### AEM Assets {#aem-assets}

Cloud Manager는 30분 테스트 기간 동안 자산을 반복적으로 업로드하여 AEM Assets 프로그램에 대한 성능 테스트를 실행합니다.

#### 온보딩 요구 사항 {#onboarding-requirement}

자산 성능 테스트의 경우 고객 성공 엔지니어가 `cloudmanager` 작성자가 스테이징 환경으로 온보딩하는 동안 사용자 및 암호입니다. 성능 테스트 단계에는 `cloudmanager` 및 CSE에서 설정한 관련 암호입니다. 작성자 인스턴스에서 이것을 제거하거나 해당 권한을 변경해서는 안 됩니다. 이렇게 하면 자산 성능 테스트가 실패할 수 있습니다.

#### 테스트용 이미지 및 자산 {#assets-for-testing}

고객은 테스트를 위해 자체 자산을 업로드할 수 있습니다. 이 작업은 **파이프라인 설정** 또는 **편집** 화면. JPEG, PNG, GIF 및 BMP와 같은 일반적인 이미지 형식은 Photoshop, Illustrator 및 Postscript 파일과 함께 지원됩니다.

이미지가 업로드되지 않으면 Cloud Manager는 테스트에 기본 이미지 및 PDF 문서를 사용합니다.

#### 테스트를 위한 자산 배포 {#distribution-of-assets}

각 유형의 분당 업로드되는 자산 수의 분포를 **파이프라인 설정** 또는 **편집** 화면.

예를 들어 70/30 분할을 사용하고 분당 10개의 자산이 업로드되는 경우 7개의 이미지와 3개의 문서가 업로드됩니다.

#### 테스트 및 보고 {#testing-and-reporting}

Cloud Manager는에서 CSE가 설정한 사용자 이름과 암호를 사용하여 작성자 인스턴스에 폴더를 만듭니다. [온보딩 요구 사항](#onboaring-requirements) 섹션을 참조하십시오. 그런 다음 오픈 소스 라이브러리를 사용하여 자산을 폴더에 업로드합니다. Assets 테스트 단계에서 실행하는 테스트는 [오픈 소스 라이브러리.](https://github.com/adobe/toughday2) 각 자산에 대한 처리 시간과 다양한 시스템 수준 지표가 30분 테스트 기간에 걸쳐 측정됩니다. 이 기능은 이미지와 PDF 문서를 모두 업로드할 수 있습니다.

>[!TIP]
>
>문서를 참조하십시오 [프로덕션 파이프라인 구성](configuring-production-pipelines.md) 추가 정보 문서를 참조하십시오 [프로그램 설정](setting-up-program.md) 프로그램 설정 및 KPI 정의 방법을 알아봅니다.

### 성능 테스트 결과 그래프 {#performance-testing-results-graphs}

에서는 많은 지표를 사용할 수 있습니다 **성능 테스트 대화 상자**

![지표 목록](assets/understand_test-results-screen1.png)

지표 패널을 확장하여 그래프를 표시하거나 다운로드에 대한 링크를 제공하거나 둘 다 제공할 수 있습니다.

![그래프로 확장된 지표](assets/screen_shot_2018-09-05at83933pm.png)

이 기능은 다음 지표에 사용할 수 있습니다.

* **CPU 사용률**
   * 테스트 기간 동안의 CPU 사용률 그래프

* **디스크 I/O 대기 시간**
   * 테스트 기간 동안의 디스크 I/O 대기 시간 그래프

* **페이지 오류율**
   * 테스트 기간 동안의 분당 페이지 오류 그래프
   * 테스트 중에 오류가 발생한 페이지를 나열하는 CSV 파일

* **디스크 대역폭 사용률**
   * 테스트 기간 동안의 디스크 대역폭 사용률 그래프

* **네트워크 대역폭 사용률**
   * 테스트 기간 동안의 네트워크 대역폭 사용률 그래프

* **최대 응답 시간**
   * 테스트 기간 동안의 분당 최대 응답 시간 그래프

* **95번째 백분위수 응답 시간**
   * 테스트 기간 동안 분당 95번째 백분위수 응답 시간의 그래프
   * 정의된 KPI를 95번째 백분위수 응답 시간이 초과한 페이지를 나열하는 CSV 파일

## 컨텐츠 패키지 스캔 최적화 {#content-package-scanning-optimization}

품질 분석 프로세스의 일부로 Cloud Manager는 Maven 빌드에서 생성한 컨텐츠 패키지를 분석합니다. Cloud Manager는 이 프로세스를 가속화하기 위한 최적화를 제공하므로 특정 패키징 제한이 준수될 때 효과적입니다. 가장 중요한 것은 단일 컨텐츠 패키지를 출력하는 프로젝트에 대해 수행되며, 일반적으로 &quot;모두&quot; 패키지로 지칭되며, 빌드에서 생성한 다른 컨텐츠 패키지가 생략된 것으로 표시됩니다. Cloud Manager가 이 시나리오를 감지하면 &quot;모두&quot; 패키지의 압축을 풀지 않고 개별 콘텐츠 패키지를 직접 스캔하고 종속성을 기반으로 정렬됩니다. 예를 들어 다음 빌드 출력을 고려해 보십시오.

* `all/myco-all-1.0.0-SNAPSHOT.zip` (content-package)
* `ui.apps/myco-ui.apps-1.0.0-SNAPSHOT.zip` (건너뛴-content-package)
* `ui.content/myco-ui.content-1.0.0-SNAPSHOT.zip` (건너뛴-content-package)

안에 있는 유일한 항목인 경우 `myco-all-1.0.0-SNAPSHOT.zip` 건너뛴 두 개의 컨텐츠 패키지인 경우 두 개의 포함된 패키지가 &quot;모든&quot; 컨텐츠 패키지 대신 검사됩니다.

수십 개의 포함된 패키지를 생성하는 프로젝트의 경우 파이프라인 실행당 이 최적화를 사용하여 최대 10분 이상을 절약했습니다.

&quot;모두&quot; 컨텐츠 패키지에 건너뛴 컨텐츠 패키지와 OSGi 번들의 조합이 포함되어 있을 때 특별한 경우가 발생할 수 있습니다. 예를 들어 `myco-all-1.0.0-SNAPSHOT.zip` 이전에 언급된 두 개의 포함된 패키지와 하나 이상의 OSGi 번들이 포함되어 있으면 OSGi 번들만 사용하여 최소 새로운 컨텐츠 패키지가 작성됩니다. 이 패키지의 이름은 항상 다음과 같습니다 `cloudmanager-synthetic-jar-package` 그리고 포함된 번들이 `/apps/cloudmanager-synthetic-installer/install`.

>[!NOTE]
>
>* 이 최적화는 AEM에 배포된 패키지에 영향을 주지 않습니다.
>* 포함된 컨텐츠 패키지와 건너뛴 컨텐츠 패키지 간의 일치는 파일 이름을 기반으로 하므로 건너뛴 여러 컨텐츠 패키지에 동일한 파일 이름이 있거나 포함 중에 파일 이름이 변경된 경우에는 이 최적화를 수행할 수 없습니다.

