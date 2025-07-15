---
title: 빌드 환경
description: Cloud Manager 사용자가 코드를 빌드하고 테스트하기 위해 사용하는 특수한 빌드 환경에 대해 알아보십시오.
exl-id: b3543320-66d4-4358-8aba-e9bdde00d976
source-git-commit: e9f3ac70735a95a15b1f63cf40496672162de777
workflow-type: tm+mt
source-wordcount: '1161'
ht-degree: 83%

---


# 빌드 환경 {#build-environment}

Cloud Manager 사용자가 코드를 빌드하고 테스트하기 위해 사용하는 특수한 빌드 환경에 대해 알아보십시오.

## 환경 세부 정보 {#details}

Cloud Manager의 빌드 환경에는 다음과 같은 속성이 있습니다.

* 빌드 환경은 Linux 기반이며 Ubuntu 22.04에서 파생되었습니다.
* Apache Maven 3.9.4가 설치되어 있습니다.
   * Adobe는 사용자가 [HTTP 대신 HTTPS를 사용하도록 Maven 저장소를 업데이트할 것](#https-maven)을 권장합니다.
* 설치된 Java 버전은 Oracle JDK 8u401 및 Oracle JDK 11.0.22입니다.
   * `/usr/lib/jvm/jdk1.8.0_401`
   * `/usr/lib/jvm/jdk-11.0.22`
* 기본적으로 `JAVA_HOME` 환경 변수는 Oracle JDK 8u401을 포함하는 `/usr/lib/jvm/jdk1.8.0_401`로 설정됩니다. 자세한 내용은 [대체 Maven 실행 JDK 버전](#alternate-maven) 섹션을 참조하십시오.
* 필요한 몇 가지 추가 시스템 패키지가 설치되어 있습니다.
   * `bzip2`
   * `unzip`
   * `libpng`
   * `imagemagick`
   * `graphicsmagick`
* [추가 시스템 패키지 설치](#installing-additional-system-packages) 섹션에 설명된 대로 빌드 시 다른 패키지를 설치할 수 있습니다.
* 모든 빌드는 완전히 새로운 환경에서 수행됩니다. 빌드 컨테이너는 실행 간에 상태를 유지하지 않습니다.
* Maven은 다음 세 가지 명령을 사용하여 실행됩니다.
   * `mvn --batch-mode org.apache.maven.plugins:maven-dependency-plugin:3.1.2:resolve-plugins`
   * `mvn --batch-mode org.apache.maven.plugins:maven-clean-plugin:3.1.0:clean -Dmaven.clean.failOnError=false`
   * `mvn --batch-mode org.jacoco:jacoco-maven-plugin:prepare-agent package`
* Maven은 `adobe-public`이라는 프로필을 사용하여 자동으로 공개 Adobe 아티팩트 저장소를 포함하는 `settings.xml` 파일로 시스템 수준에서 구성됩니다. 자세한 내용은 [Adobe 공개 Maven 저장소](https://repo1.maven.org/)를 참조하십시오.
* Node.js 18은 [프론트엔드 파이프라인](/help/overview/ci-cd-pipelines.md)에 사용할 수 있습니다.

>[!IMPORTANT]
>Maven 툴체인 지원은 Cloud Manager 2025.06.0부터 제거되었습니다. JDK 선택은 이제 `.cloudmanager/java-version`을(를) 통해서만 지원됩니다. 자세한 내용은 [특정 Java 버전 사용](#using-java-version)을 참조하십시오.

>[!NOTE]
>
>Cloud Manager에서는 `jacoco-maven-plugin`의 특정 버전을 정의하지는 않지만 사용되는 버전은 `0.7.5.201505241946` 이상이어야 합니다.

>[!TIP]
>
>Cloud Manager API를 사용하는 방법에 대한 자세한 내용은 다음 추가 리소스를 참조하십시오.
>
>* [aio-cli-plugin-cloudmanager](https://github.com/adobe/aio-cli-plugin-cloudmanager)
>* [API 통합 만들기](https://developer.adobe.com/experience-cloud/cloud-manager/guides/getting-started/create-api-integration/)
>* [API 권한](https://developer.adobe.com/experience-cloud/cloud-manager/guides/getting-started/permissions/)

## HTTPS Maven 저장소 {#https-maven}

Cloud Manager [2023.10.0](/help/release-notes/2023/2023-10-0.md)에서는 빌드 환경에 대한 롤링 업데이트(2023.12.0 릴리스로 완료)를 시작했으며, 여기에는 Maven 3.8.8 업데이트가 포함되어 있습니다. Maven 3.8.1에 도입된 주요 변경 사항은 잠재적인 취약점을 완화하기 위한 보안 강화 기능입니다. 구체적으로 Maven은 이제 [Maven 릴리스 정보](https://maven.apache.org/docs/3.8.1/release-notes.html#cve-2021-26291)에 설명된 바와 같이 안전하지 않은 모든 `http://*` 미러를 기본적으로 비활성화합니다.

이러한 보안 강화로 인해 일부 사용자는 빌드 단계에서 문제에 직면할 수 있으며, 특히 안전하지 않은 HTTP 연결을 사용하는 Maven 저장소에서 아티팩트를 다운로드할 때 이와 같은 문제가 보다 빈번하게 발생할 수 있습니다.

업데이트된 버전을 원활하게 사용하기 위해 Adobe는 사용자가 HTTP 대신 HTTPS를 사용하도록 Maven 저장소를 업데이트할 것을 권장합니다. 이러한 조정은 업계에서 점점 더 보안 통신 프로토콜로 전환하는 추세에 맞춰 안전하고 안정적인 빌드 프로세스를 유지하는 데 도움이 될 것으로 기대합니다.

## 특정 Java 버전 사용 {#using-java-version}

기본적으로 프로젝트는 Oracle 8 JDK를 사용하여 Cloud Manager 빌드 프로세스를 통해 구축됩니다. 대체 JDK를 사용하려는 고객은 전체 Maven 실행 프로세스에 대한 대체 JDK 버전을 선택할 수 있습니다.

>[!IMPORTANT]
>
>Maven 툴체인은 Cloud Manager 2025.06.0에서 더 이상 지원되지 않습니다. Maven-toolchains-plugin 구성이 포함된 파이프라인이 `Cannot find matching toolchain definitions.`(으)로 실패합니다. 대신 `.cloudmanager/java-version` 파일을 사용하여 JDK 11, 17 또는 21을 선택하십시오.
>
>**마이그레이션 지침:**
>
>1. 소스 제어에 커밋된 `org.apache.maven.plugins:maven-toolchains-plugin` 항목과 `toolchains.xml`을(를) 삭제하여 도구 체인을 제거합니다.
>1. `.cloudmanager/java-version`대체 Maven 실행 JDK 버전[에 설명된 대로 ](#alternate-maven)(21, 17 또는 11)이 포함된 JDK를 선택하십시오.
>1. Adobe에서는 Cloud Manager 빌드 캐시를 지우거나 새 파이프라인 실행을 트리거하는 것이 좋습니다.
>

<!--DEPRECATED 
### Maven Toolchains {#maven-toolchains}

The [Maven Toolchains plug-in](https://maven.apache.org/plugins/maven-toolchains-plugin/) lets projects select a specific JDK (or toolchain) to use in the context of toolchains-aware Maven plug-ins. This process is done in the project's `pom.xml` file by specifying a vendor and version value. A sample section in the `pom.xml` file is the following:

```xml
        <plugin>
    <groupId>org.apache.maven.plugins</groupId>
    <artifactId>maven-toolchains-plugin</artifactId>
    <version>1.1</version>
    <executions>
        <execution>
            <goals>
                <goal>toolchain</goal>
            </goals>
        </execution>
    </executions>
    <configuration>
        <toolchains>
            <jdk>
                <version>11</version>
                <vendor>oracle</vendor>
            </jdk>
        </toolchains>
    </configuration>
</plugin>

```

This process causes all toolchains-aware Maven plug-ins to use the Oracle JDK, version 11.

When using this method, Maven itself still runs using the default JDK (Oracle 8) and the `JAVA_HOME` environment variable is not changed. Therefore, checking or enforcing the Java version through plug-ins like the [Apache Maven Enforcer Plug-in](https://maven.apache.org/enforcer/maven-enforcer-plugin/) does not work and such plug-ins must not be used.

The currently available vendor/version combinations are:

|Vendor|Version|
|---|---|
| Oracle |1.8|
| Oracle |1.11|
| Oracle |11|
| Sun |1.8|
| Sun |1.11|
| Sun |11|

>[!NOTE]
>
>Starting April 2022, Oracle JDK is going to be the default JDK for the development and operation of AEM applications. Cloud Manager's build process automatically switches to using Oracle JDK, even if an alternative option is explicitly selected in the Maven toolchain. See the [April release notes](/help/release-notes/2022/2022-4-0.md) for more details. -->

### 대체 Maven 실행 JDK 버전 {#alternate-maven}

전체 Maven 실행에 대한 JDK로 Oracle 8 또는 Oracle 11을 선택할 수 있습니다. 이 방법은 모든 플러그인에 사용되는 JDK를 변경합니다. 따라서 [Apache Maven Enforcer 플러그인](https://maven.apache.org/enforcer/maven-enforcer-plugin/)을 사용한 Java 버전 확인 및 시행이 작동합니다.

이렇게 하려면 파이프라인에서 사용하는 Git 저장소 분기에 `.cloudmanager/java-version`이라는 파일을 생성합니다. 이 파일은 콘텐츠 `11` 또는 `8`을 가질 수 있습니다. 다른 모든 값은 무시됩니다. `11`을(를) 지정하면 시스템에서 Oracle 11을 사용하고 `JAVA_HOME` 환경 변수를 `/usr/lib/jvm/jdk-11.0.22`(으)로 설정합니다. `8`을(를) 지정하면 시스템에서 Oracle 8을 사용하고 `JAVA_HOME` 환경 변수를 `/usr/lib/jvm/jdk1.8.0_401`(으)로 설정합니다.

## 환경 변수 {#environment-variables}

### 표준 환경 변수 {#standard-environ-variables}

경우에 따라 프로그램 또는 파이프라인에 대한 정보를 기반으로 빌드 프로세스를 변경해야 할 수도 있습니다.

예를 들어 JavaScript 최소화를 위해 gulp와 같은 도구를 사용하는 경우, 개발과 스테이징 및 프로덕션 환경에 대해 다른 최소화 수준을 선호할 수 있습니다.

이를 지원하기 위해 Cloud Manager는 모든 실행 시 빌드 컨테이너에 표준 환경 변수를 추가합니다.

| 변수 이름 | 설명 |
|---|---|
| `CM_BUILD` | 항상 `true`로 설정 |
| `BRANCH` | 실행에 대해 구성된 분기 |
| `CM_PIPELINE_ID` | 숫자 파이프라인 식별자 |
| `CM_PIPELINE_NAME` | 파이프라인 이름 |
| `CM_PROGRAM_ID` | 숫자 프로그램 식별자 |
| `CM_PROGRAM_NAME` | 프로그램 이름 |
| `ARTIFACTS_VERSION` | 스테이징 또는 프로덕션 파이프라인의 경우 Cloud Manager에서 생성된 통합 버전 |

### 표준 환경 변수 가용성 {#availability}

표준 환경 변수는 여러 곳에서 사용할 수 있습니다.

#### 작성, 미리보기 및 게시 환경 {#author-preview-publish}

일반 환경 변수와 시크릿은 작성, 미리보기 및 게시 환경에서 사용할 수 있습니다.

#### Dispatcher {#dispatcher}

[Dispatcher](https://experienceleague.adobe.com/ko/docs/experience-manager-dispatcher/using/dispatcher)에는 일반 환경 변수만 사용할 수 있습니다. 시크릿은 사용할 수 없습니다.

그러나 환경 변수는 `IfDefine` 지침에서 사용할 수 없습니다.

>[!TIP]
>
>배포하기 전에 [로컬에서 Dispatcher](https://experienceleague.adobe.com/ko/docs/experience-manager-learn/cloud-service/local-development-environment-set-up/dispatcher-tools)를 사용하여 환경 변수 사용을 확인합니다.

#### OSGi 구성 {#osgi}

일반 환경 변수 및 시크릿 모두 [OSGi 구성](https://experienceleague.adobe.com/ko/docs/experience-manager-65/content/implementing/deploying/configuring/configuring-osgi)에서 사용할 수 있습니다.

### 파이프라인 변수 {#pipeline-variables}

경우에 따라 빌드 프로세스가 Git 저장소에 배치하기에 부적절하거나 동일한 분기를 사용하는 파이프라인 실행 간에 달라져야 하는 특정 구성 변수에 따라 달라질 수 있습니다.

Cloud Manager를 사용하면 파이프라인 단위로 Cloud Manager API 또는 Cloud Manager CLI를 통해 이러한 변수를 구성할 수 있습니다. 변수는 일반 텍스트로 저장되거나 사용하지 않을 때 암호화될 수 있습니다. 두 경우 모두 `pom.xml` 파일 또는 다른 빌드 스크립트 내에서 참조할 수 있는 환경 변수로 빌드 환경 내에서 변수를 사용할 수 있습니다.

CLI를 사용하여 변수를 설정하려면 다음과 유사한 명령을 실행합니다.

```shell
$ aio cloudmanager:set-pipeline-variables PIPELINEID --variable MY_CUSTOM_VARIABLE test
```

현재 변수는 다음과 유사한 명령을 사용하여 나열할 수 있습니다.

```shell
$ aio cloudmanager:list-pipeline-variables PIPELINEID
```

변수는 특정 제한 사항을 준수해야 합니다.

* 변수 이름에는 영숫자와 밑줄(`_`)만 포함될 수 있습니다.
   * 규칙상 이름은 모두 대문자로 해야 합니다.
* 파이프라인당 200개의 변수 제한이 있습니다.
* 각 이름은 100자 이하여야 합니다.
* 각 문자열 값은 2048자 이하여야 합니다.
* 각 `secretString` 값은 500자 이하여야 합니다.

Maven `pom.xml` 파일 내에서 사용할 경우, 일반적으로 다음과 유사한 구문을 사용하여 이러한 변수를 Maven 속성에 매핑하는 것이 유용합니다.

```xml
        <profile>
            <id>cmBuild</id>
            <activation>
                <property>
                    <name>env.CM_BUILD</name>
                </property>
            </activation>
            <properties>
                <my.custom.property>${env.MY_CUSTOM_VARIABLE}</my.custom.property> 
            </properties>
        </profile>
```

## 추가 시스템 패키지 설치 {#installing-additional-system-packages}

완벽한 작동을 위해서는 일부 빌드에 추가 시스템 패키지를 설치해야 합니다. 예를 들어 빌드는 Python 또는 Ruby 스크립트를 호출할 수 있으며, 결과적으로 적절한 언어 인터프리터가 설치되어야 합니다. 이 시나리오는 APT를 호출하기 위해 [`exec-maven-plugin`](https://www.mojohaus.org/exec-maven-plugin/)를 호출하여 수행할 수 있습니다. 이 실행은 일반적으로 Cloud Manager 전용 Maven 프로필로 래핑해야 합니다. 예를 들어 Python을 설치하려면 다음 작업을 수행해야 합니다.

```xml
        <profile>
            <id>install-python</id>
            <activation>
                <property>
                        <name>env.CM_BUILD</name>
                </property>
            </activation>
            <build>
                <plugins>
                    <plugin>
                        <groupId>org.codehaus.mojo</groupId>
                        <artifactId>exec-maven-plugin</artifactId>
                        <version>1.6.0</version>
                        <executions>
                            <execution>
                                <id>apt-get-update</id>
                                <phase>validate</phase>
                                <goals>
                                    <goal>exec</goal>
                                </goals>
                                <configuration>
                                    <executable>apt-get</executable>
                                    <arguments>
                                        <argument>update</argument>
                                    </arguments>
                                </configuration>
                            </execution>
                            <execution>
                                <id>install-python</id>
                                <phase>validate</phase>
                                <goals>
                                    <goal>exec</goal>
                                </goals>
                                <configuration>
                                    <executable>apt-get</executable>
                                    <arguments>
                                        <argument>install</argument>
                                        <argument>-y</argument>
                                        <argument>--no-install-recommends</argument>
                                        <argument>python</argument>
                                    </arguments>
                                </configuration>
                            </execution>
                        </executions>
                    </plugin>
                </plugins>
            </build>
        </profile>
```

이 기술은 언어별 패키지를 설치하는 데에도 사용할 수 있습니다. 즉, RubyGems에는 `gem` 또는 Python Package에는 `pip`를 사용하는 것입니다.

>[!NOTE]
>
>이 방법으로 시스템 패키지를 설치하면 Adobe Experience Manager 실행에 사용되는 런타임 환경에 설치되지 않습니다. AEM 환경에 시스템 패키지를 설치해야 하는 경우 Adobe 담당자에게 문의하십시오.
