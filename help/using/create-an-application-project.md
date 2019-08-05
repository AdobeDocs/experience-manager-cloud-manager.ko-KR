---
title: AEM 애플리케이션 프로젝트 만들기
seo-title: AEM 애플리케이션 프로젝트 만들기
description: 'null'
seo-description: 클라우드 관리자를 시작할 때 AEM 프로젝트를 설정하는 방법에 대한 자세한 내용은 이 페이지를 따르십시오.
uuid: 7 B 976 EBF -5358-49 D 8-A 58 D -0 BAE 026303 FA
contentOwner: Jsyal
products: sg_ Experiencemanager/Cloudmanager
topic-tags: Getting-Started
discoiquuid: 76 C 1 A 8 E 4-D 66 F -4 A 3 B -8 C 0 C-B 80 C 9 E 17700 E
translation-type: tm+mt
source-git-commit: 81f4e0b3b31a8be1f0620b70442b0268159e4ec0

---


# AEM 애플리케이션 프로젝트 만들기 {#create-an-aem-application-project}

## 마법사를 사용하여 AEM 애플리케이션 프로젝트 만들기 {#using-wizard-to-create-an-aem-application-project}

고객이 클라우드 관리자에게 문의하면 빈 Git 리포지토리가 제공됩니다. 현재 Adobe 관리 서비스 (AMS) 고객 (AMS로 마이그레이션 중인 고객 또는 온프레미스 AEM 고객) 는 일반적으로 Git (또는 다른 버전 제어 시스템) 에 프로젝트 코드를 가지고 있으며 프로젝트를 클라우드 관리자 Git 리포지토리로 가져옵니다. 그러나 새 고객은 기존 프로젝트가 없습니다.

