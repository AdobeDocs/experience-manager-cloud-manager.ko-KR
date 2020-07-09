---
title: AEM 애플리케이션 프로젝트 만들기
seo-title: AEM 애플리케이션 프로젝트 만들기
description: 'null'
seo-description: 클라우드 관리자를 시작할 때 AEM 프로젝트 설정에 대한 자세한 내용을 살펴보려면 이 페이지를 따르십시오.
uuid: 7b976ebf-5358-49d8-a58d-0bae026303fa
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: getting-started
discoiquuid: 76c1a8e4-d66f-4a3b-8c0c-b80c9e17700e
translation-type: tm+mt
source-git-commit: 33aeba59c149e5ba3300b9d798356ec5e9bcd4b8
workflow-type: tm+mt
source-wordcount: '1479'
ht-degree: 1%

---


# AEM 애플리케이션 프로젝트 만들기 {#create-an-aem-application-project}

## 마법사를 사용하여 AEM 애플리케이션 프로젝트 만들기 {#using-wizard-to-create-an-aem-application-project}

고객이 Cloud Manager에 온보드 방식을 사용하는 경우 빈 git 저장소가 제공됩니다. 현재 Adobe Managed Services(AMS) 고객(또는 AMS로 마이그레이션하는 온-프레미스 AEM 고객)은 일반적으로 프로젝트 코드가 git(또는 다른 버전 제어 시스템)에 이미 있으며 프로젝트를 Cloud Manager git 리포지토리로 가져옵니다. 그러나 새 고객은 기존 프로젝트를 가지고 있지 않습니다.

