---
title: Dispatcher 구성
description: Cloud Manager를 사용하여 Dispatcher 구성 파일을 배포하는 방법을 알아봅니다.
exl-id: ffc2b60e-bde7-48ca-b268-dea0f8fd4e30
source-git-commit: 6572c16aea2c5d2d1032ca5b0f5d75ade65c3a19
workflow-type: tm+mt
source-wordcount: '582'
ht-degree: 0%

---


# Dispatcher 구성 {#manage-your-dispatcher-configurations}

Cloud Manager를 사용하여 Dispatcher 구성 파일을 배포하는 방법을 알아봅니다

## Cloud Manager를 사용하여 Dispatcher 구성 배포 {#deploying-dispatcher-configurations}

Cloud Manager는 웹 서버 및 Dispatcher 구성 파일이 일반적인 AEM 컨텐츠 패키지와 함께 git 리포지토리에 저장된다고 가정할 때 배포할 수 있습니다.

이 기능을 활용하려면 Maven 빌드가 두 개 이상의 디렉터리를 포함하는 .zip 파일을 생성해야 합니다. `conf` 및 `conf.d`. 이 .zip 파일은 `maven-assembly-plugin`.

기본 제공 기능을 사용하여 Cloud Manager에서 생성한 프로젝트 [프로젝트 만들기 마법사](/help/getting-started/using-the-wizard.md) 자동으로 올바른 Maven 프로젝트 구조를 만듭니다. AMS(Adobe Managed Services)를 처음 사용하는 경우 권장되는 경로입니다.

Dispatcher 인스턴스에 배포하면 Dispatcher 인스턴스에 있는 이러한 디렉토리의 컨텐츠가 Git 리포지토리에 있는 디렉토리에 의해 덮어쓰여집니다. 웹 서버 및 Dispatcher 구성 파일은 이 기능을 올바르게 사용하려면 환경별 정보가 자주 필요하므로 먼저 CSE(Customer Success Engineers)와 협력하여 이러한 환경 변수를 `/etc/sysconfig/httpd`.

## 기존 Managed Service 고객을 위한 Dispatcher 구성 {#steps-for-configuring-dispatcher}

아래 절차에 따라 초기 Dispatcher 구성을 완료하십시오.

1. CSE에서 현재 프로덕션 구성 파일을 가져옵니다.
1. 게시 렌더러 IP 와 같이 하드 코딩된 환경별 데이터를 제거하고 변수로 바꿉니다.
1. 각 target Dispatcher에 대한 키-값 쌍에서 필수 변수를 정의하고 CSE에 추가하도록 요청합니다 `/etc/sysconfig/httpd` 참조하십시오.
1. 스테이징 환경에서 업데이트된 구성을 테스트합니다.
1. 테스트되면 CSE에서 프로덕션에 배포하도록 요청합니다.
1. 파일을 Git 리포지토리에 커밋합니다.
1. Cloud Manager를 통해 배포합니다.

>[!NOTE]
>
>Dispatcher 및 웹 서버 구성을 Git 리포지토리로 마이그레이션하는 작업은 Cloud Manager 온보딩 중에 수행할 수 있지만 나중에 수행할 수도 있습니다.

### 예 {#example}

특정 파일 및 디렉토리 구조는 프로젝트의 특성에 따라 다를 수 있지만, 이 예에서는 Apache 및 Dispatcher 구성을 포함하도록 프로젝트를 구성하는 방법에 대한 구체적인 안내서를 제공해야 합니다.

1. 이름이 인 하위 디렉토리를 만듭니다. `dispatcher`.

   여기에서 이름을 사용할 수 있지만 이 단계에서 생성된 디렉토리 이름은 6단계에서 사용한 이름과 동일해야 합니다.