새로운 고객이 시작하는 데 도움이 되도록 이제 클라우드 관리자는 최소한의 AEM 프로젝트를 시작점으로 만들 수 있습니다. 이 프로세스는 [**AEM Project Archetype**](https://github.com/Adobe-Marketing-Cloud/aem-project-archetype)를 기반으로 합니다.

<!-- 

Comment Type: annotation
Last Modified By: jsyal
Last Modified Date: 2018-10-08T12:52:50.071-0400

2018.8.0: Added this new section

 -->

아래 절차에 따라 클라우드 관리자에서 AEM 애플리케이션 프로젝트를 만드십시오.

1. 클라우드 관리자에 로그인하고 기본 프로그램 설정이 완료되면, 저장소가 비어 있는 경우 **개요** 화면에 특별 클릭 유도 카드가 표시됩니다.

   ![](assets/image2018-10-3_14-29-44.png)

1. **만들기를** 클릭하여 **파이프라인 설정** 화면으로 이동합니다.

   ![](assets/image2018-10-3_14-30-22.png)

1. 만들기를 클릭하여 **사용자가 AEM Project Archetype에 필요한 매개 변수를 제공할 수 있는 대화 상자를** 엽니다. 기본 양식에서 대화 상자는 다음 두 가지 값을 요청합니다.

   * **제목** - 기본적으로 *프로그램 이름으로 설정됩니다.*

   * **새 분기 이름** - 기본적으로 *마스터*
   ![](assets/screen_shot_2018-10-08at55825am.png)

   대화 상자에는 대화 상자 아래쪽에 있는 핸들을 클릭하여 열 수 있는 서랍 이 있습니다. 대화 상자에는 확장된 형식의 Archetype에 대한 모든 구성 매개 변수가 표시됩니다. 이러한 매개 변수에는 대부분 **제목을 기반으로 생성되는 기본값이 있습니다**.

   ![](assets/screen_shot_2018-10-08at60032am.png)

   >[!NOTE]
   >
   >예를 들어 **제목이** ***we. finance***&#x200B;인 경우 기본 maven artifact ID 매개 변수가 com. wefinance로 ***생성됩니다***. 필요한 경우 이러한 값을 변경할 수 있습니다.
   >
   >
   >예를 들어 생성된 com. wefinance ***값에서 net. wefinance*** 로 ***변경할***&#x200B;수 있습니다.

1. 이전 단계에서 **만들기를** 클릭하여 Archetype를 사용하여 시작 프로젝트를 만들고 지정된 Git 분기에 커밋합니다. 이 과정이 완료되면 파이프라인을 설정할 수 있습니다.

## 프로젝트 설정 {#setting-up-your-project}

### 프로젝트 설정 세부 사항 수정 {#modifying-project-setup-details}

클라우드 관리자를 사용하여 성공적으로 구축 및 배포하려면 기존 AEM 프로젝트가 다음과 같은 일부 기본 규칙을 준수해야 합니다.

* 프로젝트는 Apache Maven를 사용하여 구축되어야 합니다.
* Git 리포지토리의 루트에 *pom.xml* 파일이 있어야 합니다. 이 *pom.xml* 파일은 하위 모듈 (차례로 다른 하위 모듈 등) 를 참조할 수 있습니다. 필요한 경우

* *pom.xml* 파일에 추가 Maven 가공물 리포지토리에 대한 참조를 추가할 수 있습니다. 그러나 암호로 보호되거나 네트워크에 보호된 결함 리포지토리에 대한 액세스는 지원되지 않습니다.
* Target 이라는 디렉토리에 들어 있는 콘텐트 패키지 *zip* 파일을 스캔하여 배포 가능한 콘텐트 패키지를 *검색합니다*. 원하는 수의 하위 모듈을 사용하여 컨텐츠 패키지를 생성할 수 있습니다.

* conf 및 conf. d 라는 디렉토리가 있는 *zip* 파일을 스캔하면 배포 가능한 ** Dispatcher *가공물이* *검색됩니다*.

* 둘 이상의 컨텐츠 패키지가 있는 경우 패키지 배포 순서는 보장되지 않습니다. 특정 순서가 필요한 경우 컨텐츠 패키지 종속성을 사용하여 순서를 정의할 수 있습니다.

<!-- 

Comment Type: annotation
Last Modified By: jsyal
Last Modified Date: 2018-10-08T09:20:10.106-0400

2018.8.0: added existing in the opening sentence

 -->

## 환경 세부 사항 작성 {#build-environment-details}

클라우드 관리자는 전문 빌드 환경을 사용하여 코드를 작성하고 테스트합니다. 이 환경에는 다음 속성이 있습니다.

* 빌드 환경은 Ubuntu 18.04에서 파생된 Linux 기반입니다.
* Apache Maven 3.6.0 이 설치되어 있습니다.
* 설치된 Java 버전은 Oracle JDK 8 u 202 입니다.
* 다음과 같은 몇 가지 추가 시스템 패키지가 설치되어 있습니다.

   * bzip2
   * 압축을 풉니다.
   * libpng
   * Imagemagick
   * Graphicsmagick

* 아래에 설명된 [대로 다른 패키지를 빌드할 때 설치할](#installing-additional-system-packages)수 있습니다.
* 모든 빌드는 본래 환경에서 수행됩니다. 빌드 컨테이너는 실행 사이에 어떠한 상태도 유지하지 않습니다.
* maven는 항상 명령으로 실행됩니다. *MVN —Batch-Mode Clean Org. Jacoco: jaccoca-maven-plugin: Prepare-Agent Package*
* maven는 공개 Adobe **가공물** 저장소가 자동으로 포함되는 settings.xml 파일을 사용하여 시스템 수준에서 구성됩니다. (자세한 내용은 [Adobe 공개 Maven 리포지토리](https://repo.adobe.com/) 참조).

## 클라우드 관리자에서 Maven 프로필 활성화 {#activating-maven-profiles-in-cloud-manager}

일부 제한된 경우 개발자 워크스테이션에서 실행되는 경우와 반대로 클라우드 관리자를 실행할 때 빌드 프로세스를 약간 다르게 변경해야 할 수 있습니다. 이러한 경우 [, 클라우드 관리자를 포함하여, 빌드가 다른 환경에서 어떻게 달라지는지를 정의하는 데 Maven 프로필을](https://maven.apache.org/guides/introduction/introduction-to-profiles.html) 사용할 수 있습니다.

클라우드 관리자 빌드 환경에서 Maven 프로필을 활성화하려면 명명된 환경 변수가 있는지 확인해야 `CM_BUILD`합니다. 이 변수는 항상 클라우드 관리자 빌드 환경에서 설정됩니다. Conversly, 클라우드 관리자 빌드 환경의 외부에서만 사용되도록 만들어진 프로필은 이 변수의 absense를 찾아서 수행해야 합니다.

예를 들어, 클라우드 관리자에서 빌드가 실행되는 경우에만 간단한 메시지를 출력하려면 다음을 수행합니다.

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
>개발자 워크스테이션에서 이 프로필을 테스트하려면 명령줄 (포함 `-PcmBuild`) 또는 IDE (Integrated Development Environment) 에서 이 프로필을 활성화할 수 있습니다.

또한 클라우드 관리자 외부에서 빌드를 실행할 때만 간단한 메시지를 출력하려면 다음을 수행합니다.

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

## 사용자 지정 환경 변수

경우에 따라, 고객의 빌드 프로세스는 Git 리포지토리에 배치할 부적절한 특정 구성 변수에 따라 달라질 수 있습니다. Cloud Manager를 사용하면 고객 별로 CSE (Customer Success Engineer) 에서 이러한 변수를 구성할 수 있습니다. 이러한 변수는 안전한 저장소 위치에 저장되며 특정 고객에 대한 빌드 컨테이너에서만 볼 수 있습니다. 이 기능을 사용하려는 고객은 자신의 CSE에 연락하여 변수를 구성해야 합니다.

구성된 후에는 이러한 변수를 환경 변수로 사용할 수 있습니다. 이러한 속성을 maven 속성으로 사용하려면 위에서 설명한 것처럼 프로필 내에서 잠재적으로 pom.xml 파일에서 참조할 수 있습니다.

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
>
>환경 변수 이름에는 영숫자 및 밑줄 (_) 문자만 포함할 수 있습니다. 규칙별로, 이름은 모두 대문자로 구성되어야 합니다.

## 추가 시스템 패키지 설치 {#installing-additional-system-packages}

일부 빌드에서는 제대로 작동하도록 추가 시스템 패키지가 필요합니다. 예를 들어 빌드가 Python 또는 Ruby 스크립트를 호출하면 해당 언어 인터프리터가 설치되어 있어야 합니다. This can be done by call the [exec-maven-plugin](https://www.mojohaus.org/exec-maven-plugin/) to call apt. 이러한 작업은 일반적으로 클라우드 관리자 특정 Maven 프로파일에 래핑되어야 합니다. 예를 들어 Python를 설치하려면 다음을 수행하십시오.

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

이와 동일한 기술을 사용하여 언어 특정 패키지 (예: rubygems 또는 Python 패키지에 `gem` 사용) 를 `pip` 설치할 수 있습니다.

>[!NOTE]
>
>이 방법으로 시스템 패키지를 설치해도 Adobe Experience **Manager를 실행하는 데 사용되는 런타임 환경에서는** 이 패키지를 설치하지 않습니다. AEM 환경에 시스템 패키지가 설치되어 있으면 고객 성공 엔지니어 (CSE) 에 문의하십시오.

## 모범 사례를 기반으로 코드 개발 {#develop-your-code-based-on-best-practices}

Adobe 엔지니어링 및 컨설팅 팀은 AEM 개발자를 위한 [포괄적인 모범 사례를 개발했습니다](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/best-practices.html).
