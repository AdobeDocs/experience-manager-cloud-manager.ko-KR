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
source-git-commit: b39fc865e3c34052fb94b223d9eebc0fce3495d2

---


# Create an AEM Application Project {#create-an-aem-application-project}

## Using Wizard to Create an AEM Application Project {#using-wizard-to-create-an-aem-application-project}

고객이 클라우드 관리자에게 문의하면 빈 Git 리포지토리가 제공됩니다. 현재 Adobe 관리 서비스 (AMS) 고객 (AMS로 마이그레이션 중인 고객 또는 온프레미스 AEM 고객) 는 일반적으로 Git (또는 다른 버전 제어 시스템) 에 프로젝트 코드를 가지고 있으며 프로젝트를 클라우드 관리자 Git 리포지토리로 가져옵니다. 그러나 새 고객은 기존 프로젝트가 없습니다.

새로운 고객이 시작하는 데 도움이 되도록 이제 클라우드 관리자는 최소한의 AEM 프로젝트를 시작점으로 만들 수 있습니다. This process is based on the [**AEM Project Archetype**](https://github.com/Adobe-Marketing-Cloud/aem-project-archetype).

<!-- 

Comment Type: annotation
Last Modified By: jsyal
Last Modified Date: 2018-10-08T12:52:50.071-0400

2018.8.0: Added this new section

 -->

아래 절차에 따라 클라우드 관리자에서 AEM 애플리케이션 프로젝트를 만드십시오.

1. Once you log in to Cloud Manager and the basic program setup is complete, a special call to action card will be shown on the **Overview** screen, if the repository is empty.

   ![](assets/image2018-10-3_14-29-44.png)

1. **만들기를** 클릭하여 **파이프라인 설정** 화면으로 이동합니다.

   ![](assets/image2018-10-3_14-30-22.png)

1. Click **Create to** open a dialog box, which allows the user to provide the parameters required by the AEM Project Archetype. 기본 양식에서 대화 상자는 다음 두 가지 값을 요청합니다.

   * **제목** - 기본적으로 *프로그램 이름으로 설정됩니다.*

   * **새 분기 이름** - 기본적으로 *마스터*
   ![](assets/screen_shot_2018-10-08at55825am.png)

   대화 상자에는 대화 상자 아래쪽에 있는 핸들을 클릭하여 열 수 있는 서랍 이 있습니다. 대화 상자에는 확장된 형식의 Archetype에 대한 모든 구성 매개 변수가 표시됩니다. Many of these parameters have default values which are generated based on the **Title**.

   ![](assets/screen_shot_2018-10-08at60032am.png)

   >[!NOTE]
   >
   >For example, if the **Title** is ***We.Finance***, the Base Maven Artifact Id parameter is generated as ***com.wefinance***. 필요한 경우 이러한 값을 변경할 수 있습니다.
   >
   >
   >For example, you can change from the generated ***value com.wefinance*** to ***net.wefinance***.

1. Click **Create** in the preceding step to create the starter project by using the archetype and commit to the named git branch. 이 과정이 완료되면 파이프라인을 설정할 수 있습니다.

## Setting up your Project {#setting-up-your-project}

### Modifying Project Setup Details {#modifying-project-setup-details}

클라우드 관리자를 사용하여 성공적으로 구축 및 배포하려면 기존 AEM 프로젝트가 다음과 같은 일부 기본 규칙을 준수해야 합니다.

* 프로젝트는 Apache Maven를 사용하여 구축되어야 합니다.
* There must be a *pom.xml* file in the root of the Git repository. This *pom.xml* file can refer to as many submodules (which in turn may have other submodules, etc.) 필요한 경우

* *pom.xml* 파일에 추가 Maven 가공물 리포지토리에 대한 참조를 추가할 수 있습니다. 그러나 암호로 보호되거나 네트워크에 보호된 결함 리포지토리에 대한 액세스는 지원되지 않습니다.
* Deployable content packages are discovered by scanning for content package *zip* files which are contained in a directory named *target*. 원하는 수의 하위 모듈을 사용하여 컨텐츠 패키지를 생성할 수 있습니다.

* Deployable Dispatcher artifacts are discovered by scanning for *zip* files (again, contained in a directory named *target*) which have directories named *conf* and *conf.d*.

* 둘 이상의 컨텐츠 패키지가 있는 경우 패키지 배포 순서는 보장되지 않습니다. 특정 순서가 필요한 경우 컨텐츠 패키지 종속성을 사용하여 순서를 정의할 수 있습니다.

<!-- 

Comment Type: annotation
Last Modified By: jsyal
Last Modified Date: 2018-10-08T09:20:10.106-0400

2018.8.0: added existing in the opening sentence

 -->

## Build Environment Details {#build-environment-details}

Cloud Manager builds and tests your code using a specialized build runtime **Environment**. 이 환경에는 다음 속성이 있습니다.

* 빌드 환경은 Linux 기반입니다.
* Apache Maven 3.6.0 이 설치되어 있습니다.
* 설치된 Java 버전은 Oracle JDK 8 u 202 입니다.
* 다음과 같은 몇 가지 추가 시스템 패키지가 설치되어 있습니다.

   * bzip2
   * 압축을 풉니다.
   * libpng
   * Imagemagick
   * Graphicsmagick
   * 다른 패키지가 필요한 경우 Customer Success Engineer (CSE) 를 통해 요청해야 합니다.

* 모든 빌드는 본래 환경에서 수행됩니다. 빌드 컨테이너는 실행 사이에 어떠한 상태도 유지하지 않습니다.
* Maven is always run with the command: *mvn --batch-mode clean org.jacoco:jacoco-maven-plugin:prepare-agent package*
* Maven is configured at a system level with a settings.xml file which automatically includes the public Adobe **Artifact** repository. (Refer to [Adobe Public Maven Repository](https://repo.adobe.com/) for more details).

## Activating Maven Profiles in Cloud Manager {#activating-maven-profiles-in-cloud-manager}

일부 제한된 경우 개발자 워크스테이션에서 실행되는 경우와 반대로 클라우드 관리자를 실행할 때 빌드 프로세스를 약간 다르게 변경해야 할 수 있습니다. For these cases, [Maven Profiles](https://maven.apache.org/guides/introduction/introduction-to-profiles.html) can be used to define how the build should be different in different environments, including Cloud Manager.

Activation of a Maven Profile inside the Cloud Manager build environment should be done by looking for the presence of an environment variable named `CM_BUILD`. 이 변수는 항상 클라우드 관리자 빌드 환경에서 설정됩니다. Conversly, 클라우드 관리자 빌드 환경의 외부에서만 사용되도록 만들어진 프로필은 이 변수의 absense를 찾아서 수행해야 합니다.

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
>To test this profile on a developer workstation, you can either enable it on the command line (with `-PcmBuild`) or in your Integrated Development Environment (IDE).

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

## Develop your Code Based on Best Practices {#develop-your-code-based-on-best-practices}

Adobe Engineering and Consulting teams have developed a [comprehensive set of best practices for AEM developers](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/best-practices.html).
