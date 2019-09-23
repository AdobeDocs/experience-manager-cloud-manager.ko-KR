---
title: Cloud Manager용 일반 구성 설정
seo-title: Adobe AEM Cloud Manager용 일반 구성 설정
description: Cloud Manager 설정 및 사용자 인터페이스에서 컨텐츠 관리를 위한 사전 요구 사항입니다.
seo-description: Adobe AEM Cloud Manager 설정 및 사용자 인터페이스에서 컨텐츠 관리를 위한 사전 요구 사항입니다.
uuid: 65d795f9-aa97-4816-b66b-03b5ae961f47
contentOwner: jsyal
discoiquuid: 03241b88-8d28-401b-aa42-17ead6183cd8
translation-type: tm+mt
source-git-commit: 093e25fa1cf2f5cdc3d8ea0bffd5c02ade854a88

---


# 일반 구성 설정 [!UICONTROL Cloud Manager]{#setting-up-general-configurations-for-cloud-manager}

다음 섹션에서는 사용자 인터페이스에서 컨텐츠를 설정 [!UICONTROL Cloud Manager] 및 관리하기 위한 사전 요구 사항을 설명합니다.

이 섹션 페이지에서는 다음 주제를 다룹니다.

* **사용자 및 역할 설정**
* **AEM 애플리케이션 프로젝트 설정**
* **발송자 구성**
* **개발 모범 사례**

다음 다이어그램은 최상의 코드를 지속적으로 전달할 [!UICONTROL Cloud Manager] 수 있는 다양한 함수를 보여 줍니다.

![](assets/screen_shot_2018-05-01at81926pm.png)

## 사용자 및 역할 설정 {#setting-up-users-and-roles}

역할은 Adobe Admin Console [!UICONTROL Cloud Manager] 에서 관리합니다. 관리 콘솔에서 사용자를 제품 프로필에 추가하여 특정 역할 [!UICONTROL Cloud Manager] 멤버십이 제공됩니다.

>[!CAUTION]
>
>사용하려면 [!UICONTROL Cloud Manager]Adobe ID와 Adobe Managed Services 제품 컨텍스트가 있어야 합니다.

관리 콘솔에서 제품 프로필에 사용자를 추가하여 특정 역할 [!UICONTROL Cloud Manager] 멤버십을 할당할 수 있습니다.

관리 콘솔을 사용하여 다음 역할을 [!UICONTROL Cloud Manager]만듭니다.

