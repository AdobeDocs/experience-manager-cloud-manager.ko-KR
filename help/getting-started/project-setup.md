---
title: 프로젝트 설정
description: Cloud Manager를 사용하여 프로젝트를 관리하고 배포할 수 있도록 프로젝트를 설정하는 방법에 대해 알아보십시오.
exl-id: ed994daf-0195-485a-a8b1-87796bc013fa
source-git-commit: f855fa91656e4b3806a617d61ea313a51fae13b4
workflow-type: tm+mt
source-wordcount: '1395'
ht-degree: 54%

---


# 프로젝트 설정 {#setting-up-your-project}

Cloud Manager를 사용하여 프로젝트를 관리하고 배포할 수 있도록 프로젝트를 설정하는 방법에 대해 알아보십시오.

## 기존 프로젝트 편집 {#modifying-project-setup-details}

기존 AEM 프로젝트는 Cloud Manager을 사용하여 성공적으로 빌드 및 배포할 수 있도록 몇 가지 기본 규칙을 준수해야 합니다.

* 프로젝트는 Apache Maven을 사용하여 빌드해야 합니다.
* git 저장소의 루트에 `pom.xml` 파일이 있어야 합니다.
   * 이 `pom.xml` 파일은 여러 하위 모듈을 참조할 수 있습니다(다른 하위 모듈 등이 있을 수 있음).
   * `pom.xml` 파일에 추가 Maven 아티팩트 저장소에 대한 참조를 추가할 수 있습니다.
   * 구성된 경우 [암호로 보호된 아티팩트 저장소](#password-protected-maven-repositories)에 대한 액세스가 지원됩니다. 그러나 네트워크로 보호된 아티팩트 저장소에 대한 액세스는 지원되지 않습니다.
* 배포 가능한 콘텐츠 패키지는 `target`이라는 디렉터리에 포함된 콘텐츠 패키지 .zip 파일에서 검색됩니다.
   * 여러 하위 모듈에서 콘텐츠 패키지를 생성할 수 있습니다.
* 배포 가능한 Dispatcher 아티팩트는 `conf` 및 `conf.d`라는 `target`의 하위 디렉터리가 포함된 `zip` 파일을 스캔하여 검색됩니다.
* 콘텐츠 패키지가 두 개 이상인 경우 패키지 배포 순서가 보장되지 않습니다.
* 특정 순서가 필요한 경우 콘텐츠 패키지 종속성을 사용하여 순서를 정의할 수 있습니다.
* 배포에서 패키지를 [건너뛸](#skipping-content-packages) 수 있습니다.

## Cloud Manager에서 Maven 프로필 활성화 {#activating-maven-profiles-in-cloud-manager}

일부 제한된 경우 Cloud Manager 내에서 실행할 때는 개발자 워크스테이션에서 실행할 때와 달리 빌드 프로세스를 약간 변경해야 할 수 있습니다. 이러한 경우 [Maven 프로필](https://maven.apache.org/guides/introduction/introduction-to-profiles.html)을 사용하여 Cloud Manager를 비롯한 다양한 환경에서 빌드가 어떻게 달라야 하는지 정의할 수 있습니다.

Cloud Manager 빌드 환경 내에서 Maven 프로필을 활성화하려면 `CM_BUILD` [환경 변수](/help/getting-started/build-environment.md#environment-variables)를 찾아야 합니다. 반대로 Cloud Manager 빌드 환경 외부에서만 사용하려는 프로필은 이 변수가 없는지 확인해야 합니다.

예를 들어 빌드가 Cloud Manager 내에서 실행될 때만 간단한 메시지를 출력하려는 경우 다음을 수행합니다.

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
>개발자 워크스테이션에서 이 프로필을 테스트하려면 명령줄(`-PcmBuild` 사용)이나 통합 개발 환경(IDE)에서 활성화할 수 있습니다.

빌드가 Cloud Manager 외부에서 실행될 때만 간단한 메시지를 출력하려는 경우 다음을 수행합니다.

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

암호로 보호된 Maven 저장소의 아티팩트는 이러한 방식으로 배포된 코드가 Cloud Manager의 품질 게이트에서 적용되는 품질 검사를 완전히 받지 않기 때문에 신중하게 사용해야 합니다. Adobe 또한 Java 소스 및 전체 프로젝트 소스 코드를 바이너리와 함께 배포하는 것이 좋습니다.

>[!TIP]
>
>암호로 보호된 Maven 저장소의 아티팩트는 AEM에 연결되지 않은 코드에만 드물게 사용해야 합니다.

Cloud Manager에서 암호로 보호된 Maven 저장소를 사용하려면 암호(및 사용자 이름)를 비밀 [파이프라인 변수](/help/getting-started/build-environment.md#pipeline-variables)(으)로 지정한 다음 git 저장소의 `.cloudmanager/maven/settings.xml` 파일 내에서 해당 암호를 참조합니다. 이 파일은 [Maven 설정 파일](https://maven.apache.org/settings.html) 스키마를 따릅니다.

Cloud Manager 빌드 프로세스가 시작되면 이 파일의 `<servers>` 요소가 Cloud Manager에서 제공하는 기본 `settings.xml` 파일에 병합됩니다. 사용자 지정 서버는 `adobe` 및 `cloud-manager`(으)로 시작하는 서버 ID를 사용하지 않아야 합니다. 이러한 ID는 예약된 것으로 간주됩니다. Cloud Manager은 지정된 접두사 중 하나 또는 기본 ID `central`과(와) 일치하는 서버 ID만 미러링합니다.

이 파일이 있는 경우 서버 ID는 `pom.xml` 파일 내의 `<repository>` 및/또는 `<pluginRepository>` 요소 내부에서 참조됩니다. 일반적으로 이러한 `<repository>` 및/또는 `<pluginRepository>` 요소는 [Cloud Manager별 프로필](#activating-maven-profiles-in-cloud-manager) 내에 포함되지만 반드시 필요한 것은 아닙니다.

예를 들어 저장소가 `https://repository.myco.com/maven2`에 있다고 가정할 때 Cloud Manager에서 사용해야 하는 사용자 이름은 `cloudmanager`이고 암호는 `secretword`입니다.

먼저, 파이프라인에서 암호를 비밀로 설정합니다.

```shell
$ aio cloudmanager:set-pipeline-variables PIPELINEID --secret CUSTOM_MYCO_REPOSITORY_PASSWORD secretword
```

`.cloudmanager/maven/settings.xml` 파일에서 다음을 참조합니다.

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

그리고 마지막으로 `pom.xml` 파일 내에서 서버 ID를 참조합니다.

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

Maven 저장소에 이진과 함께 Java 소스를 배포하는 것이 좋습니다.

프로젝트에서 `maven-source-plugin` 구성:

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

Maven 저장소에 이진과 함께 전체 프로젝트 소스를 배포하는 것이 좋습니다. 이렇게 하면 정확한 아티팩트를 다시 작성할 수 있습니다.

프로젝트에서 `maven-assembly-plugin` 구성:

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

## 콘텐츠 패키지 건너뛰기 {#skipping-content-packages}

Cloud Manager에서 빌드는 콘텐츠 패키지를 원하는 수만큼 생성할 수 있습니다. 여러 가지 이유로, 콘텐츠 패키지를 생성하지만 배포하지 않는 것이 바람직할 수 있습니다. 예를 들어 이 방법은 테스트용으로만 콘텐츠 패키지를 빌드하거나 빌드 프로세스의 다른 단계에서 다시 패키징할 때 유용할 수 있습니다. 즉, 다른 패키지의 하위 패키지로 사용됩니다.

이러한 시나리오를 수용하기 위해 Cloud Manager는 빌드된 콘텐츠 패키지의 속성에서 `cloudManagerTarget`이라는 속성을 찾습니다. 이 속성을 `none`(으)로 설정하면 패키지를 건너뛰고 배포되지 않습니다. 이 속성을 설정하는 메커니즘은 빌드가 콘텐츠 패키지를 생성하는 방식에 따라 다릅니다. 예를 들어 `filevault-maven-plugin`을(를) 사용하여 다음과 같이 플러그인을 구성합니다.

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

`content-package-maven-plugin`을(를) 사용하면 다음과 비슷합니다.

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

## 빌드 아티팩트 재사용 {#build-artifact-reuse}

많은 경우 동일한 코드가 여러 AEM 환경에 배포됩니다. 가능한 경우, Cloud Manager은 동일한 Git Commit이 여러 전체 스택 파이프라인 실행에 사용되는 것을 감지하면 코드 베이스를 다시 빌드하지 않습니다.

실행이 시작되면 분기 파이프라인에 대한 현재 HEAD 커밋이 추출됩니다. 커밋 해시는 UI에 API를 통해 볼 수 있습니다. 빌드 단계가 정상적으로 완료되면 결과 아티팩트가 해당 커밋 해시를 기반으로 저장되고 후속 파이프라인 실행에서 재사용될 수 있습니다.

동일한 프로그램에 있는 경우 파이프라인에서 패키지가 재사용됩니다. 재사용할 수 있는 패키지를 찾을 때 AEM은 분기를 무시하고 분기 간에 아티팩트를 재사용합니다.

재사용이 발생하면 빌드 및 코드 품질 단계가 원래 실행의 결과로 효과적으로 대체됩니다. 빌드 단계의 로그 파일에는 원래 빌드하는 데 사용된 아티팩트와 실행 정보가 나열됩니다.

다음은 이러한 로그 출력의 예입니다.

```shell
The following build artifacts were reused from the prior execution 4 of pipeline 1 which used commit f6ac5e6943ba8bce8804086241ba28bd94909aef:
build/aem-guides-wknd.all-2021.1216.1101633.0000884042.zip (content-package)
build/aem-guides-wknd.dispatcher.cloud-2021.1216.1101633.0000884042.zip (dispatcher-configuration)
```

코드 품질 단계의 로그에는 유사한 정보가 포함되어 있습니다.

### 예 {#example-reuse}

#### 예 1 {#example-1}

프로그램에 두 가지 개발 파이프라인이 있다고 가정해 보겠습니다.

* 분기 `foo`의 파이프라인 1
* 분기 `bar`의 파이프라인 2

두 분기는 동일한 커밋 ID에 있습니다.

1. 파이프라인 1을 실행하면 패키지가 정상적으로 빌드됩니다.
1. 그런 다음 파이프라인 2를 실행하면 파이프라인 1에서 만든 패키지가 재사용됩니다.

#### 예 2 {#example-2}

프로그램에 두 개의 분기, 즉 분기 `foo` 및 분기 `bar`이(가) 있다고 가정해 봅니다.

두 분기의 커밋 ID는 동일합니다.

1. 개발 파이프라인은 `foo`를 빌드하고 실행합니다.
1. 결과적으로 프로덕션 파이프라인은 `bar`을(를) 빌드하고 실행합니다.

이 경우 동일한 커밋 해시가 식별되었으므로 `foo`의 아티팩트가 프로덕션 파이프라인에 재사용됩니다.

### 옵트아웃 {#opting-out}

원하는 경우 파이프라인 변수 `CM_DISABLE_BUILD_REUSE`를 `true`로 설정하여 특정 파이프라인에 대해 재사용 비헤이비어를 비활성화할 수 있습니다. 이 변수가 설정되면 커밋 해시가 계속 추출됩니다. 결과 아티팩트는 나중에 사용하기 위해 저장되지만 이전에 저장된 아티팩트는 재사용되지 않습니다. 이 비헤이비어를 이해하려면 다음 시나리오를 고려하십시오.

1. 새 파이프라인이 생성됩니다.
1. 파이프라인이 실행되고(실행 #1) 현재 HEAD 커밋은 `becdddb`입니다. 실행이 성공하고 결과 아티팩트가 저장됩니다.
1. `CM_DISABLE_BUILD_REUSE` 변수가 설정됩니다.
1. 코드를 변경하지 않고 파이프라인이 다시 실행됩니다. `becdddb`와 관련된 저장된 아티팩트가 있지만 `CM_DISABLE_BUILD_REUSE` 변수로 인해 재사용되지 않습니다.
1. 코드가 변경되고 파이프라인이 실행됩니다. 이제 HEAD 커밋은 `f6ac5e6`입니다. 실행이 성공하고 결과 아티팩트가 저장됩니다.
1. `CM_DISABLE_BUILD_REUSE` 변수가 삭제됩니다.
1. 코드를 변경하지 않고 파이프라인이 다시 실행됩니다. `f6ac5e6`과(와) 관련된 저장된 아티팩트가 있으므로 해당 아티팩트가 재사용됩니다.

### 주의 사항 {#caveats}

* 빌드 아티팩트는 커밋 해시가 동일한지 여부에 관계없이 다른 프로그램에서 재사용되지 않습니다.
* 빌드 아티팩트는 분기 및/또는 파이프라인이 다른 경우에도 동일한 프로그램 내에서 재사용됩니다.
* [Maven 버전 처리](/help/managing-code/maven-project-version.md)는 프로덕션 파이프라인에서만 프로젝트 버전을 대체합니다. 개발 및 프로덕션 파이프라인 모두에 동일한 커밋이 사용되고 개발 파이프라인이 먼저 실행되는 경우 버전이 스테이징 및 프로덕션에 변경되지 않고 배포됩니다. 하지만 이 경우에도 태그가 생성됩니다.
* 저장된 아티팩트를 성공적으로 검색하지 못하면 아티팩트가 저장되지 않은 것처럼 빌드 단계가 실행됩니다.
* `CM_DISABLE_BUILD_REUSE` 이외의 파이프라인 변수는 Cloud Manager가 이전에 생성된 빌드 아티팩트를 재사용하기로 결정할 때 고려되지 않습니다.

## 모범 사례를 기반으로 코드 개발 {#develop-your-code-based-on-best-practices}

Adobe 엔지니어링 및 컨설팅 팀은 AEM 개발자를 위한 [포괄적인 모범 사례 세트](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/implementing/developing/bestpractices/best-practices)를 개발했습니다.