신규 고객 확보를 지원하기 위해 Cloud Manager는 이제 최소한의 AEM 프로젝트를 시작점으로 만들 수 있습니다. 이 프로세스는 AEM 프로젝트 [**원형을 기반으로 합니다&#x200B;**](https://github.com/Adobe-Marketing-Cloud/aem-project-archetype).


Cloud Manager에서 AEM 애플리케이션 프로젝트를 만들려면 아래 절차를 따르십시오.

1. Cloud Manager에 로그인하고 기본 프로그램 설정이 완료되면 저장소가 비어 있는 경우 **개요** 화면에 특별 작업 카드가 표시됩니다.

   ![](assets/image2018-10-3_14-29-44.png)

1. 만들기를 **클릭하여** AEM 프로젝트 원형에서 필요한 매개 변수를 제공할 수 있는 대화 상자를 엽니다. 기본 양식에서는 대화 상자에 두 개의 값이 표시됩니다.

   * **제목** - 기본적으로 *프로그램 이름으로 설정됩니다.*

   * **새 분기 이름** - 기본적으로 *마스터*

   ![](assets/screen_shot_2018-10-08at55825am.png)

   대화 상자에는 대화 상자의 하단의 핸들을 클릭하여 열 수 있는 서랍이 있습니다. 확장된 형식의 대화 상자에는 원형 유형에 대한 모든 구성 매개 변수가 표시됩니다. 이러한 매개 변수 중에는 제목을 기반으로 생성된 기본값이 **있습니다**.

   ![](assets/screen_shot_2018-10-08at60032am.png)

   >[!NOTE]
   >
   >예를 들어 **제목** 이 ***We.Finance인***&#x200B;경우 Base Maven Artifact Id 매개 변수가 ***com.wefinance로 생성됩니다***. 원하는 경우 이러한 값을 변경할 수 있습니다.
   >
   >
   >예를 들어 생성된 ***value com.wefinance에서*** net.wefinance ***로 변경할 수 있습니다***.

1. 이전 단계 **에서 [만들기** ]를 클릭하여 원형을 사용하여 시작 프로젝트를 만들고 이름이 지정된 git 분기에 커밋합니다. 이렇게 하면 파이프라인을 설정할 수 있습니다.

## 프로젝트 설정 {#setting-up-your-project}

### 프로젝트 설정 세부 사항 수정 {#modifying-project-setup-details}

Cloud Manager를 사용하여 성공적으로 구축 및 배포하려면 기존 AEM 프로젝트에 몇 가지 기본 규칙을 준수해야 합니다.

* 프로젝트는 Apache Maven을 사용하여 빌드해야 합니다.
* Git 저장소의 루트에 *pom.xml* 파일이 있어야 합니다. 이 *pom.xml* 파일은 하위 모듈을 여러 개 참조할 수 있으며, 이 경우 다른 하위 모듈 등이 있을 수 있습니다. 필요한 경우.

* pom.xml ** 파일에서 추가 Maven 객체 저장소에 대한 참조를 추가할 수 있습니다. 그러나 암호로 보호되거나 네트워크로 보호된 객체 저장소에 대한 액세스는 지원되지 않습니다.
* 배포 가능한 컨텐츠 패키지는 *target* 이라는 디렉토리에 포함되어 있는 컨텐츠 패키지 *zip*&#x200B;파일을 검색하여 찾을 수 있습니다. 모든 수의 하위 모듈에서는 콘텐츠 패키지를 생성할 수 있습니다.

* 배포 가능한 Dispatcher 가공물은 *conf* 및 conf.d라는 이름의 디렉토리가 있는 zip *파일(* target *디렉토리에 포함됨)을 검색하여* **&#x200B;검색됩니다.

* 둘 이상의 컨텐츠 패키지가 있는 경우 패키지 배포 순서가 보장되지 않습니다. 특정 주문이 필요한 경우 컨텐츠 패키지 종속성을 사용하여 순서를 정의할 수 있습니다. 배포에서 패키지를 [건너뛸](#skipping-content-packages) 수 있습니다.

<!-- 

Comment Type: annotation
Last Modified By: jsyal
Last Modified Date: 2018-10-08T09:20:10.106-0400

2018.8.0: added existing in the opening sentence

 -->

## 빌드 환경 세부 사항 {#build-environment-details}

Cloud Manager는 전문적인 빌드 환경을 사용하여 코드를 작성하고 테스트합니다. 이 환경에는 다음과 같은 속성이 있습니다.

* 빌드 환경은 Linux 기반이며 Ubuntu 18.04에서 파생됩니다.
* Apache Maven 3.6.0이 설치되어 있습니다.
* 설치된 Java 버전은 Oracle JDK 8u202 및 11.0.2입니다.
* 다음과 같은 몇 가지 추가 시스템 패키지가 설치되어 있습니다.

   * bzip2
   * 압축 해제
   * libpng
   * imagemagick
   * graphicsmagick

* 다른 패키지는 [아래](#installing-additional-system-packages)설명에 따라 빌드 시간에 설치할 수 있습니다.
* 모든 빌드는 본래 환경에서 수행됩니다. 빌드 컨테이너는 실행 사이에 상태를 유지하지 않습니다.
* Maven은 항상 명령을 사용하여 실행됩니다. *mvn —batch-mode clean org.jacoco:jacoco-maven-plugin:pref-agent package*
* Maven은 공개 Adobe Artifact 저장소를 자동으로 포함하는 settings.xml 파일을 사용하여 시스템 수준에서 **구성됩니다** . (자세한 내용은 [Adobe Public Maven Repository](https://repo.adobe.com/) 를 참조하십시오.)

### Java 11 사용 {#using-java-11}

Cloud Manager는 이제 Java 8과 Java 11을 모두 사용하여 고객 프로젝트 작성을 지원합니다. 기본적으로 프로젝트는 Java 8을 사용하여 빌드됩니다. 프로젝트에서 Java 11을 사용하려는 고객은 [Apache Maven Toolchain 플러그인을 사용할 수 있습니다](https://maven.apache.org/plugins/maven-toolchains-plugin/).

이렇게 하려면 pom.xml 파일에서 다음과 같은 `<plugin>` 항목을 추가합니다.

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

>[!NOTE]
>지원되는 공급업체는 Oracle 및 Sun Microsystems이며 지원되는 버전은 1.8, 1.11 및 11입니다.

## 환경 변수 {#environment-variables}

### 표준 환경 변수 {#standard-environ-variables}

경우에 따라 고객은 프로그램 또는 파이프라인에 대한 정보를 기반으로 빌드 프로세스를 변경해야 합니다.

예를 들어, gulp와 같은 도구를 통해 빌드 타임 JavaScript Minification을 수행하는 경우 준비 및 제작을 위해 만드는 것이 아니라 개발 환경을 위해 빌드할 때 다른 축소 수준을 사용하고자 할 수 있습니다.

이를 지원하기 위해 Cloud Manager는 모든 실행을 위해 이러한 표준 환경 변수를 빌드 컨테이너에 추가합니다.

| **변수 이름** | **정의** |
|---|---|
| CM_BUILD | 항상 &quot;true&quot;로 설정 |
| 분기 | 실행을 위해 구성된 분기 |
| CM_PIPELINE_ID | 숫자 파이프라인 식별자 |
| CM_PIPELINE_NAME | 파이프라인 이름 |
| CM_PROGRAM_ID | 숫자 프로그램 식별자 |
| CM_PROGRAM_NAME | 프로그램 이름 |
| ARTIFACTS_VERSION | 스테이지 또는 프로덕션 파이프라인의 경우 Cloud Manager에서 생성된 합성 버전 |

### 사용자 지정 환경 변수 {#custom-variables}

경우에 따라 고객의 빌드 프로세스는 git 리포지토리에 배치하기에 부적절한 특정 구성 변수에 따라 달라질 수 있습니다. Cloud Manager를 사용하면 고객별로 CSE(Customer Success Engineer)가 이러한 변수를 구성할 수 있습니다.

이러한 변수는 보안 저장소 위치에 저장되며 특정 고객의 빌드 컨테이너에서만 볼 수 있습니다. 이 기능을 사용하려면 CSE에 연락하여 변수를 구성해야 합니다.
구성되면 이러한 변수를 환경 변수로 사용할 수 있습니다. 이들을 Maven 속성으로 사용하려면 위에서 설명한 프로필 내에서 pom.xml 파일에서 참조할 수 있습니다.


```xml
        <profile>
            <id>cmBuild</id>
            <activation>
                  <property>
                        <name>env.CM_BUILD</name>
                  </property>
            </activation>
            <properties>
                  <my.custom.property>${env.MY_CUSTOM_PROPERTY}</my.custom.property>  
            </properties>
        </profile>
```

>[!NOTE]
>환경 변수 이름에는 영숫자 및 밑줄(_)만 사용할 수 있습니다. 관례상, 이름은 모두 대문자여야 합니다.

## Cloud Manager에서 마스터 프로필 활성화 {#activating-maven-profiles-in-cloud-manager}

일부 제한된 경우, 개발자 워크스테이션에서 실행되는 경우와 달리 Cloud Manager 내에서 실행할 때 빌드 프로세스를 약간 변경해야 할 수 있습니다. 이러한 경우 Maven [Profiles를](https://maven.apache.org/guides/introduction/introduction-to-profiles.html) 사용하여 Cloud Manager를 비롯한 다양한 환경에서 빌드가 달라지는 방법을 정의할 수 있습니다.

Cloud Manager 빌드 환경 내에서 마스터 프로필의 활성화는 위에 설명된 CM_BUILD 환경 변수를 찾아 수행해야 합니다. Cloud Manager 빌드 환경 외부에서만 사용하도록 만들어진 프로필은 이 변수의 개념을 찾아 수행해야 합니다.

예를 들어 빌드가 Cloud Manager 내에서 실행되는 경우에만 간단한 메시지를 출력하려는 경우 다음을 수행합니다.

```xml
        <profile>
            <id>cmBuild</id>
            <activation>
                  <property>
                        <name>env.CM_BUILD</name>
                  </property>
            </activation>
            <build>
                <plugins>
                    <plugin>
                        <artifactId>maven-antrun-plugin</artifactId>
                        <version>1.8</version>
                        <executions>
                            <execution>
                                <phase>initialize</phase>
                                <configuration>
                                    <target>
                                        <echo>I'm running inside Cloud Manager!</echo>
                                    </target>
                                </configuration>
                                <goals>
                                    <goal>run</goal>
                                </goals>
                            </execution>
                        </executions>
                    </plugin>
                </plugins>
            </build>
        </profile>
```

>[!NOTE]
>
>개발자 워크스테이션에서 이 프로파일을 테스트하려면 명령줄(포함) 또는 IDE(Integrated Development Environment)에서 활성화할 수 `-PcmBuild`있습니다.

빌드가 Cloud Manager 외부에서 실행되는 경우에만 간단한 메시지를 출력하려는 경우 다음을 수행합니다.

```xml
        <profile>
            <id>notCMBuild</id>
            <activation>
                  <property>
                        <name>!env.CM_BUILD</name>
                  </property>
            </activation>
            <build>
                <plugins>
                    <plugin>
                        <artifactId>maven-antrun-plugin</artifactId>
                        <version>1.8</version>
                        <executions>
                            <execution>
                                <phase>initialize</phase>
                                <configuration>
                                    <target>
                                        <echo>I'm running outside Cloud Manager!</echo>
                                    </target>
                                </configuration>
                                <goals>
                                    <goal>run</goal>
                                </goals>
                            </execution>
                        </executions>
                    </plugin>
                </plugins>
            </build>
        </profile>
```

## 추가 시스템 패키지 설치 {#installing-additional-system-packages}

일부 빌드는 완전히 작동하도록 추가 시스템 패키지를 설치해야 합니다. 예를 들어 빌드는 Python 또는 Ruby 스크립트를 호출할 수 있으므로 적절한 언어 인터프리터를 설치해야 합니다. 이 작업은 APT를 호출하기 위해 [exec-maven-plugin](https://www.mojohaus.org/exec-maven-plugin/) 을 호출하여 수행할 수 있습니다. 이 실행은 일반적으로 클라우드 관리자별 Maven 프로필로 둘러싸야 합니다. 예를 들어, python을 설치하려면:

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

이와 동일한 기술을 사용하여 RubyGems용 또는 Python Packages `gem` 용 언어 관련 패키지를 설치할 수 `pip` 있습니다.

>[!NOTE]
>
>이러한 방식으로 시스템 패키지를 설치해도 Adobe Experience Manager을 실행하는 데 사용되는 런타임 환경에 설치되지 **않습니다** . AEM 환경에 시스템 패키지를 설치해야 하는 경우 고객 성공 엔지니어(CSE)에게 문의하십시오.

## 콘텐츠 패키지 건너뛰기 {#skipping-content-packages}

Cloud Manager에서 빌드는 콘텐츠 패키지를 수에 관계없이 생성할 수 있습니다.
다양한 이유로, 컨텐츠 패키지를 배포하지 않고 판매하는 것이 좋을 수 있습니다. 예를 들어 테스트용으로만 사용되는 컨텐츠 패키지를 빌드하거나 빌드 프로세스의 다른 단계에서 다시 패키지되는 컨텐츠 패키지, 즉 다른 패키지의 하위 패키지로 사용할 경우 유용합니다.

이러한 시나리오를 수용하기 위해 Cloud Manager는 내장 콘텐츠 패키지의 속성에서 ***cloudManagerTarget*** 이라는 속성을 찾습니다. 이 속성을 none으로 설정하면 패키지를 건너뛰고 배포할 수 없습니다. 이 속성을 설정하는 메커니즘은 빌드가 콘텐츠 패키지를 생성하는 방법에 따라 달라집니다. 예를 들어 filevault-maven-plugin을 사용하면 다음과 같이 플러그인을 구성할 수 있습니다.

```xml
        <plugin>
            <groupId>org.apache.jackrabbit</groupId>
            <artifactId>filevault-package-maven-plugin</artifactId>
            <extensions>true</extensions>
            <configuration>
                <properties>
                    <cloudManagerTarget>none</cloudManagerTarget>
                </properties>
        <!-- other configuration -->
            </configuration>
        </plugin>
```

content-package-maven-plugin은 다음과 유사합니다.

```xml
        <plugin>
            <groupId>com.day.jcr.vault</groupId>
            <artifactId>content-package-maven-plugin</artifactId>
            <extensions>true</extensions>
            <configuration>
                <properties>
                    <cloudManagerTarget>none</cloudManagerTarget>
                </properties>
        <!-- other configuration -->
            </configuration>
        </plugin>
```

## 모범 사례를 기반으로 코드 개발 {#develop-your-code-based-on-best-practices}

Adobe 엔지니어링 및 컨설팅 팀은 AEM 개발자를 위한 [포괄적인 우수 사례 세트를 개발했습니다](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/best-practices.html).
