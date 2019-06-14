---
title: 사용자 지정 코드 품질 규칙
seo-title: 사용자 지정 코드 품질 규칙
description: 클라우드 관리자에서 실행하는 사용자 지정 코드 품질 규칙에 대해 알려면 이 페이지를 따르십시오.
seo-description: Adobe Experience Manager Cloud Manager에서 실행하는 사용자 지정 코드 품질 규칙에 대해 알려면 이 페이지를 따르십시오.
uuid: A 7 Feb 465-1982-46 BE -9 E 57-E 67 B 59849579
contentOwner: Jsyal
products: sg_ Experiencemanager/Cloudmanager
topic-tags: using
discoiquuid: D 2338 C 74-3278-49 E 6-A 186-6 EF 62362509 F
translation-type: tm+mt
source-git-commit: f8cea9d52ebb01d7f5291d4dfcd82011da8dacc2

---


# 사용자 지정 코드 품질 규칙 {#custom-code-quality-rules}

이 페이지에서는 AEM Engineering의 모범 사례를 기반으로 만들어진 클라우드 관리자가 실행하는 사용자 지정 코드 품질 규칙을 설명합니다.

>[!NOTE]
>
>여기에 제공된 코드 샘플은 예시용으로만 제공됩니다.

## Sonarqube 규칙 {#sonarqube-rules}

다음 섹션에서는 Sonarqube 규칙을 강조 표시합니다.

### 잠재적으로 위험한 기능을 사용하지 마십시오. {#do-not-use-potentially-dangerous-functions}

**** 키: Cqrules: CWE -676

**** 유형: 취약점

**심각도**: major

**** 이후: 버전 2018.4.0

***thread. stop ()*** 및 ***thread. interrupt ()*** 메서드는 어려운 문제 및 경우에 따라 보안 취약점을 생성할 수 있습니다. 또한 사용량을 철저하게 모니터링하고 확인해야 합니다. 일반적으로 메시지 전달은 유사한 목표를 달성하는 더 안전한 방법입니다.

#### 준수하지 않는 코드 {#non-compliant-code}

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

### 외부에서 제어할 수 있는 형식 문자열은 사용하지 마십시오. {#do-not-use-format-strings-which-may-be-externally-controlled}

**** 키: Cqrules: CWE -134

**** 유형: 취약점

**심각도**: major

**** 이후: 버전 2018.4.0

외부 소스 (예를 들어, 요청 매개 변수 또는 사용자 생성 컨텐츠) 의 형식 문자열을 사용하면 서비스 거부 공격에 애플리케이션을 노출시킬 수 있습니다. 형식 문자열이 외부에서 제어되는 경우가 있지만 신뢰할 수 있는 소스에서만 허용되는 경우도 있습니다.

#### 준수하지 않는 코드 {#non-compliant-code-1}

```java
protected void doPost(SlingHttpServletRequest request, SlingHttpServletResponse response) {
  String messageFormat = request.getParameter("messageFormat");
  request.getResource().getValueMap().put("some property", String.format(messageFormat, "some text");
  response.sendStatus(HttpServletResponse.SC_OK);
}
```

### HTTP 요청에는 항상 소켓 및 Connect 시간 초과가 있어야 합니다. {#http-requests-should-always-have-socket-and-connect-timeouts}

**** 키: Cqrules: Connectiontimeoutmechanism

**** 유형: 버그

**심각도**: 중요 사항

**** 이후: 버전 2018.6.0

AEM 애플리케이션에서 HTTP 요청을 실행할 때는 불필요한 스레드 소비를 방지하기 위해 적절한 시간 초과가 구성되도록 해야 합니다. Java 기본 HTTP 클라이언트 (java.net.Ht tpurlconnection) 와 일반적으로 사용되는 Apache HTTP 구성 요소 클라이언트의 기본 동작은 시간 초과되지 않으므로 시간 초과를 명시적으로 설정해야 합니다. 또한 가장 좋은 방법은 이러한 시간 초과를 60 초 이하로 설정하는 것입니다.

#### 준수하지 않는 코드 {#non-compliant-code-2}

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

### @ Providertype로 주석을 달 제품 API는 고객이 구현하거나 확장할 수 없습니다. {#product-apis-annotated-with-providertype-should-not-be-implemented-or-extended-by-customers}

**** 키: cqbp -84, cqbp -84-dependencies

**** 유형: 버그

**심각도**: 중요 사항

**** 이후: 버전 2018.7.0

AEM API 에는 사용자 지정 코드별로 구현되지는 않지만, Java 인터페이스 및 클래스가 포함되어 있습니다. 예를 들어 인터페이스 *com.day.cq.wc m. api. page* 는 ***AEM 에서만 구현되도록 설계되었습니다***.

이러한 인터페이스에 새 메서드가 추가되면 이러한 추가 메서드는 이러한 인터페이스를 사용하는 기존 코드에 영향을 주지 않으므로 이러한 인터페이스에 새 메서드를 추가하면 역으로 호환되는 것으로 간주됩니다. 그러나 사용자 지정 코드가 ***이러한 인터페이스 중*** 하나를 구현하는 경우 사용자 지정 코드가 고객에 대한 이전 버전과의 호환성 위험을 유발합니다.

