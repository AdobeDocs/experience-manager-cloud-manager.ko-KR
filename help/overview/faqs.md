---
title: Cloud Manager FAQ
description: AMS 고객을 위한 Cloud Manager에 대해 가장 자주 묻는 질문에 대한 답변에 대해 알아봅니다.
exl-id: 52c1ca23-5b42-4eae-b63a-4b22ef1a5aee
source-git-commit: 4c4a2688cab8e5c81efa4b7b5e26f3c7b5dc30d6
workflow-type: tm+mt
source-wordcount: '748'
ht-degree: 60%

---


# Cloud Manager FAQ {#cloud-manager-faqs}

이 문서에서는 AMS 고객을 위한 Cloud Manager에 대해 가장 자주 묻는 질문에 대한 답변을 제공합니다.

## Cloud Manager 빌드와 함께 Java 11을 사용할 수 있습니까? {#java-11}

예. Java 11에 대한 올바른 설정으로 `maven-toolchains-plugin`을(를) 추가해야 합니다.

* 이 프로세스는 [여기](/help/getting-started/using-the-wizard.md)에 설명되어 있습니다.
* 예를 들어 [WKND 샘플 프로젝트 코드](https://github.com/adobe/aem-guides-wknd/commit/6cb5238cb6b932735dcf91b21b0d835ae3a7fe75)을(를) 참조하십시오.

## Java 8에서 Java 11로 전환한 후 maven-scr-plugin에 대한 오류와 함께 빌드가 실패합니다. 어떻게 해야 합니까? {#maven-src-plugin}

빌드를 Java 8에서 11로 전환하려고 하면 AEM Cloud Manager 빌드가 실패할 수 있습니다. 다음 오류가 발생하면 `maven-scr-plugin`을 제거하고 모든 OSGi 주석을 OSGi R6 주석으로 변환해야 합니다.

```text
[main] [ERROR] Failed to execute goal org.apache.felix:maven-scr-plugin:1.26.4:scr (generate-scr-scrdescriptor) on project helloworld.core: /build_root/build/testsite/src/main/java/com/adobe/HelloWorldServiceImpl.java : Unable to load compiled class: com.adobe.HelloWorldServiceImpl: com/adobe/HelloWorldServiceImpl has been compiled by a more recent version of the Java Runtime (class file version 55.0), this version of the Java Runtime only recognizes class file versions up to 52.0 -> [Help 1]
```

이 플러그인을 제거하는 방법에 대한 지침은 [여기](https://cqdump.joerghoh.de/2019/01/03/from-scr-annotations-to-osgi-annotations/)를 참조하세요.

## Java 8에서 Java 11로 전환한 후 RequireJavaVersion에 대한 오류와 함께 빌드가 실패합니다. 어떻게 하면 표시할 수 있습니까? {#requirejavaversion}

Cloud Manager 빌드의 경우 `maven-enforcer-plugin`이 해당 오류와 함께 실패할 수 있습니다.

```text
[main] [WARNING] Rule 1: org.apache.maven.plugins.enforcer.RequireJavaVersion
```

이 알려진 문제는 Cloud Manager이 코드를 컴파일하는 대신 다른 버전의 Java를 사용하여 Maven 명령을 실행했기 때문입니다. `maven-enforcer-plugin` 구성에서 `requireJavaVersion`을(를) 생략합니다.

## 코드 품질 검사에 실패하여 이제 배포가 중단되었습니다. 이 검사를 우회하는 방법이 있습니까? {#deployment-stuck}

예. 보안 등급을 제외한 모든 코드 품질 실패는 중요하지 않은 지표입니다. 따라서 결과 UI의 항목을 확장하여 배포 파이프라인의 일부로 우회할 수 있습니다.

[배포 관리자, 프로젝트 관리자 또는 비즈니스 소유자](/help/requirements/users-and-roles.md#role-definitions) 역할을 가진 사용자는 문제를 재정의할 수 있습니다. 이 경우 파이프라인이 진행됩니다. 또는 문제를 수락할 수 있으며, 이 경우 파이프라인이 실패와 함께 중지됩니다.

자세한 내용은 [파이프라인 실행 중 3계층 게이트](/help/using/code-quality-testing.md#three-tier-gates-while-running-a-pipeline) 및 [비프로덕션 파이프라인 구성](/help/using/non-production-pipelines.md#understanding-the-flow) 문서를 참조하십시오.

## Adobe Managed Services 환경의 성능 테스트 단계에서 Cloud Manager 배포가 실패합니다. 이 문제를 디버깅하여 중요 지표를 전달하려면 어떻게 해야 합니까? {#debug-critical-metrics}

이 질문에 대한 단일의 답변은 없습니다. 그러나 성능 테스트 단계에 대한 다음 사항은 도움이 될 수 있습니다.

* 이 단계는 웹 성능 단계입니다. 즉, 웹 브라우저를 사용하여 페이지를 로드할 때입니다.
* 결과 .csv 파일에 나열된 URL은 테스트 중에 Cloud Manager 인프라의 Chrome 브라우저에 로드됩니다.
* 실패하는 일반적인 지표는 오류율입니다. 따라서 URL을 전달하려면 기본 URL이 `20`초 이내에 `200` 상태로 로드되어야 합니다. 페이지 로드가 `20`초를 초과하는 경우 `504` 오류로 표시됩니다.
* 사이트에 사용자 인증이 필요한 경우 사이트에 인증할 수 있도록 테스트 구성에 대한 [테스트 결과 이해](/help/using/code-quality-testing.md#authenticated-performance-testing)를 참조하십시오.

품질 검사에 대한 자세한 내용은 [테스트 결과 이해](/help/using/code-quality-testing.md)를 참조하십시오.

## Maven 프로젝트 버전에 SNAPSHOT을 사용할 수 있습니까? {#snapshot}

예. 개발자 배포의 경우 git 분기 `pom.xml` 파일의 `<version>` 값 끝에 `-SNAPSHOT`이 포함되어야 합니다.

버전을 변경하지 않은 경우에도 후속 배포를 계속 설치할 수 있습니다. 개발자 배포에서는 Maven 빌드에 대해 자동 버전이 추가되거나 생성되지 않습니다.

단계 및 프로덕션 빌드 또는 배포에 대해 버전을 `-SNAPSHOT`으로 설정할 수도 있습니다. Cloud Manager는 자동으로 적절한 버전 번호를 설정하고 git에 태그를 생성합니다. 이 태그는 필요한 경우 나중에 참조할 수 있습니다.

버전 처리에 대한 자세한 내용은 [여기에 문서화](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/managing-code/project-version-handling)되어 있습니다.

## 패키지 및 번들 버전 관리는 스테이징 및 프로덕션 배포에서 어떻게 작동합니까? {#staging-production}

스테이징 및 프로덕션 배포에서는 [여기](/help/managing-code/maven-project-version.md)에 설명된 대로 자동 버전이 생성됩니다.

스테이지 및 프로덕션 배포에서 사용자 정의 버전을 사용하려면 `1.0.0`과 같이 적절한 3부분으로 구성된 Maven 버전을 설정합니다. 프로덕션에 배포할 때마다 버전을 늘립니다.

Cloud Manager는 스테이지 및 프로덕션 빌드에 해당 버전을 자동으로 추가하고 git 분기를 만듭니다. 특별한 구성은 필요하지 않습니다. 앞에서 설명한 대로 Maven 버전을 설정하지 않으면 배포가 계속 성공하고 버전이 자동 설정됩니다.

## Maven 빌드가 Cloud Manager 배포에 실패하지만 오류 없이 로컬로 빌드됩니다. 무엇이 문제입니까? {#maven-build-fail}

자세한 내용은 이 [git 리소스](https://github.com/cqsupport/cloud-manager/blob/main/cm-build-step-fails.md)를 참조하십시오.

## aio 명령을 사용하여 변수를 설정할 수 없습니다. 어떻게 하면 표시할 수 있습니까? {#set-variable}

`aio` 명령을 통해 파이프라인 변수를 나열하거나 설정하려고 하면 다음과 같은 403 오류가 나타날 수 있습니다.

```shell
$ aio cloudmanager:list-pipeline-variables 222

Cannot get variables: https://cloudmanager.adobe.io/api/program/111/pipeline/222/variables (403 Forbidden)

$ aio cloudmanager:set-pipeline-variables 222 --variable TEST 1

Cannot get variables: https://cloudmanager.adobe.io/api/program/111/pipeline/222/variables (403 Forbidden)

$ aio cloudmanager:set-environment-variables 1755 --variable TEST 1

setting variables... !

Cannot set variables: https://cloudmanager.adobe.io/api/program/111/environment/222/variables (403 Forbidden)
```

이 경우 이러한 명령을 실행하는 사용자는 Admin Console에서 **Deployment Manager** 역할에 추가되어야 합니다.

자세한 내용은 [API 권한](https://developer.adobe.com/experience-cloud/cloud-manager/guides/getting-started/permissions/)을 참조하십시오.
