---
title: 클라우드 관리자를 위한 일반 구성 설정
seo-title: Adobe AEM 클라우드 관리자를 위한 일반 구성 설정
description: 클라우드 관리자를 설정하고 사용자 인터페이스에서 컨텐츠를 관리하기 위한 전제 조건입니다.
seo-description: Adobe AEM 클라우드 관리자를 설정하고 사용자 인터페이스에서 컨텐츠를 관리하기 위한 전제 조건입니다.
uuid: 65 d 795 F 9-AA 97-4816-B 66 B -03 B 5 AE 961 F 47
contentOwner: Jsyal
discoiquuid: 03241 b 88-8 d 28-401 b-aa 42-17 ead 6183 cd 8
translation-type: tm+mt
source-git-commit: 1dfb065c09569f811e5a006d3d74825d3bd7cc8d

---


# 일반 구성 설정 [!UICONTROL Cloud Manager]{#setting-up-general-configurations-for-cloud-manager}

다음 섹션에서는 사용자 인터페이스에서 컨텐츠를 [!UICONTROL Cloud Manager] 설정하고 관리하기 위한 전제 조건을 집중적으로 설명합니다.

이 섹션 페이지에서는 다음 주제를 다룹니다.

* **사용자 및 역할 설정**
* **AEM 애플리케이션 프로젝트 설정**
* **Dispatcher Configurations**
* **개발 모범 사례**

다음 다이어그램은 최상의 품질을 지속적으로 제공할 수 [!UICONTROL Cloud Manager] 있는 다양한 기능을 보여줍니다.

![](assets/screen_shot_2018-05-01at81926pm.png)

## 사용자 및 역할 설정 {#setting-up-users-and-roles}

역할은 Adobe Admin [!UICONTROL Cloud Manager] Console에서 관리됩니다. 관리 콘솔에서 [!UICONTROL Cloud Manager] 제품 프로필에 사용자를 추가하면 특정 역할 멤버십이 제공됩니다.

>[!CAUTION]
>
>사용하려면 [!UICONTROL Cloud Manager]Adobe ID와 Adobe Managed Services 제품 컨텍스트가 있어야 합니다.

관리 콘솔에서 [!UICONTROL Cloud Manager] 제품 프로필에 사용자를 추가하여 특정 역할 멤버십을 할당할 수 있습니다.

Admin Console를 사용하여 [!UICONTROL Cloud Manager]다음 역할을 만듭니다.

