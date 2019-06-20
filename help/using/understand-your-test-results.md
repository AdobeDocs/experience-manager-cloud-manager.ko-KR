---
title: 테스트 결과 이해
seo-title: 테스트 결과 이해
description: 'null'
seo-description: 이 페이지를 따라 파이프라인, 코드 스캔, 성능 및 클라우드 관리자에서 프로그램의 유효성을 검사하는 보안 테스트를 실행하는 동안 세 개의 계층 게이트를 알아보십시오.
uuid: 93 caa 01 f -0 df 2-4 a 6 f -81 dc -23 dfee 24 dc 93
contentOwner: Jsyal
products: sg_ Experiencemanager/Cloudmanager
topic-tags: using
discoiquuid: 83299 ED 8-4 B 7 A -4 B 1 C-BD 56-1 BFC 7 E 7318 D 4
translation-type: tm+mt
source-git-commit: 4c1c6786db9b8972f9315bd2f12fc1752881492f

---


# Understand your Test Results {#understand-your-test-results}

**파이프라인** 프로세스가 진행되는 동안 많은 지표가 캡처되고, 비즈니스 소유자가 정의한 KPI (Key Performance Indicator) 또는 Adobe Managed Services에 의해 설정된 표준에 비해 많은 지표가 캡처됩니다.

이러한 내용은 이 섹션에 정의된 대로 세 가지 계층 처리 시스템을 사용하여 보고됩니다.

## Three-Tier Gates while Running a Pipeline  {#three-tier-gates-while-running-a-pipeline}

파이프라인에 세 개의 게이트가 있습니다.

* 코드 품질
* 성능 테스트
* 보안 테스트

이러한 각 게이트에는 게이트가 식별한 문제에 대한 세 가지 계층 구조가 있습니다.

* **중요** - 게이트가 바로 파이프라인의 실패를 초래하는 문제입니다.
* **중요** - 게이트가 일시 중지 상태를 입력하는 원인이 되는 문제입니다. 배포 관리자, 프로젝트 관리자 또는 비즈니스 소유자는 문제를 무시하거나, 파이프라인이 실패하거나, 문제가 있는 경우 파이프라인이 실패하는 문제를 해결할 수 있습니다.
* **정보** - 이러한 문제는 게이트에 의해 식별된 문제이며, 단지 정보용으로만 제공되지만 파이프라인 실행에 영향을 주지 않습니다.

## Code Quality Testing {#code-quality-testing}

파이프라인의 일부로 소스 코드가 스캔되어 배포가 특정 품질 기준을 충족하는지 확인합니다. 현재, 이는 Sonarqube와 Oakpal를 사용한 콘텐츠 패키지 수준의 검사로 구현됩니다. 일반 Java 규칙과 AEM 관련 규칙을 결합하는 규칙이 100 개 이상 있습니다. 다음 표에는 테스트 기준에 대한 등급이 요약되어 있습니다.

| 이름 | 정의 | 카테고리 | 실패 임계값 |
|--- |--- |--- |--- |
| 보안 등급 | A = 0 Vulnerability <br/>B = at least 1 Minor Vulnerability<br/> C = at least 1 Major Vulnerability <br/>D = at least 1 Critical Vulnerability <br/>E = at least 1 Blocker Vulnerability | 중요 사항 | &lt; B |
| 안정성 등급 | A = 0 Bug <br/>B = at least 1 Minor Bug <br/>C = at least 1 Major Bug <br/>D = at least 1 Critical Bug E = at least 1 Blocker Bug | 중요 사항 | &lt; C |
| 유지 관리 용이성 등급 | Outstanding remediation cost for code smells is: <br/><ul><li>&lt; = 이미 애플리케이션에 있었던 시간의 5% 입니다. 등급은 </li><li>6 ~ 10%의 등급은 A 입니다. </li><li>11 ~ 20% 등급은 C 입니다. </li><li>21 ~ 50%의 등급은 D 입니다.</li><li>50% 이상이 e</li></ul> | 중요 사항 | &lt; A |
| 범위 | A mix of unit test line coverage and condition coverage using this formula: <br/>`Coverage = (CT + CF + LC)/(2*B + EL)`  <br/>where: CT = conditions that have been evaluated to &#39;true&#39; at least once while running unit tests <br/>CF = conditions that have been evaluated to &#39;false&#39; at least once while running unit tests <br/>LC = covered lines = lines_to_cover - uncovered_lines <br/><br/> B = total number of conditions <br/>EL = total number of executable lines (lines_to_cover) | 중요 사항 | &lt; 50% |
| 건너뛴 유닛 테스트 | 건너뛴 단위 테스트 수입니다. | 정보 | &gt; 1 |
| 문제 해결 | 전반적인 문제 유형 - 취약점, 버그 및 코드 냄새 | 정보 | &gt; 1 |
| 중복 라인 | 복제된 블록과 관련된 라인 수입니다. <br/>코드 블록을 복제한 것으로 간주할 수 있습니다. <br/><ul><li>**비 Java 프로젝트:**</li><li>연속된 토큰은 100 개 이상 있어야 합니다.</li><li>이러한 토큰은 적어도 다음에서 확산되어야 합니다. </li><li>Cobol 용 30 줄의 코드 </li><li>ABAP 용 코드 줄 20 개 </li><li>다른 언어용 코드 줄 10 개</li><li>**Java 프로젝트:**</li><li> 토큰 수와 줄 수에 관계없이 연속된 10 개 이상의 중복된 문이 있어야 합니다.</li></ul> <br/>중복을 탐지하는 동안에는 들여쓰기 및 문자열 리터럴의 차이점이 무시됩니다. | 정보 | &gt; 1% |


