---
title: 맞춤형 코드 품질 규칙
description: 이 페이지에서는 코드 품질 테스트의 일부로 Cloud Manager에서 실행되는 사용자 지정 코드 품질 규칙에 대해 설명합니다. AEM Engineering의 우수 사례를 기반으로 합니다.
uuid: a7feb465-1982-46be-9e57-e67b59849579
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: using
discoiquuid: d2338c74-3278-49e6-a186-6ef62362509f
feature: Code Quality Rules
exl-id: 7d118225-5826-434e-8869-01ee186e0754
source-git-commit: 834508109e34eb1e052abac482e981735c72d43d
workflow-type: tm+mt
source-wordcount: '3611'
ht-degree: 3%

---


# 맞춤형 코드 품질 규칙 {#custom-code-quality-rules}

이 페이지에서는 Cloud Manager가 의 일부로 실행하는 사용자 지정 코드 품질 규칙에 대해 설명합니다 [코드 품질 테스트.](understand-your-test-results.md) AEM Engineering의 우수 사례를 기반으로 합니다.

>[!NOTE]
>
>AEM as a Cloud Service에서 Cloud Manager의 사용자 지정 코드 품질 규칙에 대한 자세한 내용은 다음을 참조하십시오 [참조하십시오.](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/test-results/custom-code-quality-rules.html#using-cloud-manager).

>[!NOTE]
>
>여기에 제공된 코드 샘플은 예시적인 용도로만 제공됩니다. 자세한 내용은 [SonarQube의 개념 설명서](https://docs.sonarqube.org/7.4/user-guide/concepts/) 개념 및 품질 규칙에 대해 알아봅니다.

## SonarQube 규칙 {#sonarqube-rules}

다음 섹션에서는 Cloud Manager에서 실행되는 SonarQube 규칙에 대해 자세히 설명합니다.

### 위험한 기능 사용 안 함 {#do-not-use-potentially-dangerous-functions}

* **키**: CQRules:CWE-676
* **유형**: 취약성
* **심각도**: 주요
* **이후**: 버전 2018.4.0

메서드 `Thread.stop()` 및 `Thread.interrupt()` 는 재현하기 어려운 문제와 경우에 따라 보안 취약점을 생성할 수 있습니다. Their usage should be tightly monitored and validated. In general, message passing is a safer way to accomplish similar goals.

#### 비호환 코드 {#non-compliant-code}

```java
public class DontDoThis implements Runnable {
  private Thread thread;
 
  public void start() {
    thread = new Thread(this);
    thread.start();
  }
 
  public void stop() {
    thread.stop();  // UNSAFE!
  }
 
  public void run() {
    while (true) {
        somethingWhichTakesAWhileToDo();
    }
  }
}
```

#### 호환 코드 {#compliant-code}

```java
public class DoThis implements Runnable {
  private Thread thread;
  private boolean keepGoing = true;
 
  public void start() {
    thread = new Thread(this);
    thread.start();
  }
 
  public void stop() {
    keepGoing = false;
  }
 
  public void run() {
    while (this.keepGoing) {
        somethingWhichTakesAWhileToDo();
    }
  }
}
```

### 외부에서 제어할 수 있는 형식 문자열을 사용하지 마십시오. {#do-not-use-format-strings-which-may-be-externally-controlled}

* **키**: CQRules:CWE-134
* **유형**: 취약성
* **심각도**: 주요
* **이후**: 버전 2018.4.0

외부 소스의 형식 문자열(예: 요청 매개 변수 또는 사용자 생성 컨텐츠)을 사용하면 응용 프로그램이 서비스 거부 공격을 받을 수 있습니다. 형식 문자열을 외부에서 제어할 수 있지만 신뢰할 수 있는 소스에서만 허용됩니다.

#### 비호환 코드 {#non-compliant-code-1}

```java
protected void doPost(SlingHttpServletRequest request, SlingHttpServletResponse response) {
  String messageFormat = request.getParameter("messageFormat");
  request.getResource().getValueMap().put("some property", String.format(messageFormat, "some text"));
  response.sendStatus(HttpServletResponse.SC_OK);
}
```

### HTTP 요청에는 항상 소켓 및 연결 시간 초과가 있어야 합니다. {#http-requests-should-always-have-socket-and-connect-timeouts}

* **키**: CQRules:ConnectionTimeoutMechanism
* **유형**: 버그
* **심각도**: 중요
* **이후**: 버전 2018.6.0

AEM 애플리케이션 내에서 HTTP 요청을 실행할 때 불필요한 스레드 사용을 방지하기 위해 적절한 시간 초과가 구성되어 있는지 확인해야 합니다. 안타깝게도 Java의 기본 HTTP 클라이언트인 `java.net.HttpUrlConnection`및 일반적으로 사용되는 Apache HTTP 구성 요소 클라이언트는 시간 제한을 두지 않으므로 시간 초과를 명시적으로 설정해야 합니다. 가장 좋은 방법으로서, 이러한 시간 초과는 60초 이내여야 합니다.

#### 비호환 코드 {#non-compliant-code-2}

```java
@Reference
private HttpClientBuilderFactory httpClientBuilderFactory;
 
public void dontDoThis() {
  HttpClientBuilder builder = httpClientBuilderFactory.newBuilder();
  HttpClient httpClient = builder.build();

  // do something with the client
}

public void dontDoThisEither() {
  URL url = new URL("http://www.google.com");
  URLConnection urlConnection = url.openConnection();
 
  BufferedReader in = new BufferedReader(new InputStreamReader(
    urlConnection.getInputStream()));
 
  String inputLine;
  while ((inputLine = in.readLine()) != null) {
    logger.info(inputLine);
  }
 
  in.close();
}
```

#### 호환 코드 {#compliant-code-1}

```java
@Reference
private HttpClientBuilderFactory httpClientBuilderFactory;
 
public void doThis() {
  HttpClientBuilder builder = httpClientBuilderFactory.newBuilder();
  RequestConfig requestConfig = RequestConfig.custom()
    .setConnectTimeout(5000)
    .setSocketTimeout(5000)
    .build();
  builder.setDefaultRequestConfig(requestConfig);
 
  HttpClient httpClient = builder.build();
   
  // do something with the client
}

public void orDoThis() {
  URL url = new URL("http://www.google.com");
  URLConnection urlConnection = url.openConnection();
  urlConnection.setConnectTimeout(5000);
  urlConnection.setReadTimeout(5000);
 
  BufferedReader in = new BufferedReader(new InputStreamReader(
    urlConnection.getInputStream()));
 
  String inputLine;
  while ((inputLine = in.readLine()) != null) {
    logger.info(inputLine);
  }
 
  in.close();
}
```

### ResourceResolver 개체는 항상 닫아야 합니다. {#resourceresolver-objects-should-always-be-closed}

* **키**: CQRules:CQBP-72
* **유형**: 코드 냄새
* **심각도**: 주요
* **이후**: 버전 2018.4.0

`ResourceResolver` 에서 가져온 객체 `ResourceResolverFactory` 시스템 리소스를 사용합니다. 이러한 리소스를 재생하기 위한 적절한 조치가 있지만 `ResourceResolver` 는 더 이상 사용되지 않으므로 열려 있는 항목을 명시적으로 닫는 것이 더 효율적입니다 `ResourceResolver` 를 호출하여 개체를 `close()` 메서드를 사용합니다.

비교적 일반적인 오해는 `ResourceResolver` 기존 JCR 세션을 사용하여 만든 개체는 명시적으로 닫으면 안 되며, 이렇게 하면 기본 JCR 세션이 닫힙니다. 그렇지 않습니다. Analytics Mobile Apps 또는 Analytics Premium이 `ResourceResolver` 가 열려 있으면 더 이상 사용하지 않을 때 닫아야 합니다. 이후 `ResourceResolver` 구현 `Closeable` 인터페이스, 또한 `try-with-resources` 구문 대신 를 명시적으로 호출하는 것입니다. `close()`.

#### 비호환 코드 {#non-compliant-code-4}

```java
public void dontDoThis(Session session) throws Exception {
  ResourceResolver resolver = factory.getResourceResolver(Collections.singletonMap("user.jcr.session", (Object)session));
  // do some stuff with the resolver
}
```

#### 호환 코드 {#compliant-code-2}

```java
public void doThis(Session session) throws Exception {
  ResourceResolver resolver = null;
  try {
    resolver = factory.getResourceResolver(Collections.singletonMap("user.jcr.session", (Object)session));
    // do something with the resolver
  } finally {
    if (resolver != null) {
      resolver.close();
    }
  }
}

public void orDoThis(Session session) throws Exception {
  try (ResourceResolver resolver = factory.getResourceResolver(Collections.singletonMap("user.jcr.session", (Object) session))){
    // do something with the resolver
  }
}
```

### Sling 서블릿 경로를 사용하여 서블릿을 등록하지 마십시오 {#do-not-use-sling-servlet-paths-to-register-servlets}

* **키**: CQRules:CQBP-75
* **유형**: 코드 냄새
* **심각도**: 주요
* **이후**: 버전 2018.4.0

에 설명된 대로 [Sling 설명서](http://sling.apache.org/documentation/the-sling-engine/servlets.html)인 경우 경로별 바인딩 서블릿이 비활성화됩니다. 경로 바인딩된 서블릿은 표준 JCR 액세스 제어를 사용할 수 없으므로 추가 보안 권한이 필요합니다. 경로 바인딩된 서블릿을 사용하는 대신 저장소에서 노드를 만들고 리소스 유형별로 서블릿을 등록하는 것이 좋습니다.

#### 비호환 코드 {#non-compliant-code-5}

```java
@Component(property = {
  "sling.servlet.paths=/apps/myco/endpoint"
})
public class DontDoThis extends SlingAllMethodsServlet {
 // implementation
}
```

### catch 예외가 기록되거나 throw되어야 하며, 둘 다 예외가 아닙니다. {#caught-exceptions-should-be-logged-or-thrown-but-not-both}

* **키**: CQRules:CQBP-44—CatchAndEtherLogOrThrow
* **유형**: 코드 냄새
* **심각도**: Minor
* **이후**: 버전 2018.4.0

일반적으로 예외는 정확히 한 번만 기록되어야 합니다. 예외를 여러 번 로깅하면 예외가 몇 번 발생했는지 확실하지 않으므로 혼동을 일으킬 수 있습니다. 이를 유도하는 가장 일반적인 패턴은 로깅 및 catch 예외를 throw하는 것입니다.

#### 비호환 코드 {#non-compliant-code-6}

```java
public void dontDoThis() throws Exception {
  try {
    someOperation();
  } catch (Exception e) {
    logger.error("something went wrong", e);
    throw e;
  }
}
```

#### 호환 코드 {#compliant-code-3}

```java
public void doThis() {
  try {
    someOperation();
  } catch (Exception e) {
    logger.error("something went wrong", e);
  }
}

public void orDoThis() throws MyCustomException {
  try {
    someOperation();
  } catch (Exception e) {
    throw new MyCustomException(e);
  }
}
```

### Throw 문이 바로 뒤에 오는 Log 문 방지 {#avoid-having-a-log-statement-immediately-followed-by-a-throw-statement}

* **키**: CQRules:CQBP-44—ContinuousLogAndThrow
* **유형**: 코드 냄새
* **심각도**: Minor
* **이후**: 버전 2018.4.0

메시지를 로깅한 다음 즉시 예외를 throw하는 것을 방지하는 또 다른 일반적인 패턴입니다. 일반적으로 이는 예외 메시지가 로그 파일에 복제된다는 것을 나타냅니다.

#### 비호환 코드 {#non-compliant-code-7}

```java
public void dontDoThis() throws Exception {
  logger.error("something went wrong");
  throw new RuntimeException("something went wrong");
}
```

#### 호환 코드 {#compliant-code-4}

```java
public void doThis() throws Exception {
  throw new RuntimeException("something went wrong");
}
```

### GET 또는 HEAD 요청을 처리할 때 INFO에서 로깅 방지 {#avoid-logging-at-info-when-handling-get-or-head-requests}

* **키**: CQRules:CQBP-44—LogInfoInGetOrHeadRequests
* **유형**: 코드 냄새
* **심각도**: Minor

일반적으로 INFO 로그 수준을 사용하여 중요한 작업을 구분해야 하며 기본적으로 AEM은 INFO 수준 이상으로 로그온하도록 구성되어 있습니다. GET 및 HEAD 방법은 읽기 전용 작업만 수행되어야 하므로 중요한 작업을 구성하지 않습니다. GET 또는 HEAD 요청에 응답하여 INFO 수준에서 로그인하면 상당한 로그 노이즈가 발생할 수 있으므로 로그 파일에서 유용한 정보를 식별하기가 어렵습니다. GET 또는 HEAD 요청을 처리할 때 로깅은 문제가 발생한 경우 WARN 또는 ERROR 수준에서, 또는 문제 해결 정보가 유용할 경우 DEBUG 또는 TRACE 수준에서 로깅해야 합니다.

>[!NOTE]
>
>각 요청에 대한 access.log-type 로깅에는 적용되지 않습니다.

#### 비호환 코드 {#non-compliant-code-8}

```java
public void doGet() throws Exception {
  logger.info("handling a request from the user");
}
```

#### 호환 코드 {#compliant-code-5}

```java
public void doGet() throws Exception {
  logger.debug("handling a request from the user.");
}
```

### Exception.getMessage()를 Logging 문의 첫 번째 매개 변수로 사용하지 마십시오. {#do-not-use-exception-getmessage-as-the-first-parameter-of-a-logging-statement}

* **키**: CQRules:CQBP-44—ExceptionGetMessageIsFirstLogParam
* **유형**: 코드 냄새
* **심각도**: Minor
* **이후**: 버전 2018.4.0

로그 메시지는 애플리케이션에서 예외가 발생한 위치에 대한 컨텍스트 정보를 제공하는 것이 좋습니다. 스택 추적을 사용하여 컨텍스트를 결정할 수도 있지만 일반적으로 로그 메시지는 읽고 이해하는 것이 더 쉽습니다. 따라서, 예외를 기록할 때 예외 메시지를 로그 메시지로 사용하는 것이 좋습니다. 예외 메시지에는 잘못된 내용이 포함되지만, 로그 메시지는 예외가 발생했을 때 애플리케이션이 어떤 작업을 수행했는지 로그 판독기에 알리는 데 사용해야 합니다. 예외 메시지가 계속 기록됩니다. 고유한 메시지를 지정하여 로그를 쉽게 이해할 수 있습니다.

#### 비호환 코드 {#non-compliant-code-9}

```java
public void dontDoThis() {
  try {
    someMethodThrowingAnException();
  } catch (Exception e) {
    logger.error(e.getMessage(), e);
  }
}
```

#### 호환 코드 {#compliant-code-6}

```java
public void doThis() {
  try {
    someMethodThrowingAnException();
  } catch (Exception e) {
    logger.error("Unable to do something", e);
  }
}
```

### catch 블록에 로그인하는 것은 경고 또는 오류 수준이어야 합니다. {#logging-in-catch-blocks-should-be-at-the-warn-or-error-level}

* **키**: CQRules:CQBP-44—WrongLogLevelInCatchBlock
* **유형**: 코드 냄새
* **심각도**: Minor
* **이후**: 버전 2018.4.0

이름에서 알 수 있듯이 예외사항은 항상 예외적인 상황에서 사용해야 합니다. 따라서 예외가 발생했을 때 로그 메시지가 적절한 수준에서 기록되도록 하는 것이 중요합니다. 경고 또는 오류입니다. 이렇게 하면 해당 메시지가 로그에 올바르게 표시됩니다.

#### 비호환 코드 {#non-compliant-code-10}

```java
public void dontDoThis() {
  try {
    someMethodThrowingAnException();
  } catch (Exception e) {
    logger.debug(e.getMessage(), e);
  }
}
```

#### 호환 코드 {#compliant-code-7}

```java
public void doThis() {
  try {
    someMethodThrowingAnException();
  } catch (Exception e) {
    logger.error("Unable to do something", e);
  }
}
```

### 콘솔에 스택 추적을 인쇄하지 않음 {#do-not-print-stack-traces-to-the-console}

* **키**: CQRules:CQBP-44—ExceptionPrintStackTrace
* **유형**: 코드 냄새
* **심각도**: Minor
* **이후**: 버전 2018.4.0

로그 메시지를 이해할 때 컨텍스트는 매우 중요합니다. 사용 `Exception.printStackTrace()` 스택 추적만 표준 오류 스트림으로 출력되도록 하여 모든 컨텍스트를 잃게 합니다. 또한 AEM과 같은 다중 스레드 애플리케이션에서 이 방법을 동시에 사용하여 여러 예외가 인쇄되는 경우 스택 추적이 겹쳐서 상당한 혼동을 일으킬 수 있습니다. 예외는 로깅 프레임워크를 통해서만 로깅해야 합니다.

#### 비호환 코드 {#non-compliant-code-11}

```java
public void dontDoThis() {
  try {
    someMethodThrowingAnException();
  } catch (Exception e) {
    e.printStackTrace();
  }
}
```

#### 호환 코드 {#compliant-code-8}

```java
public void doThis() {
  try {
    someMethodThrowingAnException();
  } catch (Exception e) {
    logger.error("Unable to do something", e);
  }
}
```

### 표준 출력 또는 표준 오류로 출력하지 않음 {#do-not-output-to-standard-output-or-standard-error}

* **키**: CQRules:CQBP-44—LogLevelConsolePrinters
* **유형**: 코드 냄새
* **심각도**: Minor
* **이후**: 버전 2018.4.0

AEM에서 로그인하는 작업은 항상 로깅 프레임워크인 SLF4J를 통해 수행해야 합니다. 표준 출력 또는 표준 오류 스트림에 직접 출력하면 로깅 프레임워크에서 제공하는 구조적 및 컨텍스트 정보가 손실되며, 경우에 따라 성능 문제가 발생할 수 있습니다.

#### 비호환 코드 {#non-compliant-code-12}

```java
public void dontDoThis() {
  try {
    someMethodThrowingAnException();
  } catch (Exception e) {
    System.err.println("Unable to do something");
  }
}
```

#### 호환 코드 {#compliant-code-9}

```java
public void doThis() {
  try {
    someMethodThrowingAnException();
  } catch (Exception e) {
    logger.error("Unable to do something", e);
  }
}
```

### 하드코딩된 /apps 및 /libs 경로 방지 {#avoid-hardcoded-apps-and-libs-paths}

* **키**: CQRules:CQBP-71
* **유형**: 코드 냄새
* **심각도**: Minor
* **이후**: 버전 2018.4.0

일반적으로 다음으로 시작하는 경로 `/libs` 및 `/apps` 참조하는 경로가 Sling 검색 경로에 상대적인 경로로 가장 일반적으로 저장되므로 하드코딩하지 않아야 합니다. 이 경로는 `/libs,/apps` 기본적으로 ). 절대 경로를 사용하면 프로젝트 라이프사이클에서 나중에 나타날 수 있는 미묘한 결함이 발생할 수 있습니다.

#### 비호환 코드 {#non-compliant-code-13}

```java
public boolean dontDoThis(Resource resource) {
  return resource.isResourceType("/libs/foundation/components/text");
}
```

#### 호환 코드 {#compliant-code-10}

```java
public void doThis(Resource resource) {
  return resource.isResourceType("foundation/components/text");
}
```

### Sling 스케줄러는 사용하지 않아야 합니다. {#sonarqube-sling-scheduler}

* **키**: CQRules:AMSCORE-554
* **유형**: 코드 냄새/Cloud Service 호환성
* **심각도**: Minor
* **이후**: 버전 2020.5.0

Sling 스케줄러는 보장된 실행을 필요로 하는 작업에 사용해서는 안 됩니다. Sling 예약된 작업은 실행이 보장되며, 클러스터링된 환경과 비클러스터형 환경 모두에 더 적합합니다.

을(를) 참조하십시오. [Apache Sling 이벤트 및 작업 처리 설명서](https://sling.apache.org/documentation/bundles/apache-sling-eventing-and-job-handling.html) 클러스터 환경에서 Sling 작업을 처리하는 방법에 대해 자세히 알아보십시오.

### AEM에서 더 이상 사용되지 않는 API는 사용하지 않아야 합니다. {#sonarqube-aem-deprecated}

* **키**: AMSCORE-553
* **유형**: 코드 냄새/Cloud Service 호환성
* **심각도**: Minor
* **이후**: 버전 2020.5.0

AEM API 서피스는 사용이 중단되어 더 이상 사용되지 않는 API를 식별하기 위해 상수 개정 아래에 있습니다.

대부분의 경우 이러한 API는 표준 Java를 사용하여 더 이상 사용되지 않습니다 *@Deprecated* 주석 및 기타, `squid:CallToDeprecatedMethod`.

그러나 API는 AEM 컨텍스트에서 더 이상 사용되지 않지만 다른 컨텍스트에서 더 이상 사용되지 않는 경우가 있습니다. 이 규칙은 이 두 번째 클래스를 식별합니다.

## OakPAL 콘텐츠 규칙 {#oakpal-rules}

다음 섹션에서는 Cloud Manager에서 실행되는 OakPAL 검사에 대해 자세히 설명합니다.

>[!NOTE]
>
>OakPAL은 독립형 Oak 저장소를 사용하여 컨텐츠 패키지를 확인하는 프레임워크입니다. AEM 파트너에 의해 개발되었으며 2019 AEM 록스타 노스 아메리카 상을 수상한 바 있다.

### 고객이 구현하거나 확장하면 @ProviderType으로 주석을 단 제품 API {#product-apis-annotated-with-providertype-should-not-be-implemented-or-extended-by-customers}

* **키**: CQBP-84
* **유형**: 버그
* **심각도**: 중요
* **이후**: 버전 2018.7.0

The AEM API contains Java interfaces and classes which are only meant to be used, but not implemented, by custom code. For example, the interface `com.day.cq.wcm.api.Page` is designed to be implemented by AEM only.

When new methods are added to these interfaces, those additional methods do not impact existing code which uses these interfaces and, as a result, the addition of new methods to these interfaces are considered to be backwards-compatible. However, if custom code implements one of these interfaces, that custom code has introduced a backwards-compatibility risk for the customer.

AEM에서 구현하기 위한 인터페이스 및 클래스에는 `org.osgi.annotation.versioning.ProviderType` 또는 경우에 따라 유사한 이전 주석 `aQute.bnd.annotation.ProviderType`. 이 규칙은 인터페이스가 구현되거나 사용자 지정 코드에 의해 클래스가 확장된 경우를 식별합니다.

#### 비호환 코드 {#non-compliant-code-3}

```java
import com.day.cq.wcm.api.Page;

public class DontDoThis implements Page {
// implementation here
}
```

### 고객 패키지는 /libs 아래에 노드를 만들거나 수정해서는 안 됩니다. {#oakpal-customer-package}

* **키**: 금지된 경로
* **유형**: 버그
* **심각도**: 차단기
* **이후**: 버전 2019.6.0

그것은 오랫동안 지켜온 가장 좋은 방법이었습니다 `/libs` AEM 컨텐츠 저장소의 컨텐츠 트리는 고객이 읽기 전용으로 간주해야 합니다. 아래의 노드 및 속성 수정 `/libs` 주요 업데이트 및 부분 업데이트에 심각한 위험 요소 생성 수정 사항 `/libs` Adobe이 공식 채널을 통해야만 한다.

### 패키지에 중복 OSGi 구성이 포함되어 있지 않아야 합니다. {#oakpal-package-osgi}

* **키**: DuplicateOsgiConfigurations
* **유형**: 버그
* **심각도**: 주요
* **이후**: 버전 2019.6.0

복잡한 프로젝트에서 발생하는 일반적인 문제는 동일한 OSGi 구성 요소가 여러 번 구성된 경우입니다. 이렇게 하면 작동 가능한 구성이 모호해집니다. 이 규칙은 동일한 런타임 모드 또는 런타임 모드의 조합에서 동일한 구성 요소가 여러 번 구성되는 문제만 식별한다는 점에서 &quot;실행 모드 인식&quot;입니다.

#### 비호환 코드 {#non-compliant-code-osgi}

```text
+ apps
  + projectA
    + config
      + com.day.cq.commons.impl.ExternalizerImpl
  + projectB
    + config
      + com.day.cq.commons.impl.ExternalizerImpl
```

#### 호환 코드 {#compliant-code-osgi}

```text
+ apps
  + shared-config
    + config
      + com.day.cq.commons.impl.ExternalizerImpl
```

### 구성 및 설치 폴더에는 OSGi 노드만 포함되어야 합니다. {#oakpal-config-install}

* **키**: ConfigAndInstallShouldOnlyContainOsgiNodes
* **유형**: 버그
* **심각도**: 주요
* **이후**: 버전 2019.6.0

보안상의 이유로 `/config/` 및 `/install/` 는 AEM의 관리 사용자만 읽을 수 있으며 OSGi 구성 및 OSGi 번들에만 사용해야 합니다. 이러한 세그먼트가 들어 있는 경로에 다른 유형의 컨텐츠를 배치하면 관리 사용자와 비관리 사용자 간에 실수로 변하는 애플리케이션 동작이 발생합니다.

일반적인 문제는 `config` 구성 요소 대화 상자 내에서 또는 인라인 편집을 위한 리치 텍스트 편집기 구성을 지정할 때. 이를 해결하려면 해당 노드의 이름을 호환 이름으로 변경해야 합니다. 리치 텍스트 편집기 구성의 경우 `configPath` 속성 `cq:inplaceEditing` 노드 아래에 새 위치를 지정합니다.

#### 비호환 코드 {#non-compliant-code-config-install}

```text
+ cq:editConfig [cq:EditConfig]
  + cq:inplaceEditing [cq:InplaceEditConfig]
    + config [nt:unstructured]
      + rtePlugins [nt:unstructured]
```

#### 호환 코드 {#compliant-code-config-install}

```text
+ cq:editConfig [cq:EditConfig]
  + cq:inplaceEditing [cq:InplaceEditConfig]
    ./configPath = inplaceEditingConfig (String)
    + inplaceEditingConfig [nt:unstructured]
      + rtePlugins [nt:unstructured]
```

### 패키지는 겹치지 않아야 합니다. {#oakpal-no-overlap}

* **키**: PackageOverlap
* **유형**: 버그
* **심각도**: 주요
* **이후**: 버전 2019.6.0

와 비슷합니다 [패키지에 중복 OSGi 구성 규칙이 포함되어 있지 않아야 합니다.](#oakpal-package-osgi)  이는 여러 개의 개별 컨텐츠 패키지로 동일한 노드 경로를 쓰는 복잡한 프로젝트에서 일반적으로 발생하는 문제입니다. 컨텐츠 패키지 종속성을 사용하여 일관된 결과를 보장할 수 있지만 완전히 겹치지 않는 것이 좋습니다.

### 기본 작성 모드는 클래식 UI가 아니어야 합니다. {#oakpal-default-authoring}

* **키**: ClassicUI작성 모드
* **유형**: 코드 냄새/Cloud Service 호환성
* **심각도**: Minor
* **이후**: 버전 2020.5.0

OSGi 구성 `com.day.cq.wcm.core.impl.AuthoringUIModeServiceImpl` AEM 내에서 기본 작성 모드를 정의합니다. 왜냐면 [클래식 UI는 AEM 6.4 이후 더 이상 사용되지 않습니다.](https://experienceleague.adobe.com/docs/experience-manager-64/release-notes/deprecated-removed-features.html) 기본 작성 모드가 클래식 UI로 구성되어 있으면 문제가 발생합니다.

### 대화 상자가 있는 구성 요소에는 Touch UI 대화 상자가 있어야 합니다. {#oakpal-components-dialogs}

* **키**: ComponentWithOnlyClassicUIDialog
* **유형**: 코드 냄새/Cloud Service 호환성
* **심각도**: Minor
* **이후**: 버전 2020.5.0

클래식 UI 대화 상자가 있는 AEM 구성 요소에는 항상 해당 터치 UI 대화 상자가 있어야 최적의 작성 경험을 제공하고 클래식 UI가 지원되지 않는 Cloud Service 배포 모델과 호환됩니다. 이 규칙은 다음 시나리오를 확인합니다.

* 클래식 UI 대화 상자(즉, `dialog` 하위 노드)에는 해당 터치 UI 대화 상자(즉, `cq:dialog` 하위 노드).
* 클래식 UI 디자인 대화 상자(예: `design_dialog` 노드)에는 해당 Touch UI 디자인 대화 상자(즉, `cq:design_dialog` 하위 노드).
* 클래식 UI 대화 상자와 클래식 UI 디자인 대화 상자가 모두 있는 구성 요소에는 해당 터치 UI 대화 상자와 해당 터치 UI 디자인 대화 상자가 모두 있어야 합니다.

AEM 현대화 도구 설명서는 구성 요소를 클래식 UI에서 Touch UI로 변환하는 방법에 대한 세부 사항 및 도구를 제공합니다. 을(를) 참조하십시오. [AEM 현대화 도구 설명서 ](https://opensource.adobe.com/aem-modernize-tools/pages/tools.html) 자세한 내용

### 패키지는 가변 콘텐츠와 변경할 수 없는 콘텐츠를 혼합하지 않아야 합니다. {#oakpal-packages-immutable}

* **키**: 가변 가능 혼합 패키지
* **유형**: 코드 냄새/Cloud Service 호환성
* **심각도**: Minor
* **이후**: 버전 2020.5.0

Cloud Service 배포 모델과 호환되려면 개별 컨텐츠 패키지에 저장소의 변경할 수 없는 영역에 대한 컨텐츠(즉, `/apps` 및 `/libs`) 또는 변경할 수 있는 영역(즉, 에 없는 모든 것) `/apps` 또는 `/libs`). 예를 들어, 두 가지 모두를 포함하는 패키지 `/apps/myco/components/text and /etc/clientlibs/myco` 는 Cloud Service과 호환되지 않으므로 문제가 보고됩니다.

을(를) 참조하십시오. [AEM 프로젝트 구조 설명서](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/aem-project-content-package-structure.html) 자세한 내용

>[!NOTE]
>
>규칙 [고객 패키지는 /libs 아래에 노드를 만들거나 수정해서는 안 됩니다.](#oakpal-customer-package) 항상 적용됩니다.

### 역방향 복제 에이전트 사용 안 함 {#oakpal-reverse-replication}

* **키**: 역복제
* **유형**: 코드 냄새/Cloud Service 호환성
* **심각도**: Minor
* **이후**: 버전 2020.5.0

에 설명된 대로 역방향 복제를 지원하는 것은 Cloud Service 배포에서 사용할 수 없습니다. [릴리스 노트: 복제 에이전트 제거.](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/release-notes/aem-cloud-changes.html#replication-agents)

역방향 복제를 사용하는 고객은 대체 솔루션을 사용하려면 Adobe에 문의해야 합니다.

### 프록시가 활성화된 클라이언트 라이브러리에 포함된 리소스는 리소스라는 폴더에 있어야 합니다. {#oakpal-resources-proxy}

* **키**: ClientlibProxyResource
* **유형**: 버그
* **심각도**: Minor
* **이후**: 버전 2021.2.0

AEM 클라이언트 라이브러리에는 이미지 및 글꼴과 같은 정적 리소스가 포함될 수 있습니다. 에 설명된 대로 [클라이언트측 라이브러리 설명서 사용,](https://experienceleague.adobe.com/docs/experience-manager-65/developing/introduction/clientlibs.html#using-preprocessors) proxied 클라이언트 라이브러리를 사용할 때는 이러한 정적 리소스를 `resources` 게시 인스턴스에서 효과적으로 참조할 수 있습니다.

#### 비호환 코드 {#non-compliant-proxy-enabled}

```text
+ apps
  + projectA
    + clientlib
      - allowProxy=true
      + images
        + myimage.jpg
```

#### 호환 코드 {#compliant-proxy-enabled}

```text
+ apps
  + projectA
    + clientlib
      - allowProxy=true
      + resources
        + myimage.jpg
```

### 호환되지 않는 워크플로우 프로세스 Cloud Service 사용 {#oakpal-usage-cloud-service}

* **키**: CloudService호환되지 않는 WorkflowProcess
* **유형**: 코드 냄새
* **심각도**: 차단기
* **이후**: 버전 2021.2.0

AEM Cloud Service에서 자산 처리를 위해 Asset Micro-services로 이동하면서 AEM의 온프레미스 및 AMS 버전에서 사용된 몇 가지 워크플로우 프로세스가 지원되지 않거나 필요하지 않게 되었습니다.

의 마이그레이션 도구 [AEM Assets as a Cloud Service GitHub 저장소](https://github.com/adobe/aem-cloud-migration) AEM as a Cloud Service으로 마이그레이션하는 동안 워크플로우 모델을 업데이트하는 데 사용할 수 있습니다.

### 정적 템플릿 사용이 편집 가능한 템플릿을 위해 중단됩니다 {#oakpal-static-template}

* **키**: 정적 템플릿 사용
* **유형**: 코드 냄새
* **심각도**: Minor
* **이후**: 버전 2021.2.0

이전에는 AEM 프로젝트에서 정적 템플릿을 사용하는 것이 매우 일반적이었지만 편집 가능한 템플릿은 정적 템플릿에 없는 가장 유연한 기능을 제공하고 추가 기능을 지원하기 때문에 적극 권장됩니다. 자세한 내용은 [페이지 템플릿 - 편집 가능한 설명서.](https://experienceleague.adobe.com/docs/experience-manager-65/developing/platform/templates/page-templates-editable.html)

정적 템플릿에서 편집 가능한 템플릿으로 마이그레이션은 [AEM 현대화 도구.](https://opensource.adobe.com/aem-modernize-tools/)

### 레거시 기초 구성 요소 사용이 중단되었습니다. {#oakpal-usage-legacy}

* **키**: LegacyFoundationComponentUsage
* **유형**: 코드 냄새
* **심각도**: Minor
* **이후**: 버전 2021.2.0

기존 기초 구성 요소(즉, `/libs/foundation`)은 일부 AEM 릴리스에서 더 이상 사용되지 않으며, [핵심 구성 요소.](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html?lang=ko-KR) 오버레이든 상속이든 사용자 지정 구성 요소의 기준으로서 레거시 기초 구성 요소의 사용은 금지되어 있으므로 해당 코어 구성 요소로 변환해야 합니다.

이 변환은 다음을 통해 용이하게 할 수 있습니다 [AEM 현대화 도구.](https://opensource.adobe.com/aem-modernize-tools/)

### 지원되는 런타임 모드 이름 및 순서 지정만 사용해야 합니다. {#oakpal-supported-runmodes}

* **키**: 지원되는 실행 모드
* **유형**: 코드 냄새
* **심각도**: Minor
* **이후**: 버전 2021.2.0

AEM Cloud Service에서는 런타임 모드 이름에 엄격한 이름 지정 정책을 적용하고 이러한 런타임 모드에 대해 엄격한 순서를 지정합니다. 지원되는 실행 모드 목록은 [AEM as a Cloud Service 설명서에 배포](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/deploying/overview.html#runmodes) 그리고 이로부터 오는 모든 편차는 문제로 식별됩니다.

### 사용자 지정 검색 색인 정의 노드는 /oak:index의 직접 하위 노드여야 합니다. {#oakpal-custom-search}

* **키**: OakIndexLocation
* **유형**: 코드 냄새
* **심각도**: Minor
* **이후**: 버전 2021.2.0

AEM Cloud Service에는 사용자 지정 검색 색인 정의(예: 유형의 노드)가 필요합니다 `oak:QueryIndexDefinition`)의 직접 하위 노드 `/oak:index`. 다른 위치의 인덱스를 AEM Cloud Service과 호환되도록 이동해야 합니다. 검색 인덱스에 대한 자세한 내용은 [컨텐츠 검색 및 색인 지정 설명서입니다.](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/operations/indexing.html)

### 사용자 지정 검색 색인 정의 노드에는 compatVersion 2 가 있어야 합니다. {#oakpal-custom-search-compatVersion}

* **키**: IndexCompatVersion
* **유형**: 코드 냄새
* **심각도**: Minor
* **이후**: 버전 2021.2.0

AEM Cloud Service에는 사용자 지정 검색 색인 정의(예: 유형의 노드)가 필요합니다 `oak:QueryIndexDefinition`)에는 가 있어야 합니다. `compatVersion` 속성 설정 `2`. 다른 값은 AEM Cloud Service에서 지원되지 않습니다. 검색 인덱스에 대한 자세한 내용은 [컨텐츠 검색 및 색인 지정 설명서입니다.](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/operations/indexing.html)

### 사용자 지정 검색 색인 정의 노드의 하위 노드는 nt:unrecordinated 형식이어야 합니다. {#oakpal-descendent-nodes}

* **키**: IndexDescendantNodeType
* **유형**: 코드 냄새
* **심각도**: Minor
* **이후**: 버전 2021.2.0

사용자 지정 검색 색인 정의 노드에 순서가 없는 하위 노드가 있을 때 문제를 해결하기 어려울 수 있습니다. 이를 방지하려면 `oak:QueryIndexDefinition` 노드 유형 `nt:unstructured`.

### 사용자 지정 검색 색인 정의 노드에는 하위 노드가 있는 indexRules라는 하위 노드가 있어야 합니다. {#oakpal-custom-search-index}

* **키**: IndexRulesNode
* **유형**: 코드 냄새
* **심각도**: Minor
* **이후**: 버전 2021.2.0

올바르게 정의된 사용자 지정 검색 색인 정의 노드에는 이름이 인 하위 노드가 있어야 합니다. `indexRules` 이 경우 적어도 한 명의 자녀가 있어야 합니다. 자세한 내용은 [Oak 설명서.](https://jackrabbit.apache.org/oak/docs/query/lucene.html)

### 사용자 지정 검색 색인 정의 노드는 이름 지정 규칙을 따라야 합니다. {#oakpal-custom-search-definitions}

* **키**: IndexName
* **유형**: 코드 냄새
* **심각도**: Minor
* **이후**: 버전 2021.2.0

AEM Cloud Service에는 사용자 지정 검색 색인 정의(즉, 유형 노드)가 필요합니다 `oak:QueryIndexDefinition`)에 대해 설명하는 특정 패턴에 따라 이름을 지정해야 합니다. [컨텐츠 검색 및 색인 지정](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/operations/indexing.html#how-to-use)

### 사용자 지정 검색 색인 정의 노드는 인덱스 유형 lucene을 사용해야 합니다.  {#oakpal-index-type-lucene}

* **키**: 인덱스 유형
* **유형**: 코드 냄새
* **심각도**: Minor
* **이후**: 버전 2021.2.0

AEM Cloud Service에는 사용자 지정 검색 색인 정의(예: 유형의 노드)가 필요합니다 `oak:QueryIndexDefinition`)에 `type` 값이 로 설정된 속성 `lucene`. AEM Cloud Service으로 마이그레이션하기 전에 레거시 인덱스 유형을 사용한 색인화를 업데이트해야 합니다. 자세한 내용은 [컨텐츠 검색 및 색인 지정 설명서](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/operations/indexing.html#how-to-use) 추가 정보.

### 사용자 지정 검색 색인 정의 노드에는 시드 라는 속성을 포함할 수 없습니다. {#oakpal-property-name-seed}

* **키**: IndexSeedProperty
* **유형**: 코드 냄새
* **심각도**: Minor
* **이후**: 버전 2021.2.0

AEM Cloud Service에서는 사용자 지정 검색 색인 정의(즉, 유형 노드)를 금지합니다 `oak:QueryIndexDefinition`) 접두사를 사용하지 않습니다. `seed`. AEM Cloud Service으로 마이그레이션하기 전에 이 속성을 사용한 색인화를 업데이트해야 합니다. 자세한 내용은 [컨텐츠 검색 및 색인 지정 설명서](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/operations/indexing.html#how-to-use) 추가 정보.

### 사용자 지정 검색 색인 정의 노드에는 재색인이라는 속성을 포함할 수 없습니다. {#oakpal-reindex-property}

* **키**: IndexReindexProperty
* **유형**: 코드 냄새
* **심각도**: Minor
* **이후**: 버전 2021.2.0

AEM Cloud Service에서는 사용자 지정 검색 색인 정의(즉, 유형 노드)를 금지합니다 `oak:QueryIndexDefinition`) 접두사를 사용하지 않습니다. `reindex`. AEM Cloud Service으로 마이그레이션하기 전에 이 속성을 사용한 색인화를 업데이트해야 합니다. 자세한 내용은 [컨텐츠 검색 및 색인 지정 설명서](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/operations/indexing.html#how-to-use) 추가 정보.

## Dispatcher 최적화 도구 {#dispatcher-optimization-tool-rules}

다음 섹션에는 Cloud Manager에서 실행되는 DOT(Dispatcher Optimization Tool) 검사가 나열됩니다. 각 확인의 링크를 통해 해당 GitHub 정의 및 세부 사항을 확인하십시오.

* [Dispatcher 구성 예기치 않은 토큰](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---parsing-violation---dispatcher-configuration-unexpected-tokens)

* [디스패처 구성 일치하지 않는 견적](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---parsing-violation---dispatcher-configuration-unmatched-quote)

* [디스패처 구성에 중괄호가 없습니다.](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---parsing-violation---dispatcher-configuration-missing-brace)

* [디스패처 구성 추가 중괄호](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---parsing-violation---dispatcher-configuration-extra-brace)

* [Dispatcher 구성에 필수 속성이 없습니다.](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---parsing-violation---dispatcher-configuration-missing-mandatory-property)

* [Dispatcher 구성 더 이상 사용되지 않는 속성](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---parsing-violation---dispatcher-configuration-deprecated-property)

* [디스패처 구성을 찾을 수 없음](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---parsing-violation---dispatcher-configuration-not-found)

* [Httpd 구성 포함 파일을 찾을 수 없습니다.](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---parsing-violation---httpd-configuration-include-file-not-found)

* [Dispatcher 구성 일반](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---parsing-violation---dispatcher-configuration-general)

* [Dispatcher 게시 팜 캐시에는 serverStaleOnError가 활성화되어 있어야 합니다](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---the-dispatcher-publish-farm-cache-should-have-servestaleonerror-enabled)

* [Dispatcher 게시 팜 필터에는 AEM 원형 6.x.x 버전의 기본 거부 규칙이 포함되어야 합니다](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---the-dispatcher-publish-farm-filters-should-contain-the-default-deny-rules-from-the-6xx-version-of-the-aem-archetype)

* [Dispatcher 게시 팜 캐시 상태 파일 수준 속성은 2보다 커야 합니다.](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---the-dispatcher-publish-farm-cache-statfileslevel-property-should-be--2)

* [Dispatcher 게시 팜 gracePeriod 속성은 2보다 커야 합니다.](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---the-dispatcher-publish-farm-graceperiod-property-should-be--2)

* [각 Dispatcher 팜에는 고유한 이름이 있어야 합니다](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---each-dispatcher-farm-should-have-a-unique-name)

* [Dispatcher 게시 팜 캐시에는 ignoreUrlParams 규칙이 허용 목록 방식으로 구성되어 있어야 합니다](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---the-dispatcher-publish-farm-cache-should-have-its-ignoreurlparams-rules-configured-in-an-allow-list-manner)

* [Dispatcher 게시 팜 필터는 허용 목록 방식으로 허용된 Sling 선택기를 지정해야 합니다](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---the-dispatcher-publish-farm-filters-should-specify-the-allowed-sling-selectors-in-an-allow-list-manner)

* [Dispatcher 게시 팜 필터는 허용 목록 방식으로 허용된 Sling 접미어 패턴을 지정해야 합니다](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---the-dispatcher-publish-farm-filters-should-specify-the-allowed-sling-suffix-patterns-in-an-allow-list-manner)

* [루트 디렉토리 경로가 있는 VirtualHost 디렉토리 섹션에서 &#39;모든 권한이 부여되어야 함&#39; 지시문을 사용할 수 없습니다](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---the-require-all-granted-directive-should-not-be-used-in-a-virtualhost-directory-section-with-a-root-directory-path)