AEM 에서만 구현할 인터페이스 (및 클래스) 는 *org. osgi. annotation. versioning. providertype* (또는 일부의 경우 비슷한 이전 주석 *aqute. bnd. annotation. providertype*) 로 주석을 받습니다. 이 규칙은 사용자 지정 코드에 의해 이러한 인터페이스가 구현된 (또는 클래스가 확장됨) 사례를 식별합니다.

#### 준수하지 않는 코드 {#non-compliant-code-3}

```java
import com.day.cq.wcm.api.Page;

public class DontDoThis implements Page {
// implementation here
}
```

### Resourceresolver 개체는 항상 닫아야 합니다. {#resourceresolver-objects-should-always-be-closed}

**** 키: Cqrules: CQBP -72

**** 유형: 코드 냄새

**심각도**: major

**** 이후: 버전 2018.4.0

Resourceresolverfactory에서 가져온 resourceresolver 개체는 시스템 리소스를 소모합니다. Resourceresolver가 더 이상 사용되지 않을 때 이러한 리소스를 회수할 수 있는 방법이 있지만 close () 메서드를 호출하여 열려 있는 resourceresolver 객체를 명시적으로 닫는 것이 더 효율적입니다.

상대적으로 일반적인 오해는 기존 JCR 세션을 사용하여 만든 resourceresolver 개체를 명시적으로 닫거나 이렇게 하면 기본 JCR 세션이 닫히는 것입니다. 이것은 사실이 아닙니다. Resourceresolver를 여는 방식에 관계없이 더 이상 사용되지 않을 때 닫아야 합니다. Resourceresolver는 closeable 인터페이스를 구현하므로 close () 를 명시적으로 호출하는 대신 try-with-resources 구문을 사용할 수도 있습니다.

#### 준수하지 않는 코드 {#non-compliant-code-4}

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

### Sling 서블릿 경로를 사용하여 Servlet 등록 안 함 {#do-not-use-sling-servlet-paths-to-register-servlets}

**** 키: Cqrules: CQBP -75

**** 유형: 코드 냄새

**심각도**: major

**** 이후: 버전 2018.4.0