>[!NOTE]
>
>Adobe Admin Console는 조직 전체에서 Adobe 이용 권한을 관리할 수 있는 중앙 관리 기능을 제공합니다.
>
>Adobe Admin Console에 대한 자세한 내용은 [관리 콘솔 설명서를](https://helpx.adobe.com/enterprise/using/admin-console.html)참조하십시오.

| **[!UICONTROL Cloud Manager]역할** | **설명** |
|---|---|
| 비즈니스 담당자 | KPI 정의, 프로덕션 배포 승인, 중요한 3 계층 오류 무시를 책임지고 있습니다. |
| 프로그램 관리자 | 팀 설정 수행, 상태 검토 및 KPI 보기를 [!UICONTROL Cloud Manager] 수행하는 데 사용합니다. 중요한 3 계층 오류를 승인할 수 있습니다. |
| 배포 관리자 | 배포 작업을 관리합니다. 단계/프로덕션 배포를 실행하는 [!UICONTROL Cloud Manager] 데 사용합니다. 중요한 3 계층 오류를 승인할 수 있습니다. Git 액세스 권한이 있습니다. |
| 개발자 | 사용자 지정 애플리케이션 코드를 개발하고 테스트합니다. 상태를 확인하는 데 주로 사용됩니다 [!UICONTROL Cloud Manager] . Git에 대한 액세스 권한 부여 |
| Customer Success Engineer | 일반적으로 AMS 고객을 위한 고객 성공을 지원합니다. CSE 관리자가 [!UICONTROL Cloud Manager] 필요한 배포를 실행하기 위한 목적으로 상호 작용합니다. |
| 컨텐츠 작성자 | 는 일반적으로 상호 작용하지 [!UICONTROL Cloud Manager]않습니다. 프로그램 전환기 (탐색) 를 사용하여 [!UICONTROL Cloud Manager] AEM에 액세스할 [!UICONTROL Experience Cloud]수 있습니다. |

### Admin Console를 사용하여 팀 설정 {#using-admin-console-to-set-up-team}

[!UICONTROL Cloud Manager] 사용자에게 적절한 역할 기반 권한을 제공하기 위해, 고객의 조직의 관리자가 [!UICONTROL AEM Managed Services] 제품 컨텍스트에서 새 제품 프로필을 만들어야 합니다.

>[!NOTE]
>
>Admin Console를 강조하고 팀을 설정하려면 (사용자 및 역할) 브라우저를 열고 [https://adminconsole.adobe.com를 방문하십시오](https://adminconsole.adobe.com/enterprise).

아래 그림과 같이 일반 관리 콘솔 기능을 사용하여 이러한 제품 프로필에 사용자 (또는 그룹) 를 추가할 수 있습니다.

1. Admin Console에 로그인하고 **새 프로필을** 클릭하여 새 프로필을 추가합니다.

   ![](assets/admin_console_roles.png)

1. 필드를 채워 새 역할을 [!UICONTROL Cloud Manager]설정합니다.

   **프로필 이름**, **설명을** 입력하여 새 프로필을 만듭니다. 또한 프로필에 **대한 권한 그룹을** 선택할 수 있습니다.

   **완료를** 클릭하여 프로필 작성 단계를 완료합니다.

   ![](assets/screen_shot_2018-04-23at75014am.png)

## AEM 애플리케이션 프로젝트 설정 {#aem-application-project-setup}

에서 애플리케이션 프로젝트를 설정하기 [!UICONTROL Cloud Manager]전에 두 가지 시나리오 중 하나를 고려해야 합니다. AEM 6.4를 처음 사용하거나 기존 고객일 수도 있습니다.

>[!NOTE]
>
>액세스 권한을 받으려면 [!UICONTROL Cloud Manager]고객 성공 엔지니어 (CSE) 에 문의하여 시작하려면 URL 및 자격 증명을 얻으십시오.

다음 두 가지 시나리오를 기반으로 [!UICONTROL Cloud Manager]애플리케이션 프로젝트를 설정할 수 있습니다.

* **새 AEM 프로젝트**:

새 AEM 프로젝트는 기존 프로젝트를 활용하고 작업을 수행합니다 [!UICONTROL Cloud Manager].

자세한 내용은 AEM 6.4 [시작하기를 참조하십시오](https://chl-author./content/help/en/experience-manager/6-4/sites/deploying/using/deploy.html). 또한 자세한 내용은 [AEM 리소스를](https://www.adobe.com/marketing-cloud/experience-manager/resources.html?promoid=759X6WV8&mv=other) 참조하십시오.

* **기존 AEM 프로젝트**:

기존 AEM 프로젝트는 프로젝트 설정에 대한 규칙을 확인해야 합니다. 기존 AEM 설치를 업그레이드하여 AEM 6.4에서 제공되는 새로운 기능과 개선 사항을 얻고 시작할 [!UICONTROL Cloud Manager]수 있습니다. 이러한 기준은 최소 변경 사항과 함께 사용해야 합니다. 고객 성공 엔지니어 (CSE) 에 지원을 요청하십시오.

AEM 인스턴스 업그레이드에 대한 추가 정보를 6.4로 업그레이드하려면 AEM 6.4 [업그레이드를 참조하십시오](https://helpx.adobe.com/experience-manager/6-4/sites/deploying/using/upgrade.html).

### 저장소 설정 {#setting-up-repository}

초기에 비어 있는 하나의 Git 리포지토리는 온보딩된 [!UICONTROL Cloud Manager]각 프로그램에 대해 제공됩니다. 개발자와 배포 관리자는 CSE의 Git URL 및 자격 증명과 함께 제공됩니다.

개발자는 이 정보를 사용하여 아래 섹션에 있는** Project Set Up** 의 지침에 따라 코드를 추가하여 사용하기 전에 설정 요구 사항을 완료할 [!UICONTROL Cloud Manager]수 있습니다.

## Dispatcher Configurations {#dispatcher-configurations}

[!UICONTROL Cloud Manager] 은 일반적인 AEM 컨텐츠 패키지뿐만 아니라 Git 리포지토리에 저장된 웹 서버 및 Dispatcher 구성 파일을 배포할 수 있습니다.

이 기능을 활용하기 위해 Maven Build는 ***conf*** 와 ***conf. d 라는 두 개의 디렉토리를 포함하는 zip 파일을 생성합니다***.

Dispatcher 인스턴스에 배포하면 이러한 디렉토리의 컨텐츠가 Dispatcher 인스턴스에 있는 해당 디렉토리의 컨텐츠를 덮어씁니다. 웹 서버와 Dispatcher 구성 파일에는 종종 환경별 정보가 필요하므로 이 기능을 올바로 사용하려면 먼저 해당 환경 변수를 /etc/sysconfig/httpd로 추출하려면 먼저 CSE (Customer Success Engineer) 와 협력해야 합니다.

Dispatcher 구성에서 초기 프로세스를 완료하려면 아래 단계를 따르십시오.

1. CSE에서 현재 프로덕션 구성 파일을 얻습니다.
1. 하드 코딩된 환경별 데이터 (예: 퍼블리싱 렌더러 IP) 를 제거하고 변수로 바꿉니다.
1. 각 Target Dispatcher에 대해 키-값 쌍에 필요한 변수를 정의하고 CSE가 각 인스턴스에서 ***/etc/sysconfig/httpd*** 에 추가하도록 요청합니다.
1. 스테이지에서 업데이트된 구성을 테스트한 다음 CSE를 프로덕션 팀에 배포하여 제대로 작동하는지 확인합니다.
1. Git에 파일 커밋
1. [!UICONTROL Cloud Manager]배포.

maven-assembly-plugin를 사용하여 실제 zip 파일을 생성할 수 있습니다. Lazybones AEM 다중 모듈 템플릿을 사용하여 생성된 프로젝트는 프로젝트 작성의 일부로 만들어진 올바른 Maven 프로젝트 구조를 가질 수 있습니다.

>[!NOTE]
>
>Dispatcher 구성은 온보드 단계에서 완료되지만 [!UICONTROL Cloud Manager]나중에 수행할 수도 있습니다.

### 성능 테스트용 Dispatcher 구성 {#configuring-dispatcher-for-performance-testing}

성능 테스트를 [!UICONTROL Cloud Manager] 제대로 실행하려면 Stage Dispatcher 서버가 프로덕션 서버와 일관된 방식으로 프로덕션 디스패처와 동일한 호스트 이름에 응답해야 합니다.

*예를*들어 고객이 프로덕션 호스트 이름으로 [www.myco.com](http://www.myco.com/) 및 [www.myotherco.com](http://www.myotherco.com,/) 를 보유하고 있고 stage-myco. adobecqms. net 이 스테이지 호스트 이름으로 있는 경우 다음과 같은 요청이 적절히 응답해야 합니다.

```
curl -H"Host: www.myco.com" http://stage-myco.adobecqms.net/en/home.html
```

이렇게 하면 호스트 이름이 Dispatcher 구성에서 제대로 구성되었을 뿐만 아니라, ***/etc/map***, 모든 Apache 다시 쓰기 또는 진짜로 다른 경로 ***매핑/필터*** 규칙을 Stage와 Production 간에 일관되게 구현할 수 있습니다.

## 개발 모범 사례 {#development-best-practices}

사용하기 [!UICONTROL Cloud Manager]전에 프로젝트를 설정하고 웹 서버를 구성하거나 구성 구성을 위한 몇 가지 우수 사례를 이해하는 것이 좋습니다.

### 프로젝트 설정 {#project-set-up}

프로젝트는 작업할 [!UICONTROL Cloud Manager]수 있도록 일부 기준을 준수해야 합니다.

프로젝트 설정에 대한 우수 사례를 [!UICONTROL Cloud Manager]따르십시오.

* Apache Maven 이 제공하는 유일한 빌드 툴은 Apache Maven 입니다. Apache Maven 3.3.9가 설치되어 있습니다.
* Linux 환경에서 빌드는 루트 사용자로 docker 컨테이너의 실행됩니다.
* 설치된 Java 버전은 Oracle JDK 8 u 161 입니다.
* BZIP 2, Unzip, libpng, imagemagick 및 graphicsmagick와 같은 몇 가지 추가 시스템 패키지가 설치되어 있습니다. 다른 패키지가 필요한 경우 CSE를 통해 요청해야 합니다.
* maven는 항상 command mvn -b clean 패키지로 실행됩니다.
* 하나의 Git 리포지토리가 제공됩니다. 이 저장소의 루트에 pom.xml 파일이 있어야 합니다. 이 pom.xml 파일은 하위 모듈 (차례로 다른 하위 모듈 등) 를 참조할 수 있습니다. 필요한 경우 시작점이 하나만 있어야 합니다.
* maven는 공개 Adobe 가공물 저장소 (repo.adobe.com를 자동으로 포함하는 settings.xml 파일을 포함하는 시스템 수준에서 구성됩니다.
* pom.xml 파일에 저장소를 추가할 수 있습니다. 그러나 암호로 보호되거나 네트워크에 보호된 결함 리포지토리에 대한 액세스는 지원되지 않습니다.
* Target 이라는 디렉토리에 포함되어 있는 zip 파일을 스캔하여 배포 가능한 컨텐츠 패키지를 검색합니다. 여러 하위 모듈에서 컨텐츠 패키지를 생성할 수 있습니다.
* 둘 이상의 컨텐츠 패키지가 있는 경우 패키지 배포 순서는 보장되지 않습니다. 특정 순서가 필요한 경우 컨텐츠 패키지 종속성을 사용하여 순서를 정의할 수 있습니다.

<!-- 

Comment Type: annotation
Last Modified By: jsyal
Last Modified Date: 2018-05-02T18:18:15.028-0400

change as per KT

 -->

### 다음 단계 {#the-next-steps}

일반 구성을 설정한 [!UICONTROL Cloud Manager]후에는 바로 사용할 수 있습니다.

[[! Uicontrol Cloud Manager를](https://helpx.adobe.com/experience-manager/cloud-manager/using/using-cloud-manager.html) [!UICONTROL Cloud Manager]사용하여 시작하십시오.
