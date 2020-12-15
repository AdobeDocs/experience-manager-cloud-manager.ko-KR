---
title: 테스트 결과 이해
seo-title: 테스트 결과 이해
description: 'null'
seo-description: Cloud Manager에서 파이프라인, 코드 스캔, 성능 및 보안 테스트를 실행하는 동안 3개의 계층 게이트에 대해 알아보려면 이 페이지를 따르십시오.
uuid: 93caa01f-0df2-4a6f-81dc-23dfee24dc93
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: using
discoiquuid: 83299ed8-4b7a-4b1c-bd56-1bfc7e7318d4
translation-type: tm+mt
source-git-commit: 39e6af753cdd43da96746c7609a8f502b3ac9e77
workflow-type: tm+mt
source-wordcount: '1544'
ht-degree: 7%

---


# 테스트 결과 이해 {#understand-your-test-results}

파이프라인 실행 중에 비즈니스 소유자가 정의한 주요 성과 지표(KPI) 또는 Adobe Managed Services가 설정한 표준과 비교하여 많은 지표가 캡처되어 비교됩니다.

이 항목은 이 섹션에 정의된 대로 3층 게이팅 시스템을 사용하여 보고됩니다.

## 파이프라인을 실행하는 동안 3계층 게이츠 {#three-tier-gates-while-running-a-pipeline}

파이프라인에는 세 개의 문이 있습니다.

* 코드 품질
* 성능 테스트
* 보안 테스트

이 각각의 게이트에 있어서, 게이트에 의해 식별된 문제에 대한 3층 구조가 있습니다.

* **위험**  - 파이프라인의 즉각적인 실패를 초래하는 게이트로 식별되는 문제입니다.
* **중요**  - 파이프라인이 일시 중지된 상태로 전환되는 게이트로 식별되는 문제입니다. 배포 관리자, 프로젝트 관리자 또는 비즈니스 소유자는 파이프라인이 진행되는 경우 문제를 무시하거나 해당 문제를 허용할 수 있습니다. 이 경우 파이프라인이 오류로 인해 중단됩니다.
* **정보**  - 정보 제공용으로만 제공되고 파이프라인 실행에 영향을 주지 않는 게이트로 식별되는 문제입니다.

>[!NOTE]
>
>코드 품질만 파이프라인에서 코드 품질 테스트 단계가 파이프라인의 마지막 단계이므로 코드 품질 테스트 게이트에서의 중요 오류를 무시할 수 없습니다.

## 코드 품질 테스트 {#code-quality-testing}

이 단계에서는 응용 프로그램 코드의 품질을 평가합니다. 코드 품질만 파이프라인의 핵심 목표이며 비프로덕션 및 프로덕션 파이프라인에서 빌드 단계 바로 다음에 실행됩니다. 다른 유형의 파이프라인에 대한 자세한 내용은 [CI-CD 파이프라인 구성](/help/using/configuring-pipeline.md)을 참조하십시오.

### 코드 품질 테스트 이해 {#understanding-code-quality-testing}

코드 품질 테스트에서 소스 코드가 특정 품질 기준을 충족하는지 확인하기 위해 스캔됩니다. 현재 SonarQube와 OakPAL을 사용하여 컨텐츠 패키지 레벨 검사를 조합하여 구현됩니다. 일반 Java 규칙과 AEM 관련 규칙을 결합하는 100개 이상의 규칙이 있습니다. AEM 관련 규칙 중 일부는 AEM 엔지니어링 우수 사례를 기반으로 만들어지며 [사용자 지정 코드 품질 규칙](/help/using/custom-code-quality-rules.md)이라고 합니다.

>[!NOTE]
>[여기에서 규칙 전체 목록을 다운로드할 수 있습니다](/help/using/assets/CodeQuality-rules-latest.xlsx).

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