[Sling 설명서에](http://sling.apache.org/documentation/the-sling-engine/servlets.html)설명된 것처럼 경로별 바인딩은 권장되지 않습니다. 경로 바인딩 서블릿은 표준 JCR 액세스 제어를 사용할 수 없으므로 추가 보안 보안이 필요합니다. 경로 바인딩 서블릿을 사용하는 것이 아니라 저장소에서 노드를 만들고 리소스 유형별로 서블릿을 등록하는 것이 좋습니다.

#### 준수하지 않는 코드 {#non-compliant-code-5}

```java
@Component(property = {
  "sling.servlet.paths=/apps/myco/endpoint"
})
public class DontDoThis extends SlingAllMethodsServlet {
 // implementation
}
```

### caught exceptions should be logged or throw, but not both {#caught-exceptions-should-be-logged-or-thrown-but-not-both}

**** 키: Cqrules: cqbp -44—Catchandeitherlogorthrow

**** 유형: 코드 냄새

**심각도**: minor

**** 이후: 버전 2018.4.0

일반적으로 예외는 한 번만 기록해야 합니다. 예외를 여러 번 기록하면 예외가 발생한 횟수를 명확하지 않으므로 혼란이 발생할 수 있습니다. 이로 이어지는 가장 일반적인 패턴은 catch 한 예외를 기록하고 throw 합니다.

#### 준수하지 않는 코드 {#non-compliant-code-6}

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

### log 문 다음에 throw 문이 오는 것을 피하십시오. {#avoid-having-a-log-statement-immediately-followed-by-a-throw-statement}

**** 키: Cqrules: cqbp -44—Consecutivelylogandthrow

**** 유형: 코드 냄새

**심각도**: minor

**** 이후: 버전 2018.4.0

또 다른 일반적인 패턴은 메시지를 기록한 다음 예외를 바로 throw 하는 것입니다. 이것은 일반적으로 예외 메시지가 로그 파일에서 중복됨을 나타냅니다.

#### 준수하지 않는 코드 {#non-compliant-code-7}

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

### GET 또는 HEAD 요청을 처리할 때 정보 기록 방지 {#avoid-logging-at-info-when-handling-get-or-head-requests}

**** 키: Cqrules: cqbp -44—Loginfoingetorheadrequests

**** 유형: 코드 냄새

**심각도**: minor

일반적으로, 중요한 작업을 구분하는 데 정보 로그 수준을 사용해야 하며, 기본적으로 AEM 이 정보 수준 이상으로 기록하도록 구성되어 있습니다. GET 및 HEAD 메서드는 읽기 전용 작업일 뿐이므로 중요한 작업은 구성하지 않습니다. GET 또는 HEAD 요청에 대한 응답으로 정보 수준에서 로깅하면 상당한 로그 노이즈가 생성되므로 로그 파일에서 유용한 정보를 식별하기가 어렵습니다. GET 또는 HEAD 요청을 처리할 때 로깅은 문제가 발생한 경우 경고 또는 오류 수준에서, 더 자세한 문제 해결 정보가 유용한 경우 디버그 또는 추적 수준에서 수행해야 합니다.

>[!CAUTION]
>
>이것은 각 요청에 대한 액세스. log 유형 로깅에는 적용되지 않습니다.

#### 준수하지 않는 코드 {#non-compliant-code-8}

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

### logging 문의 첫 번째 매개 변수로 exception. getmessage () 를 사용하지 마십시오. {#do-not-use-exception-getmessage-as-the-first-parameter-of-a-logging-statement}

**** 키: Cqrules: cqbp -44—Exceptiongetmessageisfirstlogparam

**** 유형: 코드 냄새

**심각도**: minor

**** 이후: 버전 2018.4.0

최상의 방법으로 로그 메시지는 애플리케이션에서 예외가 발생한 위치에 대한 컨텍스트 정보를 제공해야 합니다. 또한 스택 추적을 통해 컨텍스트를 결정할 수는 있지만 일반적으로 로그 메시지는 읽고 이해하기 쉽습니다. 따라서 예외를 기록할 때에는 예외 메시지를 로그 메시지로 사용하는 것은 잘못된 관행입니다. 예외 메시지에는 잘못된 사항이 포함될 예정이지만 예외 메시지가 발생했을 때 응용 프로그램이 수행하는 작업을 기록하려면 로그 메시지를 사용해야 합니다. 예외 메시지는 여전히 기록됩니다. 메시지를 직접 지정하면 로그가 더 쉽게 이해할 수 있습니다.

#### 준수하지 않는 코드 {#non-compliant-code-9}

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

### catch 블록에서 로깅은 경고 또는 오류 수준에 있어야 합니다. {#logging-in-catch-blocks-should-be-at-the-warn-or-error-level}

**** 키: Cqrules: cqbp -44—Wrongloglevelincatchblock

**** 유형: 코드 냄새

**심각도**: minor

**** 이후: 버전 2018.4.0

이름에서 알 수 있듯이 Java 예외는 *항상 예외적인* 상황에서 사용해야 합니다. 따라서 예외가 발견되면 로그 메시지가 경고 또는 오류 중 적절한 수준에서 기록되도록 해야 합니다. 이렇게 하면 해당 메시지가 로그에서 올바로 표시됩니다.

#### 준수하지 않는 코드 {#non-compliant-code-10}

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

### 스택으로 스택 추적 안 함 {#do-not-print-stack-traces-to-the-console}

**** 키: Cqrules: cqbp -44—Exceptionprintstacktrace

**** 유형: 코드 냄새

**심각도**: minor

**** 이후: 버전 2018.4.0

앞에서 언급했듯이, 컨텍스트는 로그 메시지를 이해하는 데 매우 중요합니다. Exception. printstacktrace () 를 사용하면 스택 **추적만** 표준 오류 스트림으로 출력하여 모든 컨텍스트를 잃게 됩니다. 또한 이 메서드를 병렬로 사용하여 여러 예외를 인쇄하는 경우 AEM와 같은 다중 스레드 응용 프로그램에서는 해당 스택 추적이 겹쳐 심각한 혼란을 일으킬 수 있습니다. 예외는 로깅 프레임워크를 통해서만 기록되어야 합니다.

#### 준수하지 않는 코드 {#non-compliant-code-11}

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

**** 키: Cqrules: cqbp -44—loglevelconsoleprinters

**** 유형: 코드 냄새

**심각도**: minor

**** 이후: 버전 2018.4.0

AEM에서 로깅은 항상 SLF 4 J (로깅 프레임워크) 를 통해 수행해야 합니다. 표준 출력 또는 표준 오류 스트림으로 직접 출력하는 경우 로깅 프레임워크에서 제공하는 구조적 및 컨텍스트 정보를 잃게 되며 경우에 따라 성능 문제가 발생할 수 있습니다.

#### 준수하지 않는 코드 {#non-compliant-code-12}

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

### 하드 코딩된 /apps 및 /libs 경로 관리 방지 {#avoid-hardcoded-apps-and-libs-paths}

**** 키: Cqrules: cqbp -71

**** 유형: 코드 냄새

**심각도**: minor

**** 이후: 버전 2018.4.0

일반적으로, /libs 및 /apps로 시작하는 경로는 sling 검색 경로 (기본적으로 /libs로 설정된 경로) 와 관련하여 가장 일반적으로 경로 (경로) 로 저장되는 경로로 하드 코딩되지 않습니다. 절대 경로를 사용하면 프로젝트 라이프사이클에서만 표시되는 미세한 결함이 발생할 수 있습니다.

#### 준수하지 않는 코드 {#non-compliant-code-13}

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