1. 이 하위 디렉토리에는 Maven 어셈블리 플러그인을 사용하여 Dispatcher .zip 파일을 빌드하는 Maven 모듈이 포함됩니다. 이를 시작하려면 다음을 수행하십시오. `dispatcher` 디렉토리, 생성 `pom.xml` 이 내용이 있는 파일, 변경 `parent` 참조, `artifactId`, 및 `name` 필요한 경우.

   ```xml
   <?xml version="1.0" encoding="UTF-8"?>
   <project xmlns="http://maven.apache.org/POM/4.0.0"
            xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
           xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/maven-v4_0_0.xsd">
       <modelVersion>4.0.0</modelVersion>
       <parent>
           <!-- reference to your parent pom -->
       </parent>
   
       <artifactId>dispatcher</artifactId> <!-- feel free to change this -->
       <packaging>pom</packaging>
       <name>dispatcher</name> <!-- feel free to change this -->
   
       <build>
           <plugins>
               <plugin>
                   <groupId>org.apache.maven.plugins</groupId>
                   <artifactId>maven-assembly-plugin</artifactId>
                   <version>3.1.0</version>
                   <executions>
                       <execution>
                           <phase>package</phase>
                           <goals><goal>single</goal></goals>
                           <configuration>
                               <descriptors>
                                   <descriptor>assembly.xml</descriptor>
                               </descriptors>
                               <appendAssemblyId>false</appendAssemblyId>
                           </configuration>
                       </execution>
                   </executions>
               </plugin>
           </plugins>
       </build>
   </project>
   ```

   * 1단계와 마찬가지로 artifactId 및 이름은 필요한 경우 다른 값이 될 수 있습니다. `dispatcher` 는 여기에서 한 가지 예를 사용할 수 있습니다.

1. Maven 어셈블리 플러그인에는 다음이 필요합니다. `descriptor` .zip 파일을 만드는 방법을 정의하려면 이 설명자를 생성하려면 `dispatcher` 하위 이름 `assembly.xml` 다음 컨텐츠로 변경 이 파일 이름은 `pom.xml` 위의 파일.

   ```xml
   <assembly xmlns="http://maven.apache.org/ASSEMBLY/2.0.0"
       xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
       xsi:schemaLocation="http://maven.apache.org/ASSEMBLY/2.0.0 http://maven.apache.org/xsd/assembly-2.0.0.xsd">
     <id>distribution</id>
     <formats>
       <format>zip</format>
     </formats>
     <includeBaseDirectory>false</includeBaseDirectory>
     <fileSets>
       <fileSet>
         <directory>${basedir}/src</directory>
         <includes>
           <include>**/*</include>
         </includes>
         <outputDirectory></outputDirectory>
       </fileSet>
     </fileSets>
   </assembly>
   ```

1. 이름이 인 하위 디렉토리를 만듭니다. `src` (11행에서 위의 어셈블리 설명자에서 참조) dispatcher 하위 디렉토리 내에 실제 Apache 및 Dispatcher 구성을 저장합니다. 이 내 `src` 디렉토리, 이름이 지정된 디렉토리 만들기 `conf`, `conf.d`, `conf.dispatcher.d`, 및 `conf.modules.d`.

1. 을(를) 채우기 `conf`, `conf.d`, `conf.dispatcher.d`, 및 `conf.modules.d` 구성 파일이 있는 디렉토리. 예를 들어, 기본 구성은 이러한 파일과 심볼 링크로 구성됩니다.

   ```
   dispatcher
   ├── assembly.xml
   ├── pom.xml
   └── src
       ├── conf
       │  ├── httpd.conf
       │  └── magic
       ├── conf.d
       │  ├── README
       │  ├── autoindex.conf
       │  ├── available_vhosts
       │  │  ├── aem_author.vhost
       │  │  ├── aem_flush.vhost
       │  │  ├── aem_health.vhost
       │  │  ├── aem_lc.vhost
       │  │  └── aem_publish.vhost
       │  ├── dispatcher_vhost.conf
       │  ├── enabled_vhosts
       │  │  ├── aem_author.vhost -> ../available_vhosts/aem_author.vhost
       │  │  ├── aem_flush.vhost -> ../available_vhosts/aem_flush.vhost
       │  │  └── aem_publish.vhost -> ../available_vhosts/aem_publish.vhost
       │  ├── rewrites
       │  │  ├── base_rewrite.rules
       │  │  └── xforwarded_forcessl_rewrite.rules
       │  ├── userdir.conf
       │  ├── variables
       │  │  └── ams_default.vars
       │  ├── welcome.conf
       │  └── whitelists
       │      └── 000_base_whitelist.rules
       ├── conf.dispatcher.d
       │  ├── available_farms
       │  │  ├── 000_ams_author_farm.any
       │  │  ├── 001_ams_lc_farm.any
       │  │  └── 999_ams_publish_farm.any
       │  ├── cache
       │  │  ├── ams_author_cache.any
       │  │  ├── ams_author_invalidate_allowed.any
       │  │  ├── ams_publish_cache.any
       │  │  └── ams_publish_invalidate_allowed.any
       │  ├── clientheaders
       │  │  ├── ams_author_clientheaders.any
       │  │  ├── ams_common_clientheaders.any
       │  │  ├── ams_lc_clientheaders.any
       │  │  └── ams_publish_clientheaders.any
       │  ├── dispatcher.any
       │  ├── enabled_farms
       │  │  ├── 000_ams_author_farm.any -> ../available_farms/000_ams_author_farm.any
       │  │  └── 999_ams_publish_farm.any -> ../available_farms/999_ams_publish_farm.any
       │  ├── filters
       │  │  ├── ams_author_filters.any
       │  │  ├── ams_lc_filters.any
       │  │  └── ams_publish_filters.any
       │  ├── renders
       │  │  ├── ams_author_renders.any
       │  │  ├── ams_lc_renders.any
       │  │  └── ams_publish_renders.any
       │  └── vhosts
       │      ├── ams_author_vhosts.any
       │      ├── ams_lc_vhosts.any
       │      └── ams_publish_vhosts.any
       └── conf.modules.d
           ├── 00-base.conf
           ├── 00-dav.conf
           ├── 00-lua.conf
           ├── 00-mpm.conf
           ├── 00-proxy.conf
           ├── 00-systemd.conf
           ├── 01-cgi.conf
           └── 02-dispatcher.conf
   ```