>[!NOTE]
>
>Adobe Admin Console은 전사적으로 Adobe 이용 권한을 중앙에서 관리할 수 있는 기능을 제공합니다.
>
>Adobe Admin Console에 대한 자세한 내용은 Admin Console 설명서를 [참조하십시오](https://helpx.adobe.com/enterprise/using/admin-console.html).

| **[!UICONTROL Cloud Manager]역할** | **설명** |
|---|---|
| 비즈니스 소유자 | KPI 정의, 프로덕션 배포 승인, 중요한 3단계 장애 무시 등의 책임입니다. |
| 프로그램 관리자 | 팀 설정을 [!UICONTROL Cloud Manager] 수행하고 상태를 검토하고 KPI를 보는 데 사용합니다. 중요한 3단계 오류를 승인할 수 있습니다. |
| 배포 관리자 | 배포 작업을 관리합니다. 스테이지/프로덕션 배포를 실행하는 [!UICONTROL Cloud Manager] 데 사용됩니다. 중요한 3단계 오류를 승인할 수 있습니다. git 액세스 |
| 개발자 | 사용자 정의 애플리케이션 코드를 개발하고 테스트합니다. 주로 상태를 보는 [!UICONTROL Cloud Manager] 데 사용됩니다. git에 대한 액세스 권한을 보유합니다. |
| 고객 성공 엔지니어 | 일반적으로 AMS 고객의 성공을 지원합니다. CSE 감독이 필요한 배포 실행을 [!UICONTROL Cloud Manager] 위해 상호 작용합니다. |
| 컨텐츠 작성자 | 일반적으로 상호 작용하지 않습니다 [!UICONTROL Cloud Manager]. 프로그램 [!UICONTROL Cloud Manager] 전환기(이동 중)를 사용하여 AEM에 액세스할 [!UICONTROL Experience Cloud]수 있습니다. |

### 관리 콘솔을 사용하여 팀 설정 {#using-admin-console-to-set-up-team}

사용자에게 적절한 역할 기반 권한을 제공하려면 고객 조직의 관리자가 제품 컨텍스트에서 새 제품 프로필을 만들어야 [!UICONTROL Cloud Manager] [!UICONTROL AEM Managed Services] 합니다.

>[!NOTE]
>
>관리 콘솔에 액세스하고 팀(사용자 및 역할)을 설정하려면 브라우저를 열고 https://adminconsole.adobe.com을 [방문하십시오](https://adminconsole.adobe.com/enterprise).

아래 그림과 같이 이러한 제품 프로필에 사용자(또는 그룹)를 추가하는 작업은 일반 관리 콘솔 기능을 사용하여 수행됩니다.

1. 관리 콘솔에 로그인하고 새 **프로필을** 클릭하여 새 프로필을 추가합니다.

   ![](assets/admin_console_roles.png)

1. 필드를 채워 새 역할을 [!UICONTROL Cloud Manager]설정합니다.

   프로필 **이름**, **설명을** 입력하여 새 프로필을 만듭니다. 또한 프로필에 대한 권한 **그룹을** 선택할 수 있습니다.

   완료를 **클릭하여** 프로필 작성 단계를 완료합니다.

   ![](assets/screen_shot_2018-04-23at75014am.png)

## AEM 애플리케이션 프로젝트 설정 {#aem-application-project-setup}

에서 응용 프로그램 프로젝트를 설정하기 전에 두 가지 시나리오 [!UICONTROL Cloud Manager]중 하나를 고려해야 합니다. AEM 6.4를 처음 사용했거나 기존 고객일 수 있습니다.

>[!NOTE]
>
>액세스 권한을 얻으려면 CSE(Customer Success Engineers) [!UICONTROL Cloud Manager]에 문의하여 URL과 자격 증명을 얻으십시오.

다음 두 가지 시나리오를 [!UICONTROL Cloud Manager]기반으로 응용 프로그램 프로젝트를 설정할 수 있습니다.

* **새 AEM 프로젝트**:

새 AEM 프로젝트는 기존 프로젝트를 활용하고 [!UICONTROL Cloud Manager]작업합니다.

자세한 내용은 AEM [6.4 시작을 참조하십시오](https://chl-author./content/help/en/experience-manager/6-4/sites/deploying/using/deploy.html). 또한 자세한 내용은 AEM [리소스를](https://www.adobe.com/marketing-cloud/experience-manager/resources.html?promoid=759X6WV8&mv=other) 참조하십시오.

* **기존 AEM 프로젝트**:

기존 AEM 프로젝트는 프로젝트 설정 규칙을 확인해야 합니다. 기존 AEM 설치를 업그레이드하여 AEM 6.4에서 제공하는 새로운 기능 및 개선 사항을 얻고 시작할 수 [!UICONTROL Cloud Manager]있습니다. 이러한 기준은 최소한으로 조정되어야 합니다. 고객 성공 엔지니어(CSE)에게 지원을 요청하십시오.

AEM 인스턴스를 6.4로 업그레이드하는 방법에 대한 자세한 내용은 AEM [6.4로 업그레이드를 참조하십시오](https://helpx.adobe.com/experience-manager/6-4/sites/deploying/using/upgrade.html).

### 저장소 설정 {#setting-up-repository}

처음에 비어 있던 단일 git 리포지토리는 온보딩된 각 프로그램에 대해 프로비저닝됩니다 [!UICONTROL Cloud Manager]. 개발자 및 배포 관리자는 CSE에서 Git URL과 자격 증명을 제공합니다.

이 정보를 통해 개발자는 아래의 다음 섹션에 있는 **프로젝트 설정 **의 지침에 따라 코드를 추가하여 사용 전에 설정 요구 사항을 완료할 수 [!UICONTROL Cloud Manager]있습니다.

## 발송자 구성 {#dispatcher-configurations}

[!UICONTROL Cloud Manager] 웹 서버 및 디스패처 구성 파일이 일반적인 AEM 컨텐츠 패키지뿐만 아니라 git 리포지토리에 저장되어 있다고 가정할 때 배포할 수 있습니다.

이 기능을 활용하기 위해 Maven 빌드는 두 개의 디렉토리 즉, ***conf*** 및 ***conf.d를 포함하는 zip 파일을 생성합니다***.

디스패처 인스턴스에 배포하면 이러한 디렉토리의 내용이 디스패처 인스턴스의 이러한 디렉토리 컨텐츠를 덮어씁니다. 웹 서버 및 디스패처 구성 파일은 환경별 정보가 자주 필요하므로 이 기능을 올바르게 사용하려면 먼저 CSE(Customer Success Engineers)와 협력하여 이러한 환경 변수를 /etc/sysconfig/httpd로 추출해야 합니다.

다음 단계에 따라 디스패처를 구성하는 초기 프로세스를 완료합니다.

1. CSE에서 현재 프로덕션 구성 파일을 얻습니다.
1. 하드 코딩된 환경별 데이터(예: 게시 렌더러 IP)를 제거하고 변수로 대체합니다.
1. 각 대상 디스패처에 대한 키-값 쌍으로 필요한 변수를 정의하고 각 인스턴스에서 ***/etc/sysconfig/httpd에*** CSE를 요청합니다.
1. 스테이지에서 업데이트된 구성을 테스트한 다음 CSE가 제대로 작동하는지 확인하기 위해 프로덕션에 배포하도록 요청합니다.
1. git에 파일 커밋
1. 배포 - [!UICONTROL Cloud Manager]

maven-assembly-plugin을 사용하여 실제 zip 파일을 생성할 수 있습니다. Lazybones AEM 다중 모듈 템플릿을 사용하여 생성된 프로젝트는 프로젝트 제작의 일부로 올바른 Maven 프로젝트 구조를 만들 수 있습니다.

>[!NOTE]
>
>디스패처 구성은 온보드 중에 [!UICONTROL Cloud Manager]수행되지만 이후 단계에서도 수행할 수 있습니다.

### 성능 테스트를 위한 Dispatcher 구성 {#configuring-dispatcher-for-performance-testing}

성능 테스트를 제대로 [!UICONTROL Cloud Manager] 실행하려면 스테이지 디스패처 서버가 프로덕션 서버와 동일한 호스트 이름에 프로덕션 디스패처와 응답해야 합니다.

*예를 들어*&#x200B;고객이 프로덕션 호스트 [이름으로 www.myco.com](http://www.myco.com/) 및 [www.myotherco.com를](http://www.myotherco.com,/) 사용하고 스테이지 호스트 이름으로 stage-myco.adobecqms.net을 사용하는 경우 이와 같은 요청은 적절히 응답해야 합니다.

```
curl -H"Host: www.myco.com" http://stage-myco.adobecqms.net/en/home.html
```

이렇게 하려면 호스트 이름이 디스패처 구성에서 제대로 구성되어야 할 뿐만 아니라 ***/etc/map***, 모든 Apache 다시 쓰기 또는 기타 모든 경로 ***매핑/필터*** 규칙이 스테이지와 프로덕션 간에 일관된 방식으로 구현되어야 합니다.

## 개발 모범 사례 {#development-best-practices}

사용하기 [!UICONTROL Cloud Manager]전에 웹 서버를 설정하고 구성하거나 구성을 표시하기 위한 몇 가지 모범 사례를 이해하는 것이 좋습니다.

### 프로젝트 설정 {#project-set-up}

프로젝트를 사용하려면 몇 가지 기준을 준수해야 합니다 [!UICONTROL Cloud Manager].

다음 사이트에서 프로젝트를 설정하는 최상의 방법을 따르십시오. [!UICONTROL Cloud Manager]

* 제공 및 지원되는 유일한 빌드 도구는 Apache Maven입니다. Apache Maven 3.3.9가 설치되어 있습니다.
* 빌드는 Docker 컨테이너의 Linux 환경에서 루트 사용자로 실행됩니다.
* 설치된 Java 버전은 Oracle JDK 8u161입니다.
* bzip2, unzip, libpng, imagemagick 및 graphicsmagick과 같은 일부 추가 시스템 패키지가 설치되어 있습니다. 다른 패키지가 필요한 경우 CSE를 통해 요청해야 합니다.
* mvn -B clean package는 항상 mvn 명령을 사용하여 실행됩니다.
* 하나의 git 리포지토리가 제공됩니다. 이 저장소의 루트에 pom.xml 파일이 있어야 합니다. 이 pom.xml 파일은 하위 모듈 수를 참조할 수 있습니다(이 경우 다른 하위 모듈 등이 있을 수 있음). 필요한 경우 한 개의 진입점만 있으면 됩니다.
* Maven은 공개 Adobe 아티팩트 저장소(repo.adobe.com)를 자동으로 포함하는 settings.xml 파일을 사용하여 시스템 수준에서 구성됩니다.
* pom.xml 파일에 저장소를 추가할 수 있습니다. 그러나 암호로 보호되거나 네트워크로 보호된 객체 저장소에 대한 액세스는 지원되지 않습니다.
* 배포 가능한 컨텐츠 패키지는 target이라는 디렉토리에 포함되어 있는 zip 파일을 스캔하여 검색합니다. 다시 한 번 말하지만, 어떤 수의 하위 모듈에서도 컨텐츠 패키지를 생성할 수 있습니다.
* 두 개 이상의 컨텐츠 패키지가 있는 경우 패키지 배포 순서가 보장되지 않습니다. 특정 주문이 필요한 경우 컨텐츠 패키지 종속성을 사용하여 순서를 정의할 수 있습니다.

<!-- 

Comment Type: annotation
Last Modified By: jsyal
Last Modified Date: 2018-05-02T18:18:15.028-0400

change as per KT

 -->

### 다음 단계 {#the-next-steps}

일반 구성을 설정하면 사용할 준비가 [!UICONTROL Cloud Manager]됩니다.

시작하려면 [[!UICONTROL Cloud Manager]](https://helpx.adobe.com/experience-manager/cloud-manager/using/using-cloud-manager.html) 사용을 [!UICONTROL Cloud Manager]참조하십시오.
