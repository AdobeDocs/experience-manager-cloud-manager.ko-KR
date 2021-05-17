---
title: 테스트 결과 이해
seo-title: 테스트 결과 이해
description: Cloud Manager에서 파이프라인을 실행하는 동안 3개의 계층 게이트에 대한 자세한 내용
seo-description: Cloud Manager에서 파이프라인, 코드 스캔, 성능 및 보안 테스트를 실행하는 동안 3개의 계층 게이트에 대해 알아보려면 이 페이지를 따르십시오.
uuid: 93caa01f-0df2-4a6f-81dc-23dfee24dc93
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: using
discoiquuid: 83299ed8-4b7a-4b1c-bd56-1bfc7e7318d4
feature: CI-CD 파이프라인, 테스트 결과
exl-id: 6a574858-a30e-4768-bafc-8fe79f928294
source-git-commit: df2f598f91201d362f54b17e4092ff6bd6a72cec
workflow-type: tm+mt
source-wordcount: '2722'
ht-degree: 4%

---

# 테스트 결과 이해 {#understand-your-test-results}

>[!NOTE]
>Cloud Services 파이프라인에 대해 클라우드 관리자가 지원하는 테스트 결과 및 테스트에 대해 알려면 [여기](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/test-results/overview-test-results.html?lang=en#using-cloud-manager)를 참조하십시오.

파이프라인 실행 중에 비즈니스 소유자가 정의한 주요 성과 지표(KPI) 또는 Adobe Managed Services가 설정한 표준과 비교하여 많은 지표가 캡처되어 비교됩니다.

이 항목은 이 섹션에 정의된 대로 3층 게이팅 시스템을 사용하여 보고됩니다.

## 파이프라인을 실행하는 동안 3계층 게이츠 {#three-tier-gates-while-running-a-pipeline}

파이프라인에는 세 개의 문이 있습니다.

* 코드 품질
* 성능 테스트
* 보안 테스트

이 각각의 게이트에 있어서, 게이트에 의해 식별된 문제에 대한 3층 구조가 있습니다.

* **위험**  - 파이프라인의 즉각적인 실패를 초래하는 게이트로 식별되는 문제입니다.
* **중요**  - 파이프라인이 일시 중지된 상태로 전환되는 게이트로 식별되는 문제입니다. 배포 관리자, 프로젝트 관리자 또는 비즈니스 소유자는 파이프라인이 진행되는 경우 문제를 무시하거나 해당 문제를 허용할 수 있습니다. 이 경우 파이프라인이 오류로 인해 중단됩니다. 중요한 실패 재정의는 [시간 초과](deploying-code.md#timeouts)에 따릅니다.
* **정보**  - 정보 제공용으로만 제공되고 파이프라인 실행에 영향을 주지 않는 게이트로 식별되는 문제입니다.

>[!NOTE]
>
>코드 품질만 파이프라인에서 코드 품질 테스트 단계가 파이프라인의 마지막 단계이므로 코드 품질 테스트 게이트에서의 중요 오류를 무시할 수 없습니다.

## 코드 품질 테스트 {#code-quality-testing}

이 단계에서는 응용 프로그램 코드의 품질을 평가합니다. 코드 품질만 파이프라인의 핵심 목표이며 비프로덕션 및 프로덕션 파이프라인에서 빌드 단계 바로 다음에 실행됩니다. 다른 유형의 파이프라인에 대한 자세한 내용은 [CI-CD 파이프라인 구성](/help/using/configuring-pipeline.md)을 참조하십시오.

### 코드 품질 테스트 이해 {#understanding-code-quality-testing}

코드 품질 테스트에서 소스 코드가 특정 품질 기준을 충족하는지 확인하기 위해 스캔됩니다. 현재 SonarQube와 OakPAL을 사용한 컨텐츠 패키지 수준 검사 및 Dispatcher 최적화 도구를 사용한 디스패처 유효성 검사 기능을 함께 사용하여 구현됩니다. 일반 Java 규칙과 AEM 관련 규칙을 결합하는 100개 이상의 규칙이 있습니다. AEM 관련 규칙 중 일부는 AEM 엔지니어링 우수 사례를 기반으로 만들어지며 [사용자 지정 코드 품질 규칙](/help/using/custom-code-quality-rules.md)이라고 합니다.

>[!NOTE]
>[여기에서 규칙 전체 목록을 다운로드할 수 있습니다](/help/using/assets/CodeQuality-rules-AMS.xlsx).

이 단계의 결과는 *등급*&#x200B;으로 전달됩니다. 아래 표에는 다양한 테스트 기준에 대한 등급이 요약되어 있습니다.

| 이름 | 정의 | 카테고리 | 실패 임계값 |
|--- |--- |--- |--- |
| 보안 등급 | A = 0 취약점 <br/>B = 최소 1개의 작은 취약점<br/> C = 최소 1개의 주요 취약점 <br/>D = 최소 1개의 중요 취약점 <br/>E = 최소 1개의 차단기 취약점 | 중요 | &lt; B |
| 신뢰성 등급 | A = 0 버그 <br/>B = 최소 1개의 경미한 버그 <br/>C = 최소 1개의 주요 버그 <br/>D = 최소 1개의 중요 버그<br/>E = 최소 1개의 차단기 버그 | 중요 사항 | &lt; C |
| 유지 관리 등급 | 코드 냄새에 대한 뛰어난 교정 비용은 다음과 같습니다.<br/><ul><li>&lt;> </li><li>평점은 6~10% 사이의 B입니다. </li><li>평점은 11~20% 사이입니다. </li><li>평점은 21~50% 사이에서 D</li><li>50% 이상의 것은 E입니다.</li></ul> | 중요 사항 | &lt; A |
| 범위 | 이 공식을 사용하여 단위 테스트 라인 적용 범위 및 조건 적용 범위를 혼합합니다.<br/>`Coverage = (CT + CF + LC)/(2*B + EL)` <br/>여기서:CT = 단위 테스트를 실행하는 동안 최소 한 번 &#39;true&#39;로 평가된 조건 <br/>CF = 장치 테스트를 실행하는 동안 최소 한 번 &#39;false&#39;로 평가된 조건 <br/>LC = 적용 라인 = lines_to_cover - inded_lines <br/><br/> B = 총 실행 라인 수 <br/>줄 수(lines_to_cover) | 중요 사항 | &lt; 50% |
| 건너뛴 단위 테스트 | 건너뛴 단위 테스트 수입니다. | 정보 | > 1 |
| 미해결 문제 | 전체 문제 유형 - 취약점, 버그 및 코드 냄새 | 정보 | > 0 |
| 중복된 선 | 중복된 블록에 포함된 줄 수입니다. <br/>코드 블록을 중복으로 간주하는 경우:  <br/><ul><li>**Java가 아닌 프로젝트:**</li><li>연속된 토큰이 100개 이상 있어야 합니다.</li><li>이러한 토큰은 다음과 같은 경우에 배포해야 합니다. </li><li>COBOL을 위한 코드 줄 30개 </li><li>ABAP용 코드 20줄 </li><li>다른 언어용 코드 10줄</li><li>**Java 프로젝트:**</li><li> 토큰 및 줄 수에 관계없이 10개 이상의 연속된 명령문과 중복되는 명령문이 있어야 합니다.</li></ul> <br/>중복 여부를 감지할 때 들여쓰기와 문자열 리터럴의 차이는 무시됩니다. | 정보 | > 1% |
| Cloud Service 호환성 | 식별된 Cloud Service 호환성 문제 수입니다. | 정보 | > 0 |


>[!NOTE]
>
>자세한 정의는 [지표 정의](https://docs.sonarqube.org/display/SONAR/Metric+Definitions)를 참조하십시오.

>[!NOTE]
>
>[!UICONTROL Cloud Manager]에서 실행하는 사용자 지정 코드 품질 규칙에 대한 자세한 내용은 [사용자 지정 코드 품질 규칙](custom-code-quality-rules.md)을 참조하십시오.

### 잘못된 포지션 처리 {#dealing-with-false-positives}

품질 스캔 프로세스는 완벽하지 않으며 실제로 문제가 되지 않는 문제를 잘못 식별하기도 합니다. 이를 &quot;거짓 양성&quot;이라고 한다.

이러한 경우 규칙 ID를 주석 속성으로 지정하는 표준 Java `@SuppressWarnings` 주석으로 소스 코드에 주석을 달 수 있습니다. 예를 들어, 한 가지 일반적인 문제는 하드코딩된 암호를 감지하는 SonarQube 규칙이 하드 코딩된 암호를 식별하는 방법에 대해 공격적일 수 있다는 것입니다.

특정 예제를 보려면, 이 코드는 일부 외부 서비스에 연결할 코드가 있는 AEM 프로젝트에서 매우 일반적입니다.

```java
@Property(label = "Service Password")
private static final String PROP_SERVICE_PASSWORD = "password";
```

SonarQube는 Blocker 취약점을 해결합니다. 코드를 검토한 후 이 취약점이 아님을 확인하고 적절한 규칙 ID로 이 코드에 주석을 달 수 있습니다.

```java
@SuppressWarnings("squid:S2068")
@Property(label = "Service Password")
private static final String PROP_SERVICE_PASSWORD = "password";
```

그러나 반면에 코드가 실제로 다음과 같은 경우:

```java
@Property(label = "Service Password", value = "mysecretpassword")
private static final String PROP_SERVICE_PASSWORD = "password";
```

그런 다음 하드 코딩된 암호를 제거하는 것이 좋습니다.

>[!NOTE]
>
>`@SuppressWarnings` 주석을 가능한 구체적으로 만드는 것이 가장 좋지만, 예를 들어 문제를 일으키는 특정 문이나 블록에만 주석을 다는 것은 클래스 수준에서 주석을 달 수 있습니다.

## 보안 테스트 {#security-testing}

[!UICONTROL Cloud Manager] 배포 후 기존  ***AEM 보안 상태*** 검사 단계를 실행하고 UI를 통해 상태를 보고합니다. 결과는 환경의 모든 AEM 인스턴스에서 집계됩니다.

이와 동일한 상태 검사는 웹 콘솔 또는 작업 대시보드를 통해 언제든지 실행할 수 있습니다.

**인스턴스** 중 특정 상태 확인에 대한 오류가 보고되는 경우 전체 **환경**&#x200B;에서 해당 상태 확인에 실패합니다. 코드 품질 및 성능 테스트와 마찬가지로 이러한 상태 검사는 카테고리로 분류되어 3계층 게이팅 시스템을 사용하여 보고됩니다. 유일한 차이점은 보안 테스트의 경우 임계값이 없다는 점입니다. 모든 상태 확인은 그냥 통과되거나 실패한다.

다음 표에는 현재 검사가 나열됩니다.

| **이름** | **상태 확인 구현** | **카테고리** |
|---|---|---|
| 비직렬화 방화벽 첨부 API 준비 상태가 허용 상태입니다. | [Deserialization Firewall Attach API Readiness](https://experienceleague.adobe.com/docs/experience-manager-65/administering/security/mitigating-serialization-issues.html?lang=en#security) | 중요 |
| 비직렬화 방화벽이 사용 가능합니다. | [Deserialization Firewall Functional](https://experienceleague.adobe.com/docs/experience-manager-65/administering/security/mitigating-serialization-issues.html?lang=en#security) | 중요 |
| 비직렬화 방화벽이 로드됨 | [Deserialization Firewall Loaded](https://experienceleague.adobe.com/docs/experience-manager-65/administering/security/mitigating-serialization-issues.html?lang=en#security) | 중요 |
| AuthorizableNodeName 구현은 노드 이름/경로에 인증 가능한 ID를 표시하지 않습니다. | [승인 가능한 노드 이름 생성](https://experienceleague.adobe.com/docs/experience-manager-64/administering/security/security-checklist.html?lang=en#security) | 중요 |
| 기본 암호가 변경되었습니다. | [기본 로그인 계정](https://experienceleague.adobe.com/docs/experience-manager-65/administering/security/security.html?lang=en#users-and-groups-in-aem) | 중요 |
| 기본 GET 서블릿은 DOS 공격으로부터 보호됩니다. | Sling Get Servlet | 중요 |
| Sling Java 스크립트 핸들러는 적절하게 구성됩니다 | Sling Java Script Handler | 중요 |
| Sling JSP 스크립트 핸들러는 적절하게 구성되어 있습니다. | Sling JSP Script Handler | 중요 |
| SSL이 올바르게 구성됨 | SSL 구성 | 중요 |
| 안전하지 않은 사용자 프로필 정책을 찾을 수 없음 | 사용자 프로필 기본 액세스 | 중요 |
| CSRF 공격을 방지하기 위해 Sling 레퍼러 필터가 구성되었습니다. | [Sling Referrer Filter](https://experienceleague.adobe.com/docs/experience-manager-65/administering/security/security-checklist.html?lang=en#security) | 중요 사항 |
| Adobe Granite HTML 라이브러리 관리자가 적절하게 구성되어 있습니다. | CQ HTML 라이브러리 관리자 구성 | 중요 사항 |
| CRXDE 지원 번들을 사용할 수 없음 | CRXDE 지원 | 중요 사항 |
| Sling DavEx 번들 및 서블릿이 비활성화됨 | DavEx 상태 검사 | 중요 사항 |
| 샘플 콘텐트가 설치되지 않았습니다. | 컨텐츠 패키지 예 | 중요 사항 |
| WCM 요청 필터와 WCM 디버그 필터가 모두 비활성화되었습니다. | [WCM 필터 구성](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/configuring/osgi-configuration-settings.html?lang=en#configuring) | 중요 사항 |
| Sling WebDAV 번들 및 서블릿이 적절하게 구성됨 | WebDAV 상태 검사 | 중요 사항 |
| 웹 서버가 클릭재킹을 방지하도록 구성되었습니다. | 웹 서버 구성 | 중요 사항 |
| 복제에서 &#39;admin&#39; 사용자를 사용하고 있지 않습니다. | 복제 및 전송 사용자 | 정보 |

## 성능 테스트 {#performance-testing}

### AEM Sites {#aem-sites}

Cloud Manager는 AEM Sites 프로그램에 대한 성능 테스트를 실행합니다. 성능 테스트는 스테이지 환경에서 페이지에 액세스하고 트래픽을 시뮬레이션하기 위해 실제 사용자를 시뮬레이션하는 가상 사용자(컨테이너)를 회전시켜 ~ 30분 동안 실행됩니다. 이러한 페이지는 크롤러를 사용하여 찾을 수 있습니다.

1. **가상 사용자**

   Cloud Manager에서 분리된 가상 사용자 또는 컨테이너의 수는 [프로그램](setting-up-program.md)을 만들거나 편집하는 동안 비즈니스 소유자 역할에서 사용자가 정의한 KPI(응답 시간 및 페이지 보기/분)에 의해 결정됩니다. 정의된 KPI를 기반으로 실제 사용자를 시뮬레이션하는 최대 10개의 컨테이너가 정리됩니다. 테스트를 위해 선택된 페이지는 분할되어 각 가상 사이트에 할당됩니다.

1. **Crawler**

   30분 테스트 기간이 시작되기 전에 Cloud Manager는 고객 성공 엔지니어가 구성한 하나 이상의 시드 URL 세트를 사용하여 스테이지 환경을 크롤합니다. 이 URL부터 시작하여 각 페이지의 HTML을 검사하고 링크를 첫 번째 방식으로 탐색합니다. 이 크롤링 프로세스는 최대 5,000페이지로 제한됩니다. 크롤러 요청에 10초의 고정 시간 초과가 있습니다.

1. **테스트용 페이지 세트**

   3개의 페이지 세트로 페이지가 선택됩니다. Cloud Manager는 프로덕션 및 스테이지에서 AEM 인스턴스의 액세스 로그를 사용하여 다음 3개의 버킷을 결정합니다.

   * *인기 있는 라이브 페이지*:이 옵션은 라이브 고객이 액세스한 가장 인기 있는 페이지가 테스트되도록 선택합니다. Cloud Manager는 액세스 로그를 읽고 라이브 고객이 가장 많이 액세스한 상위 25개 페이지를 확인하여 상위 `Popular Live Pages` 목록을 생성합니다. 스테이지에 있는 이러한 항목의 교차점은 스테이지 환경에서 크롤링됩니다.

   * *기타 라이브 페이지*:이 옵션을 선택하면 인기 없는 상위 25개의 라이브 페이지 밖에 있지만 테스트에 중요한 페이지가 테스트되도록 합니다. 인기 있는 라이브 페이지와 유사하며 액세스 로그에서 추출되며 스테이지에도 있어야 합니다.

   * *새 페이지*:이 옵션은 스테이지에만 배포되었지만 아직 프로덕션에 배치되지 않았지만 테스트되어야 하는 새 페이지를 테스트하기 위해 선택합니다.

      **선택한 페이지 세트 간 트래픽 배포**

      파이프라인 구성(삽입 링크)의 &#39;테스트&#39; 탭에서 1부터 3세트 사이의 모든 세트를 선택할 수 있습니다. 트래픽 분배는 선택된 집합 수를 기반으로 합니다. 즉, 3개를 모두 선택한 경우 총 페이지 보기의 33%가 각 집합에 배치됩니다.두 개를 선택하면 50%가 각 세트로 이동됩니다.하나를 선택하면 트래픽의 100%가 해당 세트로 이동합니다.

      예를 들어, 인기 있는 라이브 페이지와 새 페이지 세트(이 예에서는 다른 라이브 페이지가 사용되지 않음) 간에 50% - 50% 분할이 있고 새 페이지 세트에 3000페이지가 포함되어 있다고 가정해 보겠습니다. 분당 페이지 뷰 수 KPI는 200으로 설정됩니다. 30분 동안의 테스트 기간:

      * 인기 있는 라이브 페이지 세트의 25개 페이지는 각각 120회 - ((200 * 0.5) / 25) * 30 = 120으로 히트합니다.

      * 새 페이지 세트의 3000개 각 페이지가 한 번 히트 - ((200 * 0.5) / 3000) * 30 = 1

#### 테스트 및 보고 {#testing-reporting}

Cloud Manager는 스테이지 게시 서버에서 30분 동안 기본적으로 인증되지 않은 사용자로 페이지를 요청하고 (가상) 사용자가 생성한 지표(응답 시간, 오류 비율, 분당 보기 수 등)를 측정하여 AEM Sites 프로그램에 대한 성능 테스트를 실행합니다. 각 페이지와 모든 인스턴스에 대한 다양한 시스템 수준 지표(CPU, 메모리, 네트워킹 데이터)에 대해 수행됩니다.\
다음 표는 3계층 게이팅 시스템을 사용하는 성과 테스트 지표를 보여줍니다.

다음 표에는 3계층 게이팅 시스템을 사용하는 성능 테스트 매트릭스가 요약되어 있습니다.

| **지표** | **카테고리** | **실패 임계값** |
|---|---|---|
| 페이지 요청 오류 비율 % | 중요 | >= 2% |
| CPU 활용률 | 중요 | >= 80% |
| 디스크 IO 대기 시간 | 중요 | >= 50% |
| 95 백분위수 응답 시간 | 중요 사항 | >= 프로그램 수준 KPI |
| 최대 응답 시간 | 중요 사항 | >= 18초 |
| 분당 페이지 보기 횟수 | 중요 사항 | &lt; Program-level=&quot;&quot; KPI=&quot;&quot;> |
| 디스크 대역폭 사용 | 중요 사항 | >= 90% |
| 네트워크 대역폭 사용 | 중요 사항 | >= 90% |
| 분당 요청 수 | 정보 | >= 6000 |

사이트 및 자산에 대한 성능 테스트에 기본 인증을 사용하는 방법에 대한 자세한 내용은 아래 섹션 **인증된 성능 테스트**&#x200B;를 참조하십시오.

>[!NOTE]
>각 인스턴스는 테스트 기간 동안 게시 및 작성자에 대해 모니터링됩니다. 한 인스턴스에만 대한 지표를 얻지 못한 경우 해당 지표가 알 수 없는 것으로 보고되고 해당 단계가 실패합니다.

#### 인증된 성능 테스트 {#authenticated-performance-testing}

이 기능은 사이트 선택 사항입니다.
인증된 사이트를 보유한 AMS 고객은 Cloud Manager가 사이트 성능 테스트 동안 웹 사이트에 액세스하는 데 사용할 사용자 이름과 암호를 지정할 수 있습니다.
사용자 이름과 암호는 `CM_PERF_TEST_BASIC_USERNAME` 및 `CM_PERF_TEST_BASIC_PASSWORD` 이름의 파이프라인 변수로 지정됩니다.
반드시 필요한 것은 아니지만 사용자 이름에 문자열 변수 유형을 사용하고 암호에 대해 secretString 변수 유형을 사용하는 것이 좋습니다. 이 두 가지가 모두 지정되면 성능 테스트 크롤러 및 테스트 가상 사용자의 모든 요청에 이러한 자격 증명이 HTTP Basic 인증으로 포함됩니다.

Cloud Manager CLI를 사용하여 이러한 변수를 설정하려면 다음을 실행하십시오.

```shell
$ aio cloudmanager:set-pipeline-variables <pipeline id> --variable CM_PERF_TEST_BASIC_USERNAME <username> --secret CM_PERF_TEST_BASIC_PASSWORD <password>
```

API를 사용하는 방법에 대해 알려면 [변수](https://www.adobe.io/apis/experiencecloud/cloud-manager/api-reference.html#/Variables/patchPipelineVariables)를 참조하십시오.

### AEM Assets {#aem-assets}

Cloud Manager는 30분 테스트 기간 동안 자산을 반복적으로 업로드하여 AEM Assets 프로그램에 대한 성능 테스트를 실행합니다.

1. **온보딩 요구 사항**

   자산 성능 테스트의 경우 고객 성공 엔지니어는 작성자-단계 환경 온보딩 중에 `cloudmanager` 사용자(및 암호)를 만듭니다. 성능 테스트 단계에는 `cloudmanager`이라는 사용자와 CSE에 의해 설정된 관련 암호가 필요합니다. 이는 작성자에서 제거되거나 사용 권한으로 변경되지 않아야 합니다. 이렇게 하면 자산 성능 테스트가 실패할 가능성이 있습니다.

1. **테스트용 이미지 및 에셋**

   고객은 자체 에셋을 업로드하여 테스트할 수 있습니다. 이 작업은 파이프라인 설정(Pipeline Setup) 또는 편집(Edit) 화면에서 수행할 수 있습니다. JPEG, PNG, GIF 및 BMP와 같은 일반적인 이미지 형식은 Photoshop, Illustrator 및 Postscript 파일과 함께 지원됩니다. 그러나 업로드된 이미지가 없는 경우 Cloud Manager는 테스트용으로 기본 이미지와 PDF 문서를 사용합니다.

1. **테스트용 에셋 배포**

   각 유형의 업로드된 에셋 수에 대한 분배는 파이프라인 설정(Pipeline Setup) 또는 편집(Edit) 화면에서 설정됩니다.
예를 들어, 아래 그림에서와 같이 70/30 분할을 사용하는 경우 분당 10개의 에셋이 업로드되고 분당 7개의 이미지가 업로드되며 3개의 문서가 업로드됩니다.

1. **테스트 및 보고**

   Cloud Manager는 위에 언급된 #1(온보딩 요구 사항)의 CSE에서 사용자 이름 및 암호 설정을 사용하여 작성자 인스턴스에 폴더를 만들고 오픈 소스가 있는 라이브러리를 사용하여 폴더에 에셋을 업로드합니다. 자산 테스트 단계에서 실행하는 테스트는 이 [오픈 소스 라이브러리](https://github.com/adobe/toughday2)를 사용하여 작성됩니다. 각 자산에 대한 처리 시간과 다양한 시스템 수준 지표가 30분 테스트 기간에 걸쳐 측정됩니다. 이 기능은 이미지와 PDF 문서를 모두 업로드할 수 있습니다.

   >[!NOTE]
   >성능 테스트 구성에 대한 자세한 내용은 [CI/CD 파이프라인 구성](configuring-pipeline.md)에서 확인할 수 있습니다. 프로그램을 설정하고 KPI를 정의하는 방법에 대해 알아보려면 [프로그램 설정](setting-up-program.md)을 참조하십시오.

### 성능 테스트 결과 그래프 {#performance-testing-results-graphs}

새 그래프 및 다운로드 옵션이 성능 테스트 결과 대화 상자에 추가되었습니다.

[성능 테스트] 대화 상자를 열면 지표 패널을 확장하여 그래프를 표시하거나, 다운로드 링크를 제공하거나, 둘 모두를 제공할 수 있습니다.

[!UICONTROL Cloud Manager] 릴리스 2018.7.0의 경우 이 기능을 다음 지표에 사용할 수 있습니다.

* **CPU 사용**
   * 테스트 기간 동안의 CPU 활용률 그래프.

* **디스크 I/O 대기 시간**
   * 테스트 기간 동안의 디스크 I/O 대기 시간 그래프.

* **페이지 오류 비율**
   * 테스트 기간 동안 분당 페이지 오류 그래프입니다.
   * 테스트 중에 오류가 발생한 페이지를 나열하는 CSV 파일.

* **디스크 대역폭 사용**
   * 테스트 기간 동안의 디스크 대역폭 사용 그래프.

* **네트워크 대역폭 사용**
   * 테스트 기간 동안의 네트워크 대역폭 사용 그래프.

* **최대 응답 시간**
   * 테스트 기간 중 분당 최대 응답 시간에 대한 그래프입니다.

* **95번째 백분위수 응답 시간**
   * 테스트 기간 동안 분당 95번째 백분위수 응답 시간의 그래프.
   * 정의된 KPI를 초과하는 95번째 백분위수 응답 시간을 가진 페이지가 나열된 CSV 파일

다음 이미지에는 성능 테스트 그래프가 표시됩니다.

![](assets/understand_test-results-screen1.png)

![](assets/screen_shot_2018-09-05at83933pm.png)
