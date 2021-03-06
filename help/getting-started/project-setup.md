---
title: 프로젝트 설정
description: Cloud Manager를 사용하여 관리하고 배포할 수 있도록 프로젝트를 설정하는 방법을 알아봅니다.
exl-id: ed994daf-0195-485a-a8b1-87796bc013fa
source-git-commit: 6572c16aea2c5d2d1032ca5b0f5d75ade65c3a19
workflow-type: tm+mt
source-wordcount: '1432'
ht-degree: 2%

---


# 프로젝트 설정 {#setting-up-your-project}

Cloud Manager를 사용하여 관리하고 배포할 수 있도록 프로젝트를 설정하는 방법을 알아봅니다.

## 기존 프로젝트 수정 {#modifying-project-setup-details}

Cloud Manager를 사용하여 성공적으로 빌드하고 배포하려면 기존 AEM 프로젝트가 몇 가지 기본 규칙을 준수해야 합니다.

* Apache Maven을 사용하여 프로젝트를 빌드해야 합니다.
* 다음 항목이 있어야 합니다. `pom.xml` git 저장소의 루트에 있는 파일입니다.
   * 이 `pom.xml` 파일은 필요에 따라 하위 모듈 수(다른 하위 모듈이 있을 수 있음)를 참조할 수 있습니다.
   * 에서 추가 Maven 객체 저장소에 대한 참조를 추가할 수 있습니다 `pom.xml` 파일.
   * 액세스 권한 [암호로 보호된 객체 저장소](#password-protected-maven-repositories) 는 구성 시 지원됩니다. 그러나 네트워크 보호 아티팩트 리포지토리에 대한 액세스는 지원되지 않습니다.
* 배포 가능한 컨텐츠 패키지는 이름이 지정된 디렉터리에 포함된 컨텐츠 패키지 .zip 파일을 검색하여 찾습니다 `target`.
   * 임의의 하위 모듈 개수로 컨텐츠 패키지를 생성할 수 있습니다.
* 배포 가능한 Dispatcher 가공물은 `zip` 파일에 하위 디렉토리에 포함됨 `target` 명명된 이름 `conf` 및 `conf.d`.
* 두 개 이상의 컨텐츠 패키지가 있는 경우 패키지 배포를 순서 지정할 수 없습니다.
* 특정 순서가 필요한 경우 컨텐츠 패키지 종속성을 사용하여 순서를 정의할 수 있습니다.
* 패키지는 [생략됨](#skipping-content-packages) 배포

## Cloud Manager에서 Maven 프로필 활성화 {#activating-maven-profiles-in-cloud-manager}

일부 제한된 경우에는 개발자 워크스테이션에서 실행되는 경우와 달리 Cloud Manager 내에서 실행할 때 빌드 프로세스를 약간 변경해야 할 수 있습니다. 이러한 경우 [Maven 프로필](https://maven.apache.org/guides/introduction/introduction-to-profiles.html) 는 Cloud Manager를 포함하여 다양한 환경에서 빌드가 어떻게 달라야 하는지를 정의하는 데 사용할 수 있습니다.

Cloud Manager 빌드 환경 내의 Maven 프로필 활성화는 `CM_BUILD` [환경 변수](/help/getting-started/build-environment.md#environment-variables) 환경 변수 입니다. 반대로 Cloud Manager 빌드 환경 외부에서만 사용하도록 만들어진 프로필은 이 변수가 없는 경우를 찾아 작성해야 합니다.

예를 들어 빌드가 Cloud Manager 내에서 실행될 때만 단순 메시지를 출력하려는 경우 다음을 수행합니다.

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
>개발자 워크스테이션에서 이 프로필을 테스트하려면 명령줄에서 을(를) 활성화하거나 `-PcmBuild`) 또는 IDE(Integrated Development Environment)에서 사용할 수 있습니다.

빌드가 Cloud Manager 외부에서 실행될 때만 간단한 메시지를 출력하려면 다음을 수행합니다.

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

## 암호로 보호된 Maven 저장소 지원 {#password-protected-maven-repositories}

암호로 보호된 Maven 저장소의 가공물은 이 메커니즘을 통해 배포된 코드가 Cloud Manager의 품질 게이트에 구현된 모든 품질 규칙을 통해 실행되지 않으므로 매우 신중하게 사용해야 합니다. Java 소스뿐만 아니라 전체 프로젝트 소스 코드도 바이너리와 함께 배포하는 것이 좋습니다.

>[!TIP]
>
>암호로 보호된 Maven 리포지토리의 아티팩트는 드문 경우이며 AEM에 연결되지 않은 코드에만 사용해야 합니다.

Cloud Manager에서 암호로 보호된 Maven 저장소를 사용하려면 암호(및 선택적으로 사용자 이름)를 암호로 지정합니다 [파이프라인 변수](/help/getting-started/build-environment.md#pipeline-variables) 그런 다음 파일 내에서 해당 암호를 참조합니다. `.cloudmanager/maven/settings.xml` git 리포지토리에서 생성합니다. 이 파일은 [Maven 설정 파일](https://maven.apache.org/settings.html) 스키마.

Cloud Manager 빌드 프로세스가 시작되면 `<servers>` 이 파일의 요소는 기본 `settings.xml` Cloud Manager에서 제공하는 파일입니다. 서버 ID 시작 `adobe` 및 `cloud-manager` 는 예약된 것으로 간주되므로 사용자 지정 서버에서 사용해서는 안 됩니다. 서버 ID가 이러한 접두사 또는 기본 ID 중 하나와 일치하지 않습니다 `central` 는 Cloud Manager에서 미러링되지 않습니다.

이 파일이 준비되면 서버 ID가 `<repository>` 및/또는 `<pluginRepository>` 내부 요소 `pom.xml` 파일. 일반적으로 다음과 같습니다 `<repository>` 및/또는 `<pluginRepository>` 요소는 [Cloud Manager별 프로필](#activating-maven-profiles-in-cloud-manager)하지만, 이것은 엄격히 필요한 것은 아닙니다.

예를 들어, 저장소가 `https://repository.myco.com/maven2`를 설정하는 경우 Cloud Manager에서 사용해야 하는 사용자 이름은 다음과 같습니다. `cloudmanager` 그리고 암호는 `secretword`.

먼저 파이프라인에서 암호를 암호로 설정합니다.

```shell
$ aio cloudmanager:set-pipeline-variables PIPELINEID --secret CUSTOM_MYCO_REPOSITORY_PASSWORD secretword
```

그런 다음 `.cloudmanager/maven/settings.xml` 파일:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<settings xmlns="http://maven.apache.org/SETTINGS/1.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
        xsi:schemaLocation="http://maven.apache.org/SETTINGS/1.0.0 http://maven.apache.org/xsd/settings-1.0.0.xsd">
    <servers>
        <server>
            <id>myco-repository</id>
            <username>cloudmanager</username>
            <password>${env.CUSTOM_MYCO_REPOSITORY_PASSWORD}</password>
        </server>
    </servers>
</settings>
```

그리고 마지막으로 `pom.xml` 파일:

```xml
<profiles>
    <profile>
        <id>cmBuild</id>
        <activation>
                <property>
                    <name>env.CM_BUILD</name>
                </property>
        </activation>
        <build>
            <repositories>
                <repository>
                    <id>myco-repository</id>
                    <name>MyCo Releases</name>
                    <url>https://repository.myco.com/maven2</url>
                    <snapshots>
                        <enabled>false</enabled>
                    </snapshots>
                    <releases>
                        <enabled>true</enabled>
                    </releases>
                </repository>
            </repositories>
            <pluginRepositories>
                <pluginRepository>
                    <id>myco-repository</id>
                    <name>MyCo Releases</name>
                    <url>https://repository.myco.com/maven2</url>
                    <snapshots>
                        <enabled>false</enabled>
                    </snapshots>
                    <releases>
                        <enabled>true</enabled>
                    </releases>
                </pluginRepository>
            </pluginRepositories>
        </build>
    </profile>
</profiles>
```

### 소스 배포 {#deploying-sources}

바이너리와 함께 Java 소스를 Maven 저장소에 배포하는 것이 좋습니다.

구성 `maven-source-plugin` 프로젝트에서 다음을 수행하십시오.

```xml
        <plugin>
            <groupId>org.apache.maven.plugins</groupId>
            <artifactId>maven-source-plugin</artifactId>
            <executions>
                <execution>
                    <id>attach-sources</id>
                    <goals>
                        <goal>jar-no-fork</goal>
                    </goals>
                </execution>
            </executions>
        </plugin>
```

### 프로젝트 소스 배포 {#deploying-project-sources}

바이너리와 함께 전체 프로젝트 소스를 Maven 저장소에 배포하는 것이 좋습니다. 이를 통해 정확한 아티팩트를 다시 작성할 수 있습니다.

구성 `maven-assembly-plugin` 프로젝트에서 다음을 수행하십시오.

```xml
        <plugin>
            <groupId>org.apache.maven.plugins</groupId>
            <artifactId>maven-assembly-plugin</artifactId>
            <executions>
                <execution>
                    <id>project-assembly</id>
                    <phase>package</phase>
                    <goals>
                        <goal>single</goal>
                    </goals>
                    <configuration>
                        <descriptorRefs>
                            <descriptorRef>project</descriptorRef>
                        </descriptorRefs>
                    </configuration>
                </execution>
            </executions>
        </plugin>
```

## 컨텐츠 패키지 건너뛰기 {#skipping-content-packages}

Cloud Manager에서 빌드는 다양한 컨텐츠 패키지를 생성할 수 있습니다. 다양한 이유로 컨텐츠 패키지를 개발하지만 배포하지는 않는 것이 좋을 수 있습니다. 예를 들어 테스트에만 사용하거나 빌드 프로세스의 다른 단계에서 다시 패키징하는 컨텐츠 패키지를 만들 때, 즉 다른 패키지의 하위 패키지로 사용할 수 있습니다.

To accommodate these scenarios, Cloud Manager will look for a property named `cloudManagerTarget` in the properties of built content packages. 이 속성이 `none`를 지정하면 패키지를 건너뛰고 배포하지 않습니다. The mechanism to set this property depends upon the way the build is producing the content package. 예를 들어, `filevault-maven-plugin` 다음과 같이 플러그인을 구성합니다.

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

사용 `content-package-maven-plugin` 비슷함:

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

## 객체 재사용 작성 {#build-artifact-reuse}

대부분의 경우 동일한 코드가 여러 AEM 환경에 배포됩니다. 가능한 경우 Cloud Manager는 동일한 Git 커밋이 여러 전체 스택 파이프라인 실행에서 사용됨을 감지하면 코드 기반 재구축을 방지할 수 있습니다.

실행이 시작되면 분기 파이프라인에 대한 현재 HEAD 커밋이 추출됩니다. 커밋 해시는 UI 및 API를 통해 표시됩니다. 빌드 단계가 성공적으로 완료되면 결과 가공물들은 해당 커밋 해시를 기반으로 저장되고 후속 파이프라인 실행에서 재사용될 수 있습니다.

패키지는 동일한 프로그램에 있는 경우 파이프라인 간에 재사용됩니다. 다시 사용할 수 있는 패키지를 찾을 때 AEM은 분기를 삭제하고 여러 분기 간에 아티팩트를 다시 사용합니다.

재사용이 발생하면 빌드 및 코드 품질 단계가 원래 실행의 결과로 효과적으로 대체됩니다. 빌드 단계에 대한 로그 파일에는 아티팩트와 원래 이 객체를 작성하는 데 사용된 실행 정보가 나열됩니다.

다음은 이러한 로그 출력의 예입니다.

```shell
The following build artifacts were reused from the prior execution 4 of pipeline 1 which used commit f6ac5e6943ba8bce8804086241ba28bd94909aef:
build/aem-guides-wknd.all-2021.1216.1101633.0000884042.zip (content-package)
build/aem-guides-wknd.dispatcher.cloud-2021.1216.1101633.0000884042.zip (dispatcher-configuration)
```

코드 품질 단계 로그에는 유사한 정보가 포함됩니다.

### 예 {#example-reuse}

#### 예제 1 {#example-1}

프로그램에는 두 개의 개발 파이프라인이 있습니다.

* 분기의 파이프라인 1 `foo`
* 분기의 파이프라인 2 `bar`

두 분기 모두 동일한 커밋 ID에 있습니다.

1. 먼저 파이프라인 1을 실행하면 패키지가 정상적으로 생성됩니다.
1. 그런 다음 파이프라인 2를 실행하면 파이프라인 1에 의해 생성된 패키지를 다시 사용하게 됩니다.

#### 예제 2 {#example-2}

프로그램에는 두 개의 분기가 있습니다.

* 분기 `foo`
* 분기 `bar`

두 분기 모두 커밋 ID가 동일합니다.

1. 개발 파이프라인이 빌드 및 실행됩니다 `foo`.
1. 그런 다음 프로덕션 파이프라인이 빌드 및 실행됩니다 `bar`.

이 경우 `foo` 동일한 커밋 해시가 식별되었으므로 이 프로덕션 파이프라인에 다시 사용됩니다.

### 옵트아웃 {#opting-out}

원할 경우 파이프라인 변수를 설정하여 특정 파이프라인에 대해 재사용 동작을 비활성화할 수 있습니다 `CM_DISABLE_BUILD_REUSE` to `true`. 이 변수를 설정하면 커밋 해시가 여전히 추출되며 결과 아티팩트는 나중에 사용할 수 있도록 저장되지만 이전에 저장된 아티팩트는 다시 사용되지 않습니다. 이 동작을 이해하려면 다음 시나리오를 고려하십시오.

1. 새 파이프라인이 생성됩니다.
1. 파이프라인이 실행되며(실행 #1) 현재 HEAD 커밋은 `becdddb`. 실행이 성공적이며 결과 가공물이 저장됩니다.
1. 다음 `CM_DISABLE_BUILD_REUSE` 변수가 설정되어 있습니다.
1. 파이프라인이 코드를 변경하지 않고 다시 실행됩니다. 에 연결된 저장 가공물만 있지만 `becdddb`으로 인해 다시 사용되지 않습니다 `CM_DISABLE_BUILD_REUSE` 변수를 채우는 방법을 설명합니다.
1. 코드가 변경되고 파이프라인이 실행됩니다. 이제 HEAD 커밋 `f6ac5e6`. 실행이 성공적이며 결과 가공물이 저장됩니다.
1. 다음 `CM_DISABLE_BUILD_REUSE` 변수가 삭제됩니다.
1. 파이프라인은 코드를 변경하지 않고 재실행됩니다. 연결된 저장 가공물이므로 `f6ac5e6`와 같은 가공물들은 재사용됩니다.

### 경고 {#caveats}

* 커밋 해시가 동일한지 여부에 관계없이 빌드 아티팩트는 다른 프로그램에서 다시 사용되지 않습니다.
* 빌드 객체는 분기 및/또는 파이프라인이 다른 경우에도 동일한 프로그램 내에서 재사용됩니다.
* [Maven 버전 처리](/help/managing-code/maven-project-version.md) 프로덕션 파이프라인에서만 프로젝트 버전을 대체합니다. 따라서 개발 배포 실행과 프로덕션 파이프라인 실행 둘 다에서 동일한 커밋을 사용하고 개발 배포 파이프라인이 먼저 실행되는 경우 버전은 변경되지 않고 스테이지와 프로덕션에 배포됩니다. 그러나 이 경우에도 태그가 생성됩니다.
* 저장된 아티팩트를 검색하지 못하면 아티팩트가 저장되지 않은 것처럼 빌드 단계가 실행됩니다.
* 다음 이외의 파이프라인 변수 `CM_DISABLE_BUILD_REUSE` Cloud Manager가 이전에 만든 빌드 아티팩트를 다시 사용하기로 결정한 경우에는 고려되지 않습니다.

## 우수 사례를 기반으로 코드 개발 {#develop-your-code-based-on-best-practices}

Adobe 엔지니어링 및 컨설팅 팀이 [AEM 개발자를 위한 포괄적인 모범 사례 세트.](https://experienceleague.adobe.com/docs/experience-manager-65/developing/bestpractices/best-practices.html)
