---
title: 빌드 환경
description: Cloud Manager 사용자가 코드를 빌드하고 테스트하기 위한 전문 빌드 환경에 대해 알아봅니다.
exl-id: b3543320-66d4-4358-8aba-e9bdde00d976
source-git-commit: 4c051cd1696f8a00d0278131c9521ad4dcb956a3
workflow-type: tm+mt
source-wordcount: '1044'
ht-degree: 1%

---


# 빌드 환경 {#build-environment}

Cloud Manager 사용자가 코드를 빌드하고 테스트하기 위한 전문 빌드 환경에 대해 알아봅니다.

## 환경 세부 사항 {#details}

Cloud Manager의 빌드 환경에는 다음 속성이 있습니다.

* 빌드 환경은 Ubuntu 18.04에서 파생된 Linux 기반입니다.
* Apache Maven 3.6.0이 설치됩니다.
* 설치된 Java 버전은 Oracle JDK 8u202 및 Oracle JDK 11.0.2입니다.
* 기본적으로 `JAVA_HOME`  환경 변수가 `/usr/lib/jvm/jdk1.8.0_202` 에는 Oracle JDK 8u202가 포함되어 있습니다. 섹션을 참조하십시오 [대체 Maven 실행 JDK 버전](#alternate-maven) 섹션을 참조하십시오.
* 필요한 몇 가지 추가 시스템 패키지가 설치되어 있습니다.
   * `bzip2`
   * `unzip`
   * `libpng`
   * `imagemagick`
   * `graphicsmagick`
* 섹션에 설명된 대로 빌드 시 다른 패키지를 설치할 수 있습니다 [추가 시스템 패키지를 설치하는 중입니다.](#installing-additional-system-packages)
* 모든 빌드는 깨끗한 환경에서 수행됩니다. 빌드 컨테이너는 실행 사이에 상태를 유지하지 않습니다.
* Maven은 항상 다음 세 가지 명령을 사용하여 실행됩니다.
   * `mvn --batch-mode org.apache.maven.plugins:maven-dependency-plugin:3.1.2:resolve-plugins`
   * `mvn --batch-mode org.apache.maven.plugins:maven-clean-plugin:3.1.0:clean -Dmaven.clean.failOnError=false`
   * `mvn --batch-mode org.jacoco:jacoco-maven-plugin:prepare-agent package`
* Maven은 `settings.xml` 이름이 지정된 프로파일을 사용하여 공용 Adobe 객체 저장소를 자동으로 포함하는 파일 `adobe-public`.
   * 자세한 내용은 [Adobe 공용 Maven 저장소](https://repo1.maven.org/) 자세한 내용

>[!NOTE]
>
>Cloud Manager는 `jacoco-maven-plugin`, 사용된 버전은 적어도 `0.7.5.201505241946`.

>[!TIP]
>
>Cloud Manager API 사용 방법에 대해 알아보려면 다음 추가 리소스를 참조하십시오.
>* [aio-cli-plugin-cloudmanager](https://github.com/adobe/aio-cli-plugin-cloudmanager)
>* [API 통합 만들기](https://developer.adobe.com/experience-cloud/cloud-manager/guides/getting-started/create-api-integration/)
>* [API 권한](https://developer.adobe.com/experience-cloud/cloud-manager/guides/getting-started/permissions/)


## 특정 Java 버전 사용 {#using-java-version}

기본적으로 프로젝트는 Oracle 8 JDK를 사용하여 Cloud Manager 빌드 프로세스에서 빌드됩니다. 대체 JDK를 사용하려는 고객은 두 가지 옵션을 사용할 수 있습니다.

* [Maven 도구 체인](#maven-toolchains)
* [전체 Maven 실행 프로세스에 대한 대체 JDK 버전 선택](#alternate-maven)

### Maven 도구 체인 {#maven-toolchains}

다음 [Maven Toolchain 플러그인](https://maven.apache.org/plugins/maven-toolchains-plugin/) 프로젝트에서 도구 체인 인식 Maven 플러그인 컨텍스트에서 사용할 특정 JDK(또는 도구 체인)를 선택할 수 있습니다. 이 작업은 프로젝트의 `pom.xml` 공급업체 및 버전 값을 지정하여 파일을 작성합니다. 의 샘플 섹션 `pom.xml` 파일:

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

이렇게 하면 모든 도구 체인 인식 Maven 플러그인이 Oracle JDK, 버전 11을 사용하게 됩니다.

이 메서드를 사용하는 경우 Maven 자체는 기본 JDK(Oracle 8) 및 `JAVA_HOME` 환경 변수가 변경되지 않았습니다. 따라서 와 같은 플러그인을 통해 Java 버전을 확인하거나 강제로 적용하는 경우 [Apache Maven Enforcer 플러그인](https://maven.apache.org/enforcer/maven-enforcer-plugin/) 은 작동하지 않으며 이러한 플러그인은 사용하지 않아야 합니다.

현재 사용 가능한 공급업체/버전 조합은 다음과 같습니다.

| 공급업체 | 버전 |
|---|---|
| oracle | 1.8 |
| oracle | 1.11 |
| oracle | 11 |
| 태양 | 1.8 |
| 태양 | 1.11 |
| 태양 | 11 |

>[!NOTE]
>
>2022년 4월부터 AEM 애플리케이션 개발 및 작업을 위한 기본 JDK는 Oracle JDK입니다. Cloud Manager의 빌드 프로세스는 Maven 도구 체인에서 대체 옵션을 명시적으로 선택한 경우에도 Oracle JDK를 사용하여 자동으로 로 전환됩니다. 자세한 내용은 [4월 릴리스 노트](/help/release-notes/2022/2022-4-0.md) 자세한 내용

### 대체 Maven 실행 JDK 버전 {#alternate-maven}

또한 전체 Maven 실행에 대한 JDK로 Oracle 8 또는 Oracle 11을 선택할 수도 있습니다. 도구 체인 옵션과 달리 도구 체인 구성이 도구 체인 인식 Maven 플러그인에 대해 여전히 도구 체인 구성이 적용되는 경우에도 도구 체인 구성이 설정되어 있지 않으면 모든 플러그인에 사용되는 JDK가 변경됩니다. 따라서 를 사용하여 Java 버전을 확인하고 적용합니다 [Apache Maven Enforcer 플러그인](https://maven.apache.org/enforcer/maven-enforcer-plugin/) 사용할 수 있습니다.

이렇게 하려면 이름이 인 파일을 만듭니다 `.cloudmanager/java-version` 파이프라인에서 사용하는 git 리포지토리 분기입니다. 이 파일에는 다음 내용 중 하나가 있을 수 있습니다. `11` 또는 `8`. 다른 값은 무시됩니다. If `11` 이 지정되면 Oracle 11이 사용되고 `JAVA_HOME` 환경 변수가 `/usr/lib/jvm/jdk-11.0.2`. If `8` 이 지정되면 Oracle 8이 사용되고 `JAVA_HOME` 환경 변수가 `/usr/lib/jvm/jdk1.8.0_202`.

## 환경 변수 {#environment-variables}

### 표준 환경 변수 {#standard-environ-variables}

경우에 따라 프로그램 또는 파이프라인에 대한 정보를 기반으로 빌드 프로세스를 변경해야 할 수 있습니다.

예를 들어, gulp와 같은 도구를 통해 빌드 시간 JavaScript 축소를 수행하는 경우, 스테이징 및 프로덕션을 위해 빌드하는 것이 아니라 개발 환경을 위해 빌드할 때 다른 축소 수준을 사용하려는 경우가 있을 수 있습니다.

이를 지원하기 위해 Cloud Manager는 모든 실행을 위해 빌드 컨테이너에 표준 환경 변수를 추가합니다.

| 변수 이름 | 설명 |
|---|---|
| `CM_BUILD` | 항상 로 설정 `true` |
| `BRANCH` | 실행을 위해 구성된 분기 |
| `CM_PIPELINE_ID` | 숫자 파이프라인 식별자 |
| `CM_PIPELINE_NAME` | 파이프라인 이름 |
| `CM_PROGRAM_ID` | 숫자 프로그램 식별자 |
| `CM_PROGRAM_NAME` | 프로그램 이름 |
| `ARTIFACTS_VERSION` | 스테이징 또는 프로덕션 파이프라인의 경우 Cloud Manager에서 생성한 가상 버전입니다 |

### 파이프라인 변수 {#pipeline-variables}

경우에 따라 빌드 프로세스는 Git 리포지토리에 배치하기에 적합하지 않거나 동일한 분기를 사용하여 파이프라인 실행 간에 변경해야 하는 특정 구성 변수에 따라 달라질 수 있습니다.

Cloud Manager를 사용하면 이러한 변수를 파이프라인별로 Cloud Manager API 또는 Cloud Manager CLI를 통해 구성할 수 있습니다. 변수는 일반 텍스트로 저장되거나, 나머지는 암호화될 수 있습니다. 어느 경우든 변수는 빌드 환경 내에서 환경 변수로 사용할 수 있으며 이 변수는 빌드 환경에서 참조할 수 있습니다 `pom.xml` 파일 또는 기타 빌드 스크립트.

CLI를 사용하여 변수를 설정하려면 다음과 유사한 명령을 실행합니다.

```shell
$ aio cloudmanager:set-pipeline-variables PIPELINEID --variable MY_CUSTOM_VARIABLE test
```

현재 변수는 다음과 유사한 명령을 사용하여 나열할 수 있습니다.

```shell
$ aio cloudmanager:list-pipeline-variables PIPELINEID
```

변수는 특정 제한 사항을 준수해야 합니다.

* 변수 이름에는 영숫자와 밑줄(`_`).
   * 규칙에 따라 이름은 모두 대문자로 지정해야 합니다.
* 파이프라인당 200개의 변수가 제한됩니다.
* 각 이름은 100자 미만이어야 합니다.
* 각 문자열 값은 2048자 미만이어야 합니다.
* 각 secretString 값은 500자 미만이어야 합니다.

Maven 내에서 사용하는 경우 `pom.xml` 파일에서 이러한 변수는 일반적으로 다음과 유사한 구문을 사용하여 Maven 속성에 매핑하는 데 유용합니다.

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

일부 빌드가 제대로 작동하려면 추가 시스템 패키지를 설치해야 합니다. 예를 들어, 빌드는 Python 또는 Ruby 스크립트를 호출할 수 있으므로 적절한 언어 해석기를 설치해야 합니다. 이 작업은 [`exec-maven-plugin`](https://www.mojohaus.org/exec-maven-plugin/) APT를 호출합니다. 일반적으로 이 실행은 Cloud Manager 관련 Maven 프로필에 래핑되어야 합니다. 예를 들어 Python을 설치하려면

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

이와 동일한 기술을 사용하여 언어별 패키지(예: `gem` RubyGems 또는 `pip` Python 패키지

>[!NOTE]
>
>이러한 방식으로 시스템 패키지를 설치해도 Adobe Experience Manager 실행에 사용되는 런타임 환경에 설치되지 않습니다. AEM 환경에 시스템 패키지가 설치되어 필요한 경우 Adobe 담당자에게 문의하십시오.