**인스턴스** 중 특정 상태 확인에 대한 오류가 보고되는 경우 전체 **환경**&#x200B;에서 해당 상태 확인에 실패합니다. 코드 품질 및 성능 테스트와 마찬가지로 이러한 상태 검사는 카테고리로 분류되어 3계층 게이팅 시스템을 사용하여 보고됩니다. 유일한 차이점은 보안 테스트의 경우 임계값이 없다는 점입니다. 모든 상태 확인은 그냥 통과되거나 실패한다.

다음 표에는 현재 검사가 나열됩니다.

| **이름** | **상태 확인 구현** | **카테고리** |
|---|---|---|
| 비직렬화 방화벽 첨부 API 준비 상태가 허용 상태입니다. | Deserialization Firewall Attach API Readiness | 중요 |
| 비직렬화 방화벽이 사용 가능합니다. | Deserialization Firewall Functional | 중요 |
| 비직렬화 방화벽이 로드됨 | Deserialization Firewall Loaded | 중요 |
| AuthorizableNodeName 구현은 노드 이름/경로에 인증 가능한 ID를 표시하지 않습니다. | 승인 가능한 노드 이름 생성 | 중요 |
| 기본 암호가 변경되었습니다. | 기본 로그인 계정 | 중요 |
| 기본 GET 서블릿은 DOS 공격으로부터 보호됩니다. | Sling Get Servlet | 중요 |
| Sling Java 스크립트 핸들러는 적절하게 구성됩니다 | Sling Java Script Handler | 중요 |
| Sling JSP 스크립트 핸들러는 적절하게 구성되어 있습니다. | Sling JSP Script Handler | 중요 |
| SSL이 올바르게 구성됨 | SSL 구성 | 중요 |
| 안전하지 않은 사용자 프로필 정책을 찾을 수 없음 | 사용자 프로필 기본 액세스 | 중요 |
| CSRF 공격을 방지하기 위해 Sling 레퍼러 필터가 구성되었습니다. | Sling Referrer Filter | 중요 사항 |
| Adobe Granite HTML 라이브러리 관리자가 적절하게 구성되어 있습니다. | CQ HTML 라이브러리 관리자 구성 | 중요 사항 |
| CRXDE 지원 번들을 사용할 수 없음 | CRXDE 지원 | 중요 사항 |
| Sling DavEx 번들 및 서블릿이 비활성화됨 | DavEx 상태 검사 | 중요 사항 |
| 샘플 콘텐트가 설치되지 않았습니다. | 컨텐츠 패키지 예 | 중요 사항 |
| WCM 요청 필터와 WCM 디버그 필터가 모두 비활성화되었습니다. | WCM 필터 구성 | 중요 사항 |
| Sling WebDAV 번들 및 서블릿이 적절하게 구성됨 | WebDAV 상태 검사 | 중요 사항 |
| 웹 서버가 클릭재킹을 방지하도록 구성되었습니다. | 웹 서버 구성 | 중요 사항 |
| 복제에서 &#39;admin&#39; 사용자를 사용하고 있지 않습니다. | 복제 및 전송 사용자 | 정보 |

## 성능 테스트 {#performance-testing}

*성능* 테스트 [!UICONTROL Cloud Manager] 는 30분 테스트를 사용하여 구현됩니다.

파이프라인 설정 중에 배포 관리자는 각 버킷으로 이동할 트래픽의 양을 결정할 수 있습니다.

버킷 제어에 대한 자세한 내용은 [CI/CD 파이프라인 구성](configuring-pipeline.md)을 참조하십시오.

>[!NOTE]
>
>프로그램을 설정하고 KPI를 정의하려면 [프로그램 설정](setting-up-program.md)을 참조하십시오.

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

### 성능 테스트 결과 그래프 {#performance-testing-results-graphs}

새 그래프 및 다운로드 옵션이 성능 테스트 결과 대화 상자에 추가되었습니다.

[성능 테스트] 대화 상자를 열면 지표 패널을 확장하여 그래프를 표시하거나, 다운로드 링크를 제공하거나, 둘 다를 제공할 수 있습니다.

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