>[!NOTE]
>
>Refer to [Metric Definitions](https://docs.sonarqube.org/display/SONAR/Metric+Definitions) for more detailed definitions.

You can download the list of rules here [code-quality-rules.xlsx](/help/using/assets/code-quality-rules.xlsx)

>[!NOTE]
>
>To learn more about the custom code quality rules executed by [!UICONTROL Cloud Manager], please refer to [Custom Code Quality Rules](custom-code-quality-rules.md).

### Dealing with False Positives {#dealing-with-false-positives}

품질 스캔 프로세스는 완벽하지 않으며 간혹 문제가 되지 않는 문제를 잘못 식별하기도 합니다. 이것을 &quot;거짓 긍정&quot; 이라고 합니다.

In these cases, the source code can be annotated with the standard Java `@SuppressWarnings` annotation specifying the rule ID as the annotation attribute. 예를 들어, 하드 코딩된 암호를 감지하는 Sonarqube 규칙은 하드코딩된 암호가 어떻게 식별되는지에 대해 공격적일 수 있다는 것입니다.

특정 예제를 살펴보기 위해 이 코드는 일부 외부 서비스에 연결하기 위한 코드가 있는 AEM 프로젝트에서 매우 일반적입니다.

```java
@Property(label = "Service Password")
private static final String PROP_SERVICE_PASSWORD = "password";
```

그런 다음 Sonarqube가 차단기 취약점을 발생시킵니다. 코드를 검토한 후 이 취약점이 취약하지 않음을 확인하고 적절한 규칙 ID로 주석을 달 수 있습니다.

```java
@SuppressWarnings("squid:S2068")
@Property(label = "Service Password")
private static final String PROP_SERVICE_PASSWORD = "password";
```

그러나 실제로는 코드가 다음과 같은 경우입니다.

```java
@Property(label = "Service Password", value = "mysecretpassword")
private static final String PROP_SERVICE_PASSWORD = "password";
```

그런 다음 하드 코딩된 암호를 제거해야 합니다.

>[!NOTE]
>
>`@SuppressWarnings` 주석을 가능한 한 구체적으로 만드는 것이 가장 좋은 방법입니다. 즉, 문제의 원인이 되는 특정 문이나 블록에만 주석을 달 수 있으며 클래스 수준에서 주석을 달 수 있습니다.

## Security Testing {#security-testing}

[!UICONTROL Cloud Manager] 배포 이후 스테이지에서 기존 ***AEM*** 보안 히스를 실행하고 UI를 통해 상태를 보고합니다. 결과는 환경의 모든 AEM 인스턴스에서 집계됩니다.

**인스턴스** 중 하나라도 해당 Health Check에 실패하는 경우 **전체 환경에** Health Check가 실패합니다. 코드 품질 및 성능 테스트와 마찬가지로 이러한 상태 확인은 카테고리로 구성되며 3 계층 게이팅 시스템을 사용하여 보고됩니다. 유일한 차이점은 보안 테스트의 경우 임계값이 없다는 것입니다. 모든 상태 검사는 단순히 합격 또는 불합격입니다.

다음 표에는 현재 검사가 나와 있습니다.

| **이름** | **상태 점검 구현** | **카테고리** |
|---|---|---|
| 비일련화 방화벽 첨부 API 준비 상태가 허용 가능 상태입니다. | Deserialization Firewall Attach API Readiness | 중요 사항 |
| 비일련화 방화벽이 작동하는 기능 | Deserialization Firewall Functional | 중요 사항 |
| 비일련화 방화벽이 로드되었습니다. | Deserialization Firewall Loaded | 중요 사항 |
| Authorizablenodename 구현은 노드 이름/경로에 Authorizable ID를 표시하지 않습니다. | 승인 가능한 노드 이름 생성 | 중요 사항 |
| 기본 암호가 변경되었습니다. | 기본 로그인 계정 | 중요 사항 |
| Sling Default GET Servlet는 DOS 공격으로부터 보호됩니다. | Sling Get Servlet | 중요 사항 |
| 디스패처가 요청을 올바르게 필터링 중입니다. | CQ Dispatcher 구성 | 중요 사항 |
| Adobe Granite HTML 라이브러리 관리자가 적절하게 구성됩니다. | CQ HTML 라이브러리 관리자 구성 | 중요 사항 |
| Sling Java 스크립트 처리기가 적절하게 구성됩니다. | Sling Java Script Handler | 중요 사항 |
| Sling JSP 스크립트 처리기가 적절하게 구성됩니다. | Sling JSP 스크립트 처리기 | 중요 사항 |
| Sling 레퍼러 필터는 CSRF 공격을 방지하기 위해 구성됩니다. | Sling Referrer Filter | 중요 사항 |
| SSL 이 올바르게 구성됨 | SSL 구성 | 중요 사항 |
| 안전하지 않은 사용자 프로필 정책을 찾을 수 없습니다. | 사용자 프로필 기본 액세스 | 중요 사항 |
| CRXDE 지원 번들이 비활성화됨 | CRXDE 지원 | 중요 사항 |
| Sling davex 번들 및 서블릿이 비활성화됨 | DavEx 상태 검사 | 중요 사항 |
| 샘플 컨텐츠가 설치되지 않았습니다. | 컨텐츠 패키지 예 | 중요 사항 |
| WCM 요청 필터와 WCM 디버그 필터가 모두 비활성화되었습니다. | WCM 필터 구성 | 중요 사항 |
| Sling webdav 번들 및 서블릿이 적절하게 구성됩니다. | WebDAV 상태 검사 | 중요 사항 |
| 웹 서버가 클릭재킹 방지를 위해 구성되었습니다. | 웹 서버 구성 | 중요 사항 |
| 복제에서&#39;관리자&#39;사용자를 사용하지 않습니다. | 복제 및 전송 사용자 | 정보 |

## Performance Testing {#performance-testing}

*성능 테스트는* 30 분 [!UICONTROL Cloud Manager] 테스트를 사용하여 구현됩니다.

파이프라인 설정 중에 배포 관리자는 각 버킷으로 이동할 트래픽의 양을 결정할 수 있습니다.

You can learn more about bucket controls, from [Configure your CI/CD Pipeline](configuring-pipeline.md).

>[!NOTE]
>
>To setup your program and define your KPIs, see [Setup your Program](setting-up-program.md).

다음 표에는 세 가지 계층 구조의 게이팅 시스템을 사용한 성능 테스트 행렬이 요약되어 있습니다.

| **지표** | **카테고리** | **실패 임계값** |
|---|---|---|
| 페이지 요청 오류율 % | 중요 사항 | &gt;= 2% |
| CPU 사용률 | 중요 사항 | &gt;= 80% |
| 디스크 IO 대기 시간 | 중요 사항 | &gt;= 50% |
| 95 개의 백분위수 응답 시간 | 중요 사항 | &gt;= 프로그램 수준 KPI |
| 최대 응답 시간 | 중요 사항 | &gt;= 18 초 |
| 분당 페이지 보기 횟수 | 중요 사항 | &lt; 프로그램 수준 KPI |
| 디스크 대역폭 활용 | 중요 사항 | &gt;= 90% |
| 네트워크 대역폭 활용 | 중요 사항 | &gt;= 90% |
| 분당 요청 수 | 정보 | &lt; 6000 |

### Performance Testing Results Graphs {#performance-testing-results-graphs}

새 그래프 및 다운로드 옵션이 성능 테스트 결과 대화 상자에 추가되었습니다.

성능 테스트 대화 상자를 열면 지표 패널을 확장하여 그래프를 표시하거나, 다운로드에 대한 링크를 제공하거나, 둘 다에 대한 링크를 제공할 수 있습니다.

For [!UICONTROL Cloud Manager] Release 2018.7.0, this functionality is available for the following metrics:

* **CPU 사용률**
   * 테스트 기간 동안의 CPU 사용률 그래프.

* **디스크 I/O 대기 시간**
   * 테스트 기간 동안의 디스크 I/O 대기 시간 그래프.

* **페이지 오류율**
   * 테스트 기간 동안 분당 페이지 오류 그래프.
   * 테스트 중에 오류를 일으킨 CSV 파일 목록 페이지.

* **디스크 대역폭 활용**
   * 테스트 기간 동안의 디스크 대역폭 사용률 그래프.

* **네트워크 대역폭 활용**
   * 테스트 기간 동안의 네트워크 대역폭 사용률 그래프.

* **최대 응답 시간**
   * 테스트 기간 동안 분당 최대 응답 시간 그래프.

* **95 번째 백분위수 응답 시간**
   * 테스트 기간 동안 분당 95 번째 백분위수 응답 시간의 그래프.
   * 95 번째 백분위수 응답 시간이 정의된 KPI를 초과하는 CSV 파일 목록 페이지.

다음 이미지는 성능 테스트 그래프를 표시합니다.

![](assets/understand_test-results-screen1.png)

![](assets/screen_shot_2018-09-05at83933pm.png)

