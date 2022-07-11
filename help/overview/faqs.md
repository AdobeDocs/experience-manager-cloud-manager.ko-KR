---
title: Cloud Manager FAQ
description: 이 문서에서는 AMS 고객을 위한 Cloud Manager에 대해 자주 묻는 질문에 대한 답변을 제공합니다.
exl-id: 52c1ca23-5b42-4eae-b63a-4b22ef1a5aee
source-git-commit: 6be659e02df0657ec7d3dbce8c18c44a327a36f4
workflow-type: tm+mt
source-wordcount: '776'
ht-degree: 1%

---


# Cloud Manager FAQ {#cloud-manager-faqs}

이 문서에서는 AMS 고객을 위한 Cloud Manager에 대해 자주 묻는 질문에 대한 답변을 제공합니다.

## Cloud Manager 빌드와 함께 Java 11을 사용할 수 있습니까? {#java-11}

예. 을(를) 추가해야 합니다 `maven-toolchains-plugin` ( Java 11에 대한 올바른 설정 사용).

* 이 프로세스는 문서화되었습니다 [여기 있습니다.](/help/getting-started/using-the-wizard.md)
* 예를 보려면 [wknd 샘플 프로젝트 코드.](https://github.com/adobe/aem-guides-wknd/commit/6cb5238cb6b932735dcf91b21b0d835ae3a7fe75)

## Java 8에서 Java 11로 전환한 후 maven-scr-plugin에 대한 오류로 인해 내 빌드가 실패합니다. 어떻게 해야 합니까? {#maven-src-plugin}

빌드를 Java 8에서 11로 전환하려고 할 때 AEM Cloud Manager 빌드가 실패할 수 있습니다. 다음 오류가 발생하면 다음을 제거해야 합니다 `maven-scr-plugin` 모든 OSGi 주석을 OSGi R6 주석으로 변환합니다.

```text
[main] [ERROR] Failed to execute goal org.apache.felix:maven-scr-plugin:1.26.4:scr (generate-scr-scrdescriptor) on project helloworld.core: /build_root/build/testsite/src/main/java/com/adobe/HelloWorldServiceImpl.java : Unable to load compiled class: com.adobe.HelloWorldServiceImpl: com/adobe/HelloWorldServiceImpl has been compiled by a more recent version of the Java Runtime (class file version 55.0), this version of the Java Runtime only recognizes class file versions up to 52.0 -> [Help 1]
```

이 플러그인을 제거하는 방법에 대한 지침은 [여기 를 참조하십시오.](https://cqdump.wordpress.com/2019/01/03/from-scr-annotations-to-osgi-annotations/)

## Java 8에서 Java 11로 전환한 후 RequireJavaVersion에 대해 오류가 발생하여 빌드가 실패합니다. 어떻게 해야 합니까? {#requirejavaversion}

Cloud Manager 빌드의 경우 `maven-enforcer-plugin` 이 오류로 인해 실패할 수 있습니다.

```text
[main] [WARNING] Rule 1: org.apache.maven.plugins.enforcer.RequireJavaVersion
```

이 문제는 코드 컴파일과 비교하여 maven 명령을 실행하기 위해 다른 버전의 Java를 사용하는 Cloud Manager로 인해 알려진 문제입니다. 생략 `requireJavaVersion` 다음 `maven-enforcer-plugin` 구성.

## 코드 품질 검사에 실패하여 배포가 중단되었습니다. 이 수표를 우회할 수 있는 방법이 있나요? {#deployment-stuck}

예. 보안 등급을 제외한 모든 코드 품질 오류는 중요하지 않은 지표이므로 결과 UI에서 항목을 확장하여 배포 파이프라인의 일부로 우회할 수 있습니다.

을 사용하는 사용자 [배포 관리자, 프로젝트 관리자 또는 비즈니스 소유자](/help/requirements/users-and-roles.md#role-definitions) 역할은 문제를 재정의할 수 있습니다. 이 경우 파이프라인이 진행되거나 해당 문제를 수락할 수 있습니다. 이 경우 파이프라인이 오류로 중지됩니다.

문서 보기 [파이프라인 실행 중 3계층 게이트](/help/using/code-quality-testing.md#three-tier-gates-while-running-a-pipeline) 및 [비프로덕션 파이프라인 구성](/help/using/non-production-pipelines.md#understanding-the-flow) 자세한 내용

## Cloud Manager 배포는 Adobe Managed Services 환경의 성능 테스트 단계에서 실패합니다. 중요한 지표를 전달하려면 이 디버그 방법을 어떻게 적용합니까? {#debug-critical-metrics}

이 질문에 대한 한 가지 답변은 없다. 그러나 다음은 성능 테스트 단계의 몇 가지 중요한 점이며, 이러한 점은 사용자가 기억해야 합니다.

* 이 단계는 웹 성능 단계입니다. 즉, 웹 브라우저를 사용하여 페이지를 로드할 시간입니다.
* 결과 .csv 파일에 나열된 URL은 테스트 중에 Cloud Manager 인프라의 Chrome 브라우저에 로드됩니다.
* 실패하는 일반적인 지표는 오류 비율입니다.
   * URL을 전달하려면 기본 URL을 `200` 상태 및 보다 작음 `20` 초.
   * 를 초과하는 페이지 로드 `20` 초 는 로 표시됩니다. `504` 오류가 발생합니다.
* 사이트에 사용자 인증이 필요한 경우 문서를 참조하십시오 [테스트 결과 이해](/help/using/code-quality-testing.md#authenticated-performance-testing) 를 사용하도록 테스트 구성

문서 보기 [테스트 결과 이해](/help/using/code-quality-testing.md) 품질 검사에 대한 자세한 정보.

## Maven 프로젝트 버전에 SNAPSHOT을 사용할 수 있습니까? {#snapshot}

예. 개발자 배포의 경우 git 분기입니다 `pom.xml` 파일은 포함해야 합니다. `-SNAPSHOT` 의 끝 `<version>` 값.

따라서 버전이 변경되지 않은 경우에도 후속 배포를 계속 설치할 수 있습니다. 개발자 배포에서 maven 빌드에 대한 자동 버전이 추가되거나 생성되지 않습니다.

버전을 로 설정할 수도 있습니다. `-SNAPSHOT` 스테이지 및 프로덕션 빌드 또는 배포용. Cloud Manager는 적절한 버전 번호를 자동으로 설정하고 git에서 태그를 만듭니다. 필요한 경우 나중에 이 태그를 참조할 수 있습니다.

버전 처리에 대한 자세한 내용은 다음과 같습니다 [여기에 설명되어 있습니다.](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/managing-code/project-version-handling.html)

## 스테이징 및 프로덕션 배포에 패키지 및 번들 버전 관리는 어떻게 작동합니까? {#staging-production}

스테이징 및 프로덕션 배포에서 자동 버전이 생성됩니다 [여기에 설명된 대로,](/help/managing-code/maven-project-version.md)

스테이지 및 프로덕션 배포에서 사용자 정의 버전 지정을 위해 다음과 같은 적절한 3가지 부분 maven 버전을 설정합니다. `1.0.0`. 프로덕션에 배포할 때마다 버전을 늘립니다.

Cloud Manager는 해당 버전을 스테이징 및 프로덕션 빌드에 자동으로 추가하고 Git 분기를 만듭니다. 특별한 구성이 필요하지 않습니다. 이전에 설명한 대로 maven 버전을 설정하지 않은 경우 배포는 계속 성공하며 버전이 자동으로 설정됩니다.

## Cloud Manager 배포에 대한 전문 빌드가 실패하지만 오류 없이 로컬에서 빌드됩니다. 뭐가 잘못됐나요? {#maven-build-fail}

다음 보기 [git 리소스](https://github.com/cqsupport/cloud-manager/blob/main/cm-build-step-fails.md) 자세한 내용

## aio 명령을 사용하여 변수를 설정할 수 없습니다. 어떻게 해야 합니까? {#set-variable}

를 통해 파이프라인 변수를 나열하거나 설정하려고 할 때 다음과 같은 403 오류가 발생할 수 있습니다 `aio` 명령.

```shell
$ aio cloudmanager:list-pipeline-variables 222

Cannot get variables: https://cloudmanager.adobe.io/api/program/111/pipeline/222/variables (403 Forbidden)

$ aio cloudmanager:set-pipeline-variables 222 --variable TEST 1

Cannot get variables: https://cloudmanager.adobe.io/api/program/111/pipeline/222/variables (403 Forbidden)

$ aio cloudmanager:set-environment-variables 1755 --variable TEST 1

setting variables... !

Cannot set variables: https://cloudmanager.adobe.io/api/program/111/environment/222/variables (403 Forbidden)
```

이 경우 이러한 명령을 실행하는 사용자를 **배포 관리자** Admin Console의 역할입니다.

자세한 내용은 [API 권한](https://developer.adobe.com/experience-cloud/cloud-manager/guides/getting-started/permissions/) 자세한 내용
