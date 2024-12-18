---
title: 사용자 정의 코드 품질 규칙
description: 코드 품질 테스트 도중 Cloud Manager에서 실행되는 사용자 정의 코드 품질 규칙의 특성에 대해 알아봅니다. 이러한 규칙은 AEM Engineering의 모범 사례를 기반으로 합니다.
exl-id: 7d118225-5826-434e-8869-01ee186e0754
source-git-commit: 8811ed130b2c7a37a0c811c308b57acf0872e9c8
workflow-type: ht
source-wordcount: '3514'
ht-degree: 100%

---


# 사용자 정의 코드 품질 규칙 {#custom-code-quality-rules}

AEM 엔지니어링의 모범 사례를 기반으로 [코드 품질 테스트](/help/using/code-quality-testing.md)의 일환으로 Cloud Manager가 실행하는 사용자 정의 코드 품질 규칙에 대해 자세히 알아보십시오.

>[!NOTE]
>
>여기에 제공된 코드 샘플은 설명 목적으로만 제공됩니다. SonarQube의 개념 및 품질 규칙에 대해 알아보려면 [SonarQube의 개념 설명서](https://docs.sonarsource.com/sonarqube/latest/)를 참조하십시오.

>[!NOTE]
>
>전체 SonarQube 규칙은 Adobe 독점 정보로 인해 다운로드할 수 없습니다. [이 링크를 사용하여 전체 규칙 목록을 다운로드할 수 있습니다](/help/assets/CodeQuality-rules-latest-AMS.xlsx). 규칙에 대한 설명과 예를 보려면 이 문서를 계속 읽어 보십시오.

## SonarQube 규칙 {#sonarqube-rules}

다음 섹션에서는 Cloud Manager에서 실행되는 SonarQube 규칙에 대해 자세히 설명합니다.

### 잠재적으로 위험한 기능을 사용하지 않음 {#do-not-use-potentially-dangerous-functions}

* **키**: CQRules:CWE-676
* **유형**: 취약성
* **심각도**: 주요
* **이후**: 버전 2018.4.0

`Thread.stop()` 및 `Thread.interrupt()` 메서드는 재현하기 어려운 문제와 경우에 따라 보안 취약성을 발생시킬 수 있습니다. 이러한 사용은 철저하게 모니터링되고 검증되어야 합니다. 일반적으로 메시지 전달은 유사한 목표를 달성하기 위한 보다 안전한 방법입니다.

#### 비준수 코드 {#non-compliant-code}

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

#### 준수 코드 {#compliant-code}

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

### 외부에서 제어할 수 있는 형식 문자열을 사용하지 않음 {#do-not-use-format-strings-which-may-be-externally-controlled}

* **키**: CQRules:CWE-134
* **유형**: 취약성
* **심각도**: 주요
* **이후**: 버전 2018.4.0

외부 소스의 형식 문자열(예: 요청 매개변수 또는 사용자 생성 콘텐츠)을 사용하면 애플리케이션이 서비스 거부 공격에 노출될 수 있습니다. 형식 문자열이 외부에서 제어될 수 있지만 신뢰할 수 있는 소스에서만 허용되는 환경이 있습니다.

#### 비준수 코드 {#non-compliant-code-1}

```java
protected void doPost(SlingHttpServletRequest request, SlingHttpServletResponse response) {
  String messageFormat = request.getParameter("messageFormat");
  request.getResource().getValueMap().put("some property", String.format(messageFormat, "some text"));
  response.sendStatus(HttpServletResponse.SC_OK);
}
```

### HTTP 요청에 항상 소켓 및 연결 시간 초과가 포함되어 있어야 함 {#http-requests-should-always-have-socket-and-connect-timeouts}

* **키**: CQRules:ConnectionTimeoutMechanism
* **유형**: 버그
* **심각도**: 심각
* **이후**: 버전 2018.6.0

AEM 애플리케이션 내부에서 HTTP 요청을 실행할 때 불필요한 스레드 소비를 방지하기 위해 적절한 시간 초과가 구성되도록 하는 것이 중요합니다. 현재 Java™의 기본 HTTP 클라이언트 `java.net.HttpUrlConnection`과 널리 사용되는 Apache HTTP 구성 요소 클라이언트에는 기본 시간 초과가 없습니다. 따라서 시간 초과를 명시적으로 구성해야 합니다. 가장 좋은 방법은 이러한 시간 초과를 60초 이내로 설정하는 것입니다.

#### 비준수 코드 {#non-compliant-code-2}

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

#### 준수 코드 {#compliant-code-1}

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

### `ResourceResolver` 오브젝트를 항상 닫아야 함 {#resourceresolver-objects-should-always-be-closed}

* **키**: CQRules:CQBP-72
* **유형**: 코드 스멜
* **심각도**: 주요
* **이후**: 버전 2018.4.0

`ResourceResolverFactory`에서 가져온 `ResourceResolver` 오브젝트는 시스템 리소스를 사용합니다. `ResourceResolver`가 더 이상 사용되지 않을 때 이러한 리소스를 회수하는 방법이 있지만 `close()` 메서드를 호출하여 열려 있는 `ResourceResolver` 오브젝트를 명시적으로 닫는 것이 더 효율적입니다.

일반적인 오해 중 하나는 기존 JCR 세션을 사용하여 생성된 `ResourceResolver` 오브젝트는 명시적으로 닫으면 안 된다는 것입니다. 또 다른 오해는 이러한 오브젝트를 닫으면 기본 JCR 세션이 닫힌다는 것입니다. 이는 사실이 아닙니다. `ResourceResolver`를 여는 방법과 상관없이 더 이상 사용하지 않을 때는 닫아야 합니다. `ResourceResolver`는 `Closeable` 인터페이스를 구현하기 때문에 `close()`를 명시적으로 호출하는 대신 `try-with-resources` 구문을 사용하는 것도 가능합니다.

#### 비준수 코드 {#non-compliant-code-4}

```java
public void dontDoThis(Session session) throws Exception {
  ResourceResolver resolver = factory.getResourceResolver(Collections.singletonMap("user.jcr.session", (Object)session));
  // do some stuff with the resolver
}
```

#### 준수 코드 {#compliant-code-2}

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

### 슬링 서블릿 경로를 사용하여 서블릿을 등록 안 함 {#do-not-use-sling-servlet-paths-to-register-servlets}

* **키**: CQRules:CQBP-75
* **유형**: 코드 스멜
* **심각도**: 주요
* **이후**: 버전 2018.4.0

[슬링 설명서](https://sling.apache.org/documentation/the-sling-engine/servlets.html)에 설명된 대로 경로별로 서블릿을 바인딩하는 것은 권장되지 않습니다. 경로 바인딩 서블릿은 표준 JCR 액세스 제어를 사용할 수 없으며, 결과적으로 엄격한 추가 보안이 요구됩니다. 경로 바인딩 서블릿을 사용하는 대신 저장소에 노드를 생성하고 리소스 유형별로 서블릿을 등록하는 것이 좋습니다.

#### 비준수 코드 {#non-compliant-code-5}

```java
@Component(property = {
  "sling.servlet.paths=/apps/myco/endpoint"
})
public class DontDoThis extends SlingAllMethodsServlet {
 // implementation
}
```

### 발견된 예외를 기록하거나 표시하되 둘 다 해서는 안 됨 {#caught-exceptions-should-be-logged-or-thrown-but-not-both}

* **키**: CQRules:CQBP-44---CatchAndEitherLogOrThrow
* **유형**: 코드 스멜
* **심각도**: 사소
* **이후**: 버전 2018.4.0

일반적으로 예외는 정확히 한 번 기록해야 합니다. 예외를 여러 번 기록하면 예외가 몇 번 발생했는지 알 수 없으므로 혼동이 발생할 수 있습니다. 이러한 문제를 발생시키는 가장 일반적인 패턴은 발생한 예외의 기록과 표시입니다.

#### 비준수 코드 {#non-compliant-code-6}

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

#### 준수 코드 {#compliant-code-3}

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

### throw 문 바로 뒤에 오는 log 문 방지 {#avoid-having-a-log-statement-immediately-followed-by-a-throw-statement}

* **키**: CQRules:CQBP-44---ConsecutivelyLogAndThrow
* **유형**: 코드 스멜
* **심각도**: 사소
* **이후**: 버전 2018.4.0

피해야 할 또 다른 일반적인 패턴은 메시지를 기록한 다음 즉시 예외를 발생시키는 것입니다. 이 문제는 일반적으로 예외 메시지가 로그 파일에 중복됨을 나타내는 것입니다.

#### 비준수 코드 {#non-compliant-code-7}

```java
public void dontDoThis() throws Exception {
  logger.error("something went wrong");
  throw new RuntimeException("something went wrong");
}
```

#### 준수 코드 {#compliant-code-4}

```java
public void doThis() throws Exception {
  throw new RuntimeException("something went wrong");
}
```

### GET 또는 HEAD 요청을 처리할 때 INFO에서 로깅하지 않음 {#avoid-logging-at-info-when-handling-get-or-head-requests}

* **키**: CQRules:CQBP-44---LogInfoInGetOrHeadRequests
* **유형**: 코드 스멜
* **심각도**: 사소

일반적으로 INFO 로그 수준은 중요한 작업을 구분하는 데 사용되어야 하며 기본적으로 AEM은 INFO 수준 또는 그 이상에서 기록되도록 구성됩니다. GET 및 HEAD 메서드는 읽기 전용 작업이어야 하므로 중요한 작업을 구성하지 않습니다. GET 또는 HEAD 요청에 대한 응답으로 INFO 수준에서 로깅하면 상당한 로그 노이즈가 발생하여 로그 파일에서 유용한 정보를 식별하기가 더 어려워질 수 있습니다. GET 또는 HEAD 요청을 처리할 때 문제가 발생한 경우 WARN 또는 ERROR 수준으로 로깅해야 합니다. 더 심층적인 문제 해결 정보를 얻으려면 로깅을 DEBUG 또는 TRACE 수준으로 설정해야 합니다.

>[!NOTE]
>
>이러한 워크플로는 각 요청에 대한 access.log-type 로깅에는 적용되지 않습니다.

#### 비준수 코드 {#non-compliant-code-8}

```java
public void doGet() throws Exception {
  logger.info("handling a request from the user");
}
```

#### 준수 코드 {#compliant-code-5}

```java
public void doGet() throws Exception {
  logger.debug("handling a request from the user.");
}
```

### logging 문의 첫 번째 매개변수로 `Exception.getMessage()` 사용 안 함 {#do-not-use-exception-getmessage-as-the-first-parameter-of-a-logging-statement}

* **키**: CQRules:CQBP-44---ExceptionGetMessageIsFirstLogParam
* **유형**: 코드 스멜
* **심각도**: 사소
* **이후**: 버전 2018.4.0

가장 좋은 방법은 로그 메시지가 애플리케이션에서 예외가 발생한 위치에 대한 상황별 정보를 제공하는 것입니다. 스택 추적을 사용하여 컨텍스트를 결정할 수도 있지만 일반적으로 로그 메시지는 읽고 이해하는 것이 더 쉬울 것입니다. 따라서 예외를 기록할 때 예외 메시지를 로그 메시지로 사용하는 것은 잘못된 관행입니다. 예외 메시지에는 발생한 문제에 대해 자세히 설명되어 있습니다. 반면에, 로그 메시지는 예외가 발생했을 때 애플리케이션이 무엇을 하고 있었는지를 나타냅니다. 예외 메시지는 계속 기록됩니다. 고유한 메시지를 지정하면 로그를 쉽게 이해할 수 있습니다.

#### 비준수 코드 {#non-compliant-code-9}

```java
public void dontDoThis() {
  try {
    someMethodThrowingAnException();
  } catch (Exception e) {
    logger.error(e.getMessage(), e);
  }
}
```

#### 준수 코드 {#compliant-code-6}

```java
public void doThis() {
  try {
    someMethodThrowingAnException();
  } catch (Exception e) {
    logger.error("Unable to do something", e);
  }
}
```

### Catch 블록에 로그인할 때 WARN 또는 ERROR 수준을 유지해야 함 {#logging-in-catch-blocks-should-be-at-the-warn-or-error-level}

* **키**: CQRules:CQBP-44---WrongLogLevelInCatchBlock
* **유형**: 코드 스멜
* **심각도**: 사소
* **이후**: 버전 2018.4.0

이름에서 알 수 있듯이 Java™ 예외는 예외적인 상황에서 항상 사용되어야 합니다. 결과적으로 예외가 발생하면 로그 메시지가 WARN 또는 ERROR 중 적절한 수준으로 기록되도록 하는 것이 중요합니다. 이렇게 하면 해당 메시지가 로그에 올바르게 표시됩니다.

#### 비준수 코드 {#non-compliant-code-10}

```java
public void dontDoThis() {
  try {
    someMethodThrowingAnException();
  } catch (Exception e) {
    logger.debug(e.getMessage(), e);
  }
}
```

#### 준수 코드 {#compliant-code-7}

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

* **키**: CQRules:CQBP-44---ExceptionPrintStackTrace
* **유형**: 코드 스멜
* **심각도**: 사소
* **이후**: 버전 2018.4.0

로그 메시지를 이해할 때 컨텍스트는 중요합니다. `Exception.printStackTrace()`를 사용하면 스택 추적만 표준 오류 스트림으로 출력되므로 모든 컨텍스트가 손실됩니다. 또한 AEM과 같은 다중 스레드 애플리케이션에서 이 방법을 사용하여 여러 예외를 병렬로 인쇄하면 스택 추적이 겹쳐서 상당한 혼동을 일으킬 수 있습니다. 예외는 로깅 프레임워크에서만 기록되어야 합니다.

#### 비준수 코드 {#non-compliant-code-11}

```java
public void dontDoThis() {
  try {
    someMethodThrowingAnException();
  } catch (Exception e) {
    e.printStackTrace();
  }
}
```

#### 준수 코드 {#compliant-code-8}

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
* **유형**: 코드 스멜
* **심각도**: 사소
* **이후**: 버전 2018.4.0

AEM에서의 로깅은 항상 로깅 프레임워크인 SLF4J를 통해 수행되어야 합니다. 표준 출력 또는 표준 오류 스트림으로 직접 출력하면 로깅 프레임워크에서 제공하는 구조 및 컨텍스트 정보가 손실되고 경우에 따라 성능 문제가 발생할 수 있습니다.

#### 비준수 코드 {#non-compliant-code-12}

```java
public void dontDoThis() {
  try {
    someMethodThrowingAnException();
  } catch (Exception e) {
    System.err.println("Unable to do something");
  }
}
```

#### 준수 코드 {#compliant-code-9}

```java
public void doThis() {
  try {
    someMethodThrowingAnException();
  } catch (Exception e) {
    logger.error("Unable to do something", e);
  }
}
```

### 하드코딩된 `/apps` 경로 및 `/libs` 경로 방지 {#avoid-hardcoded-apps-and-libs-paths}

* **키**: CQRules:CQBP-71
* **유형**: 코드 스멜
* **심각도**: 사소
* **이후**: 버전 2018.4.0

`/libs` 및 `/apps`로 시작하는 경로는 일반적으로 하드코딩해서는 안 됩니다. 이러한 경로는 일반적으로 슬링 검색 경로를 기준으로 저장되며, 기본값은 `/libs,/apps`입니다. 절대 경로를 사용하면 프로젝트 수명 주기의 후반에만 나타나는 미묘한 결함이 발생할 수 있습니다.

#### 비준수 코드 {#non-compliant-code-13}

```java
public boolean dontDoThis(Resource resource) {
  return resource.isResourceType("/libs/foundation/components/text");
}
```

#### 준수 코드 {#compliant-code-10}

```java
public void doThis(Resource resource) {
  return resource.isResourceType("foundation/components/text");
}
```

### 슬링 스케줄러를 사용하면 안 됨 {#sonarqube-sling-scheduler}

* **키**: CQRules:AMSCORE-554
* **유형**: 코드 스멜/Cloud Service 호환성
* **심각도**: 사소
* **이후**: 버전 2020.5.0

보장된 실행이 필요한 작업에는 Sling 스케줄러를 사용하지 마십시오. Sling의 예정된 작업은 실행을 보장하며 클러스터된 환경과 클러스터되지 않은 환경 모두에 더 적합합니다.

클러스터 환경에서 Sling 작업이 처리되는 방법에 대한 자세한 내용은 [Apache Sling 이벤트 및 작업 처리 설명서](https://sling.apache.org/documentation/bundles/apache-sling-eventing-and-job-handling.html)를 참조하십시오.

### 더 이상 사용되지 않는 AEM API를 사용하면 안 됨 {#sonarqube-aem-deprecated}

* **키**: AMSCORE-553
* **유형**: 코드 스멜/Cloud Service 호환성
* **심각도**: 사소
* **이후**: 버전 2020.5.0

AEM API 표면은 사용이 권장되지 않아 더 이상 사용되지 않는 것으로 간주되는 API를 식별하기 위해 지속적으로 수정되고 있습니다.

대부분의 경우 이러한 API는 표준 Java™ *@Deprecated* 주석을 사용하여 더 이상 사용되지 않으며, `squid:CallToDeprecatedMethod`에 의해 식별됩니다.

그러나 AEM의 컨텍스트에서는 API가 더 이상 사용되지 않지만 다른 컨텍스트에서는 사용되는 경우가 있습니다. 이 규칙은 이 두 번째 클래스를 식별합니다.

## OakPAL 콘텐츠 규칙 {#oakpal-rules}

다음 섹션에서는 Cloud Manager에서 실행되는 OakPAL 검사에 대해 자세히 설명합니다.

>[!NOTE]
>
>OakPAL은 독립 실행형 Oak 저장소를 사용하여 콘텐츠 패키지의 유효성을 검사하는 프레임워크입니다. AEM 파트너이자 2019년 AEM Rock Star North America 어워드 수상자가 개발했습니다.

### @ProviderType으로 주석이 달린 제품 API는 고객이 구현하거나 확장해서는 안 됨 {#product-apis-annotated-with-providertype-should-not-be-implemented-or-extended-by-customers}

* **키**: CQBP-84
* **유형**: 버그
* **심각도**: 심각
* **이후**: 버전 2018.7.0

AEM API는 사용자 정의 코드에 의해 사용될 뿐 구현되지 않는 Java™ 인터페이스와 클래스를 포함합니다. 예를 들어 AEM만 `com.day.cq.wcm.api.Page` 인터페이스를 구현합니다.

이러한 인터페이스에 새로운 메서드를 추가해도 기존 코드에는 영향을 미치지 않으므로 새로운 메서드를 추가해도 이전 버전과 호환됩니다. 그러나 사용자 정의 코드로 이러한 인터페이스 중 하나를 구현하는 경우 해당 사용자 정의 코드로 인해 이전 버전과 호환되지 않는 문제가 발생합니다.

AEM은 구현되도록 의도된 인터페이스 및 클래스에 `org.osgi.annotation.versioning.ProviderType` 또는 경우에 따라 `aQute.bnd.annotation.ProviderType` 기존 주석을 주석으로 추가합니다. 이 규칙은 사용자 정의 코드가 이러한 인터페이스를 구현하거나 클래스를 확장하는 인스턴스를 감지합니다.

#### 비준수 코드 {#non-compliant-code-3}

```java
import com.day.cq.wcm.api.Page;

public class DontDoThis implements Page {
// implementation here
}
```

### 고객 패키지는 `/libs`에서 노드를 생성하거나 수정해서는 안 됨 {#oakpal-customer-package}

* **키**: BannedPath
* **유형**: 버그
* **심각도**: Blocker
* **이후**: 버전 2019.6.0

AEM 콘텐츠 저장소의 `/libs` 콘텐츠 트리는 고객이 읽기 전용으로 간주해야 하는 것이 오랜 모범 사례였습니다. `/libs`에서 노드 및 속성을 수정하면 주 업데이트 및 부 업데이트에 상당한 위험이 발생합니다. `/libs`에 대한 편집은 공식 채널을 통해 Adobe에 의해서만 이루어져야 합니다.

### 패키지에 중복된 OSGi 구성을 포함하지 않음 {#oakpal-package-osgi}

* **키**: DuplicateOsgiConfigurations
* **유형**: 버그
* **심각도**: 주요
* **이후**: 버전 2019.6.0

복잡한 프로젝트에서 발생하는 일반적인 문제는 동일한 OSGi 구성 요소가 여러 번 구성되는 경우입니다. 이러한 문제로 인해 어떤 구성이 작동 가능할지 모호해집니다. 이 규칙은 동일한 구성 요소가 동일한 실행 모드 또는 실행 모드 조합에서 여러 번 구성된 문제만 식별한다는 점에서 “실행 모드 인식” 규칙입니다.

#### 비준수 코드 {#non-compliant-code-osgi}

```text
+ apps
  + projectA
    + config
      + com.day.cq.commons.impl.ExternalizerImpl
  + projectB
    + config
      + com.day.cq.commons.impl.ExternalizerImpl
```

#### 준수 코드 {#compliant-code-osgi}

```text
+ apps
  + shared-config
    + config
      + com.day.cq.commons.impl.ExternalizerImpl
```

### 구성 및 설치 폴더에 OSGi 노드만 포함해야 함 {#oakpal-config-install}

* **키**: ConfigAndInstallShouldOnlyContainOsgiNodes
* **유형**: 버그
* **심각도**: 주요
* **이후**: 버전 2019.6.0

보안상의 이유로 `/config/` 및 `/install/`가 포함된 경로는 AEM의 관리 사용자만 읽을 수 있으며 OSGi 구성 및 OSGi 번들에만 사용해야 합니다. 이러한 세그먼트를 포함하는 경로에 다른 유형의 콘텐츠를 배치하면 관리 사용자와 비관리 사용자 간에 의도하지 않게 달라지는 애플리케이션 비헤이비어가 발생합니다.

일반적인 문제는 구성 요소 대화 상자 내에서 `config`라는 노드를 사용하거나 인라인 편집을 위해 리치 텍스트 편집기 구성을 지정할 때 발생합니다. 이 문제를 해결하려면 문제가 있는 노드의 이름을 규정 준수 이름으로 변경해야 합니다. 리치 텍스트 편집기 구성의 경우 `cq:inplaceEditing` 노드의 `configPath` 속성을 사용하여 새 위치를 지정하십시오.

#### 비준수 코드 {#non-compliant-code-config-install}

```text
+ cq:editConfig [cq:EditConfig]
  + cq:inplaceEditing [cq:InplaceEditConfig]
    + config [nt:unstructured]
      + rtePlugins [nt:unstructured]
```

#### 준수 코드 {#compliant-code-config-install}

```text
+ cq:editConfig [cq:EditConfig]
  + cq:inplaceEditing [cq:InplaceEditConfig]
    ./configPath = inplaceEditingConfig (String)
    + inplaceEditingConfig [nt:unstructured]
      + rtePlugins [nt:unstructured]
```

### 패키지를 겹치지 않음 {#oakpal-no-overlap}

* **키**: PackageOverlaps
* **유형**: 버그
* **심각도**: 주요
* **이후**: 버전 2019.6.0

[패키지에 중복된 OSGi 구성 규칙을 포함해서는 안 됨](#oakpal-package-osgi)과 마찬가지로, 이 문제는 여러 개의 개별 콘텐츠 패키지에 의해 동일한 노드 경로가 기록되는 복잡한 프로젝트에서 일반적인 문제입니다. 콘텐츠 패키지 종속성을 사용하면 일관된 결과를 보장할 수 있지만 중복을 완전히 피하는 것이 좋습니다.

### 기본 작성 모드는 클래식 UI가 아니어야 함 {#oakpal-default-authoring}

* **키**: ClassicUIAuthoringMode
* **유형**: 코드 스멜/Cloud Service 호환성
* **심각도**: 사소
* **이후**: 버전 2020.5.0

OSGi 구성 `com.day.cq.wcm.core.impl.AuthoringUIModeServiceImpl` AEM 내의 기본 제작 모드를 정의합니다. AEM 6.4 이후 클래식 UI가 더 이상 사용되지 않으므로 기본 제작 모드가 클래식 UI로 구성되면 문제가 발생합니다.

### 대화 상자가 있는 구성 요소에는 터치 UI 대화 상자가 있어야 함 {#oakpal-components-dialogs}

* **키**: ComponentWithOnlyClassicUIDialog
* **유형**: 코드 스멜/Cloud Service 호환성
* **심각도**: 사소
* **이후**: 버전 2020.5.0

클래식 UI 대화 상자가 있는 AEM 구성 요소에는 클래식 UI를 지원하지 않는 Cloud Service 배포 모델과의 최적의 작성 및 호환성을 위해 터치 UI 대화 상자도 있어야 합니다. 이 규칙은 다음 시나리오를 확인합니다.

* Classic UI 대화 상자(즉, `dialog` 하위 노드)가 있는 구성 요소에는 해당 터치 UI 대화 상자(즉, `cq:dialog` 하위 노드)가 있어야 합니다.
* Classic UI 디자인 대화 상자(예: `design_dialog` 노드)가 있는 구성 요소에는 해당 터치 UI 디자인 대화 상자(예: `cq:design_dialog` 하위 노드)가 있어야 합니다.
* 클래식 UI 대화 상자 및 클래식 UI 디자인 대화 상자가 모두 있는 구성 요소에는 해당 터치 UI 대화 상자 및 해당 터치 UI 디자인 대화 상자가 모두 있어야 합니다.

AEM 현대화 도구 설명서는 구성 요소를 클래식 UI에서 터치 UI로 변환하는 방법에 대한 세부 정보와 도구를 제공합니다. 자세한 내용은 [AEM 현대화 도구 설명서](https://opensource.adobe.com/aem-modernize-tools/)를 참조하십시오.

### 역방향 복제 에이전트를 사용하면 안 됨 {#oakpal-reverse-replication}

* **키**: ReverseReplication
* **유형**: 코드 스멜/Cloud Service 호환성
* **심각도**: 사소
* **이후**: 버전 2020.5.0

[릴리스 정보: 복제 에이전트 제거](https://experienceleague.adobe.com/kr/docs/experience-manager-cloud-service/content/release-notes/aem-cloud-changes#replication-agents)에서 설명한 대로 Cloud Service 배포에서는 역방향 복제에 대한 지원을 사용할 수 없습니다.

역방향 복제를 사용하는 고객은 Adobe에 대체 솔루션을 문의해야 합니다.

### 프록시가 활성화된 클라이언트 라이브러리에 포함된 리소스는 “resources” 폴더에 있어야 함 {#oakpal-resources-proxy}

* **키**: ClientlibProxyResource
* **유형**: 버그
* **심각도**: 사소
* **이후**: 버전 2021.2.0

AEM 클라이언트 라이브러리는 이미지 및 글꼴과 같은 정적 리소스를 포함할 수 있습니다. [클라이언트측 라이브러리 사용 설명서](https://experienceleague.adobe.com/kr/docs/experience-manager-65/content/implementing/developing/introduction/clientlibs#using-preprocessors)에 설명된 대로 프록시 클라이언트 라이브러리를 사용할 때 게시 인스턴스에서 효과적으로 참조하려면 이러한 정적 리소스가 `resources`라는 하위 폴더에 포함되어 있어야 합니다.

#### 비준수 코드 {#non-compliant-proxy-enabled}

```text
+ apps
  + projectA
    + clientlib
      - allowProxy=true
      + images
        + myimage.jpg
```

#### 준수 코드 {#compliant-proxy-enabled}

```text
+ apps
  + projectA
    + clientlib
      - allowProxy=true
      + resources
        + myimage.jpg
```

### Cloud Service의 호환되지 않는 워크플로 프로세스 사용 {#oakpal-usage-cloud-service}

* **키**: CloudServiceIncompatibleWorkflowProcess
* **유형**: 코드 스멜
* **심각도**: Blocker
* **이후**: 버전 2021.2.0

AEM Cloud Service에서 자산 처리를 위해 Asset 마이크로 서비스로 이동하면서 AEM의 온프레미스 및 AMS 버전에서 사용되던 여러 워크플로 프로세스가 지원되지 않거나 불필요하게 되었습니다.

[AEM Assets as a Cloud Service GitHub 저장소](https://github.com/adobe/aem-cloud-migration)에 있는 마이그레이션 도구를 사용하여 AEM as a Cloud Service로 마이그레이션하는 동안 워크플로 모델을 업데이트할 수 있습니다.

### 편집 가능한 템플릿을 위해 정적 템플릿을 사용하지 않음 {#oakpal-static-template}

* **키**: StaticTemplateUsage
* **유형**: 코드 스멜
* **심각도**: 사소
* **이후**: 버전 2021.2.0

정적 템플릿의 사용은 역사적으로 AEM 프로젝트에서 흔했지만 편집 가능한 템플릿은 가장 유연하고 정적 템플릿에 없는 추가 기능을 지원하기 때문에 적극 권장됩니다. 자세한 내용은 [페이지 템플릿 - 편집 가능](https://experienceleague.adobe.com/kr/docs/experience-manager-65/content/implementing/developing/platform/templates/page-templates-editable) 문서에서 확인할 수 있습니다.

정적 템플릿에서 편집 가능 템플릿으로의 마이그레이션은 [AEM 현대화 도구](https://opensource.adobe.com/aem-modernize-tools/)를 사용하여 대부분 자동화할 수 있습니다.

### 기존 기초 구성 요소를 사용하지 않음 {#oakpal-usage-legacy}

* **키**: LegacyFoundationComponentUsage
* **유형**: 코드 스멜
* **심각도**: 사소
* **이후**: 버전 2021.2.0

레거시 Foundation 구성 요소(즉, `/libs/foundation` 아래의 구성 요소)는 [핵심 구성 요소](https://experienceleague.adobe.com/kr/docs/experience-manager-core-components/using/introduction)를 위한 여러 AEM 릴리스에서 더 이상 사용되지 않습니다. 기존 Foundation 구성 요소를 오버레이 또는 상속 여부에 관계없이 사용자 정의 구성 요소의 기준으로 사용하는 것은 권장되지 않으며 해당 핵심 구성 요소로 변환해야 합니다.

이러한 변환은 [AEM 현대화 도구](https://opensource.adobe.com/aem-modernize-tools/)를 통해 촉진될 수 있습니다.

### 사용자 정의 검색 인덱스 정의 노드는 `/oak:index`의 직접 하위 노드여야 함 {#oakpal-custom-search}

* **키**: OakIndexLocation
* **유형**: 코드 스멜
* **심각도**: 사소
* **이후**: 버전 2021.2.0

AEM Cloud Service를 사용하려면 사용자 정의 검색 인덱스 정의(즉, `oak:QueryIndexDefinition` 유형의 노드)가 `/oak:index`의 직접 하위 노드여야 합니다. AEM Cloud Service와 호환되려면 다른 위치의 인덱스를 이동해야 합니다. 검색 인덱스에 대한 자세한 내용은 [콘텐츠 검색 및 색인화 설명서](https://experienceleague.adobe.com/kr/docs/experience-manager-cloud-service/content/operations/indexing)를 참조하십시오.

### 사용자 정의 검색 인덱스 정의 노드의 compatVersion을 2로 설정해야 함 {#oakpal-custom-search-compatVersion}

* **키**: IndexCompatVersion
* **유형**: 코드 스멜
* **심각도**: 사소
* **이후**: 버전 2021.2.0

AEM Cloud Service를 사용하려면 사용자 정의 검색 인덱스 정의(즉, `oak:QueryIndexDefinition` 유형의 노드)에 `2`로 설정된 `compatVersion` 속성이 있어야 합니다. 다른 값은 AEM Cloud Service에서 지원되지 않습니다. 검색 인덱스에 대한 자세한 내용은 [콘텐츠 검색 및 색인화 설명서](https://experienceleague.adobe.com/kr/docs/experience-manager-cloud-service/content/operations/indexing)를 참조하십시오.

### 사용자 정의 검색 인덱스 정의 노드의 하위 노드 유형은 `nt:unstructured`여야 함 {#oakpal-descendent-nodes}

* **키**: IndexDescendantNodeType
* **유형**: 코드 스멜
* **심각도**: 사소
* **이후**: 버전 2021.2.0

사용자 정의 검색 인덱스 정의 노드에 순서가 지정되지 않은 하위 노드가 있으면 문제를 해결하기 어려운 문제가 발생할 수 있습니다. 이러한 노드를 방지하려면 `oak:QueryIndexDefinition` 노드의 모든 하위 노드가 `nt:unstructured` 유형인 것이 좋습니다.

### 사용자 정의 검색 인덱스 정의 노드는 하위 노드가 있는 `indexRules`라는 하위 노드를 포함해야 함 {#oakpal-custom-search-index}

* **키**: IndexRulesNode
* **유형**: 코드 스멜
* **심각도**: 사소
* **이후**: 버전 2021.2.0

올바르게 정의된 사용자 정의 검색 인덱스 정의 노드에는 `indexRules`라는 하위 노드가 있어야 하며, 이 노드에는 하나 이상의 하위 노드가 있어야 합니다. 자세한 내용은 [Oak 문서](https://jackrabbit.apache.org/oak/docs/query/lucene.html)에서 확인할 수 있습니다.

### 사용자 정의 검색 인덱스 정의 노드는 명명 규칙을 준수해야 함 {#oakpal-custom-search-definitions}

* **키**: IndexName
* **유형**: 코드 스멜
* **심각도**: 사소
* **이후**: 버전 2021.2.0

AEM Cloud Service를 사용하려면 사용자 정의 검색 인덱스 정의(즉, `oak:QueryIndexDefinition` 유형의 노드)를 [콘텐츠 검색 및 색인화](https://experienceleague.adobe.com/kr/docs/experience-manager-cloud-service/content/operations/indexing#how-to-use)에 설명된 특정 패턴에 따라 지정해야 합니다.

### 사용자 정의 검색 인덱스 정의 노드는 lucene 유형의 인덱스를 사용해야 함 {#oakpal-index-type-lucene}

* **키**: IndexType
* **유형**: 코드 스멜
* **심각도**: 사소
* **이후**: 버전 2021.2.0

AEM Cloud Service를 사용하려면 사용자 정의 검색 인덱스 정의(즉, `oak:QueryIndexDefinition` 유형의 노드)에 값이 `lucene`로 설정된 `type` 속성이 있어야 합니다. 레거시 인덱스 유형을 사용하는 색인화는 AEM Cloud Service로 마이그레이션하기 전에 업데이트해야 합니다. 자세한 내용은 [콘텐츠 검색 및 색인화 문서](https://experienceleague.adobe.com/kr/docs/experience-manager-cloud-service/content/operations/indexing#how-to-use)를 참조하십시오.

### 사용자 정의 검색 인덱스 정의 노드에는 `seed`라는 속성이 포함되어서는 안 됨 {#oakpal-property-name-seed}

* **키**: IndexSeedProperty
* **유형**: 코드 스멜
* **심각도**: 사소
* **이후**: 버전 2021.2.0

AEM Cloud Service는 사용자 정의 검색 인덱스 정의(즉, `oak:QueryIndexDefinition` 유형의 노드)에 `seed`라는 속성을 포함하는 것을 금지합니다. 이 속성을 사용하는 색인화는 AEM Cloud Service로 마이그레이션하기 전에 업데이트해야 합니다. 자세한 내용은 [콘텐츠 검색 및 색인화 문서](https://experienceleague.adobe.com/kr/docs/experience-manager-cloud-service/content/operations/indexing#how-to-use)를 참조하십시오.

### 사용자 정의 검색 인덱스 정의 노드에는 `reindex`라는 속성이 포함되어서는 안 됨 {#oakpal-reindex-property}

* **키**: IndexReindexProperty
* **유형**: 코드 스멜
* **심각도**: 사소
* **이후**: 버전 2021.2.0

AEM Cloud Service는 사용자 정의 검색 인덱스 정의(즉, `oak:QueryIndexDefinition` 유형의 노드)에 `reindex`라는 속성을 포함하는 것을 금지합니다. 이 속성을 사용하는 색인화는 AEM Cloud Service로 마이그레이션하기 전에 업데이트해야 합니다. 자세한 내용은 [콘텐츠 검색 및 색인화 문서](https://experienceleague.adobe.com/kr/docs/experience-manager-cloud-service/content/operations/indexing#how-to-use)를 참조하십시오.

### UI 콘텐츠 패키지에 색인 정의 노드를 배포하면 안 됨 {#oakpal-ui-content-package}

* **키**: IndexNotUnderUIContent
* **유형**: 개선
* **심각도**: 사소
* **이후**: 버전 2024.6.0

AEM Cloud Service는 UI 콘텐츠 패키지에 사용자 정의 검색 색인 정의(유형 `oak:QueryIndexDefinition`의 노드)를 배포할 수 없도록 합니다.

>[!WARNING]
>
>[Cloud Manager 2024년 8월 릴리스](/help/release-notes/current.md)부터 파이프라인에 장애가 발생하므로 가능한 한 빨리 이 문제를 해결해야 합니다.

### 유형 `damAssetLucene`의 사용자 정의 전체 텍스트 색인 정의는 `damAssetLucene` 접두사가 올바르게 추가되어야 함 {#oakpal-dam-asset-lucene}

* **키**: CustomFulltextIndexesOfTheDamAssetCheck
* **유형**: 개선
* **심각도**: 사소
* **이후**: 버전 2024.6.0

AEM Cloud Service는 `damAssetLucene`의 사용자 정의 전체 텍스트 색인 정의에 `damAssetLucene` 이외의 접두사가 붙지 못하도록 합니다.

>[!WARNING]
>
>[Cloud Manager 2024년 8월 릴리스](/help/release-notes/current.md)부터 파이프라인에 장애가 발생하므로 가능한 한 빨리 이 문제를 해결해야 합니다.

### 색인 정의 노드에는 동일한 이름의 속성이 포함되면 안 됨 {#oakpal-index-property-name}

* **키**: DuplicateNameProperty
* **유형**: 개선
* **심각도**: 사소
* **이후**: 버전 2024.6.0

AEM Cloud Service는 사용자 정의 검색 색인 정의(즉, 유형 `oak:QueryIndexDefinition`의 노드)에 동일한 이름의 속성을 포함하는 것을 금지합니다.

>[!WARNING]
>
>[Cloud Manager 2024년 8월 릴리스](/help/release-notes/current.md)부터 파이프라인에 장애가 발생하므로 가능한 한 빨리 이 문제를 해결해야 합니다.

### 특정 기본 제공 색인 정의는 사용자 정의할 수 없음 {#oakpal-customizing-ootb-index}

* **키**: RestrictIndexCustomization
* **유형**: 개선
* **심각도**: 사소
* **이후**: 버전 2024.6.0

AEM Cloud Service는 다음 OOTB 색인의 무단 수정을 금지합니다.

* `nodetypeLucene`
* `slingResourceResolver`
* `socialLucene`
* `appsLibsLucene`
* `authorizables`
* `pathReference`

>[!WARNING]
>
>[Cloud Manager 2024년 8월 릴리스](/help/release-notes/current.md)부터 파이프라인에 장애가 발생하므로 가능한 한 빨리 이 문제를 해결해야 합니다.

### 분석기의 토큰화 구성은 `tokenizer`라는 이름으로 생성해야 함 {#oakpal-tokenizer}

* **키**: AnalyzerTokenizerConfigCheck
* **유형**: 개선
* **심각도**: 사소
* **이후**: 버전 2024.6.0

AEM Cloud Service는 분석기에서 잘못된 이름을 가진 토큰화 생성을 금지합니다. 토큰화는 항상 `tokenizer`로 정의되어야 합니다.

### 색인화 정의 구성에 공백이 포함되어서는 안 됨 {#oakpal-indexing-definitions-spaces}

* **키**: PathSpacesCheck
* **유형**: 개선
* **심각도**: 사소
* **이후**: 버전 2024.7.0

AEM Cloud Service는 공백이 있는 속성을 포함하는 색인화 &#x200B;&#x200B;정의 생성을 금지합니다.

### 색인화 정의 구성에 haystack0 속성이 포함되어서는 안 됨 {#oakpal-indexing-haystack0-property}

* **키**: HayStackPropertyCheck
* **유형**: 개선
* **심각도**: 사소
* **이후**: 버전 2024.12.0

AEM Cloud Service는 haystack 속성을 포함하는 색인화 &#x200B;&#x200B;정의 생성을 금지합니다.

## Dispatcher 최적화 도구 {#dispatcher-optimization-tool-rules}

다음 섹션에서는 Cloud Manager에서 실행되는 DOT(Dispatcher 최적화 도구) 검사를 나열합니다. GitHub 정의 및 세부 정보를 확인하려면 각 링크를 따르십시오.

* [Dispatcher 구성 예기치 않은 토큰](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---parsing-violation---dispatcher-configuration-unexpected-tokens)

* [Dispatcher 구성 불일치 견적](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---parsing-violation---dispatcher-configuration-unmatched-quote)

* [Dispatcher 구성 중괄호 누락](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---parsing-violation---dispatcher-configuration-missing-brace)

* [Dispatcher 구성 추가 중괄호](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---parsing-violation---dispatcher-configuration-extra-brace)

* [Dispatcher 구성 필수 속성 누락](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---parsing-violation---dispatcher-configuration-missing-mandatory-property)

* [Dispatcher 구성 더 이상 사용되지 않는 속성](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---parsing-violation---dispatcher-configuration-deprecated-property)

* [Dispatcher 구성을 찾을 수 없음](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---parsing-violation---dispatcher-configuration-not-found)

* [Httpd 구성 포함 파일을 찾을 수 없음](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---parsing-violation---httpd-configuration-include-file-not-found)

* [Dispatcher 구성 일반](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---parsing-violation---dispatcher-configuration-general)

* [Dispatcher 게시 팜 캐시에 `serveStaleOnError`가 활성화되어 있어야 함](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---the-dispatcher-publish-farm-cache-should-have-servestaleonerror-enabled)

* [Dispatcher 게시 팜 필터는 6.x.x 버전의 AEM Archetype의 기본 거부 규칙을 포함해야 함](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---the-dispatcher-publish-farm-filters-should-contain-the-default-deny-rules-from-the-6xx-version-of-the-aem-archetype)

* [Dispatcher 게시 팜 캐시 `statfileslevel` 속성은 2보다 크거나 같아야 함](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---the-dispatcher-publish-farm-cache-statfileslevel-property-should-be--2)

* [Dispatcher 게시 팜 `gracePeriod` 속성은 2보다 크거나 같아야 함](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---the-dispatcher-publish-farm-graceperiod-property-should-be--2)

* [각 Dispatcher 팜에는 고유한 이름이 있어야 함](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---each-dispatcher-farm-should-have-a-unique-name)

* [Dispatcher 게시 팜 캐시에는 `ignoreUrlParams` 규칙이 허용 목록 방식으로 구성되어 있어야 함](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---the-dispatcher-publish-farm-cache-should-have-its-ignoreurlparams-rules-configured-in-an-allow-list-manner)

* [Dispatcher 게시 팜 필터는 허용 목록 방식으로 허용되는 Sling 선택기를 지정해야 함](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---the-dispatcher-publish-farm-filters-should-specify-the-allowed-sling-selectors-in-an-allow-list-manner)

* [Dispatcher 게시 팜 필터는 허용 목록 방식으로 허용되는 Sling 접미사 패턴을 지정해야 함](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---the-dispatcher-publish-farm-filters-should-specify-the-allowed-sling-suffix-patterns-in-an-allow-list-manner)

* [루트 디렉터리 경로가 있는 VirtualHost Directory 섹션에서 “Require all granted” 지시어를 사용하면 안 됨](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---the-require-all-granted-directive-should-not-be-used-in-a-virtualhost-directory-section-with-a-root-directory-path)