1. 마지막으로, `pom.xml` 프로젝트의 루트에 있는 파일에서 `<module>` dispatcher 모듈을 포함할 요소입니다.

   예를 들어, 기존 모듈 목록이

   ```xml
       <modules>
           <module>core</module>
           <module>ui.apps</module>
           <module>ui.content</module>
       </modules>
   ```

   다음으로 변경해야 합니다.

   ```xml
       <modules>
           <module>core</module>
           <module>ui.apps</module>
           <module>ui.content</module>
           <module>dispatcher</module>
       </modules>
   ```

   * 1단계에서 언급한 대로 `<module>` 요소는 생성된 디렉토리 이름과 일치해야 합니다.

1. 테스트하려면 다음을 실행하십시오 `mvn clean package` 프로젝트 루트 디렉토리에서 다음 작업을 수행합니다. 출력에는 다음과 같은 선이 표시됩니다.

   ```
   [INFO] --- maven-assembly-plugin:3.1.0:single (default) @ dispatcher ---
   [INFO] Reading assembly descriptor: assembly.xml
   [INFO] Building zip: /Users/me/mycompany/dispatcher/target/dispatcher-1.0-SNAPSHOT.zip
   ```

   이 파일의 압축을 풀어 내용을 볼 수도 있습니다.

   ```shell
   $ unzip -l dispatcher/target/dispatcher-1.0-SNAPSHOT.zip
   Archive:  dispatcher/target/dispatcher-1.0-SNAPSHOT.zip
     Length      Date    Time    Name
   ---------  ---------- -----   ----
           0  09-12-2018 12:53   conf.modules.d/
           0  10-19-2018 10:38   conf.dispatcher.d/
           0  09-12-2018 12:53   conf.dispatcher.d/available_farms/
           0  09-12-2018 12:53   conf.dispatcher.d/filters/
           0  09-12-2018 12:53   conf.dispatcher.d/renders/
           0  09-12-2018 12:53   conf.dispatcher.d/cache/
           0  09-12-2018 12:53   conf.dispatcher.d/clientheaders/
           0  09-12-2018 12:53   conf.dispatcher.d/enabled_farms/
           0  09-12-2018 12:53   conf.dispatcher.d/vhosts/
           0  09-12-2018 12:53   conf.d/
           0  09-12-2018 12:53   conf.d/rewrites/
           0  09-12-2018 12:53   conf.d/whitelists/
           0  09-12-2018 12:53   conf.d/variables/
           0  11-01-2018 13:53   conf.d/enabled_vhosts/
           0  09-12-2018 12:53   conf.d/available_vhosts/
           0  09-12-2018 12:53   conf/
          88  09-12-2018 12:53   conf.modules.d/00-systemd.conf
        4913  09-12-2018 12:53   conf.dispatcher.d/available_farms/999_ams_publish_farm.any
         152  09-12-2018 12:53   conf.dispatcher.d/renders/ams_lc_renders.any
         490  09-12-2018 12:53   conf.dispatcher.d/clientheaders/ams_common_clientheaders.any
        1727  09-12-2018 12:53   conf.d/rewrites/base_rewrite.rules
          36  09-12-2018 12:53   conf.d/enabled_vhosts/aem_author.vhost
       11753  09-12-2018 12:53   conf/httpd.conf
         957  09-12-2018 12:53   conf.modules.d/00-proxy.conf
         944  09-12-2018 12:53   conf.dispatcher.d/available_farms/001_ams_lc_farm.any
         220  09-12-2018 12:53   conf.dispatcher.d/cache/ams_author_invalidate_allowed.any
          43  09-12-2018 12:53   conf.dispatcher.d/enabled_farms/999_ams_publish_farm.any
         516  09-12-2018 12:53   conf.d/welcome.conf
          37  09-12-2018 12:53   conf.d/enabled_vhosts/aem_publish.vhost
       13077  09-12-2018 12:53   conf/magic
          96  09-12-2018 12:53   conf.modules.d/02-dispatcher.conf
        2601  09-12-2018 12:53   conf.dispatcher.d/available_farms/000_ams_author_farm.any
         837  09-12-2018 12:53   conf.dispatcher.d/cache/ams_author_cache.any
          42  09-12-2018 12:53   conf.dispatcher.d/enabled_farms/000_ams_author_farm.any
        2926  09-12-2018 12:53   conf.d/autoindex.conf
        2555  09-12-2018 12:53   conf.d/available_vhosts/aem_lc.vhost
          41  09-12-2018 12:53   conf.modules.d/00-lua.conf
        2234  09-12-2018 12:53   conf.dispatcher.d/filters/ams_publish_filters.any
         220  09-12-2018 12:53   conf.dispatcher.d/cache/ams_publish_invalidate_allowed.any
         402  09-12-2018 12:53   conf.dispatcher.d/dispatcher.any
         573  09-12-2018 12:53   conf.d/whitelists/000_base_whitelist.rules
         871  09-12-2018 12:53   conf.d/available_vhosts/aem_flush.vhost
         139  09-12-2018 12:53   conf.modules.d/00-dav.conf
         742  09-12-2018 12:53   conf.dispatcher.d/filters/ams_author_filters.any
         557  09-12-2018 12:53   conf.dispatcher.d/cache/ams_publish_cache.any
         105  09-12-2018 12:53   conf.dispatcher.d/vhosts/ams_lc_vhosts.any
         101  09-12-2018 12:53   conf.dispatcher.d/vhosts/ams_publish_vhosts.any
        3582  09-12-2018 12:53   conf.d/dispatcher_vhost.conf
        2529  09-12-2018 12:53   conf.d/available_vhosts/aem_publish.vhost
         742  09-12-2018 12:53   conf.modules.d/00-mpm.conf
          88  09-12-2018 12:53   conf.dispatcher.d/filters/ams_lc_filters.any
         177  09-12-2018 12:53   conf.dispatcher.d/clientheaders/ams_lc_clientheaders.any
         366  09-12-2018 12:53   conf.d/README
        2723  09-12-2018 12:53   conf.d/available_vhosts/aem_author.vhost
        3739  09-12-2018 12:53   conf.modules.d/00-base.conf
         138  09-12-2018 12:53   conf.dispatcher.d/renders/ams_author_renders.any
          44  09-12-2018 12:53   conf.dispatcher.d/clientheaders/ams_publish_clientheaders.any
         112  09-12-2018 12:53   conf.dispatcher.d/vhosts/ams_author_vhosts.any
         580  09-12-2018 12:53   conf.d/variables/ams_default.vars
          35  09-12-2018 12:53   conf.d/enabled_vhosts/aem_flush.vhost
        1252  09-12-2018 12:53   conf.d/userdir.conf
         451  09-12-2018 12:53   conf.modules.d/01-cgi.conf
         321  09-12-2018 12:53   conf.dispatcher.d/renders/ams_publish_renders.any
         170  09-12-2018 12:53   conf.dispatcher.d/clientheaders/ams_author_clientheaders.any
         220  09-12-2018 12:53   conf.d/rewrites/xforwarded_forcessl_rewrite.rules
        1753  09-12-2018 12:53   conf.d/available_vhosts/aem_health.vhost
   ---------                     -------
       69017                     66 files
   ```
