---
title: Cloud Manager FAQ
seo-title: Cloud Manager FAQ
description: 문제 해결 팁을 얻으려면 Cloud Manager FAQ를 참조하십시오.
seo-description: Cloud Manager FAQ에 대한 답변을 얻으려면 이 페이지를 따르십시오
translation-type: tm+mt
source-git-commit: cb63a8bbe30b28668313dc851f17aa34fc166474
workflow-type: tm+mt
source-wordcount: '873'
ht-degree: 0%

---


# Cloud Manager FAQ {#cloud-manager-faqs}

다음 섹션에서는 Cloud Manager와 관련하여 자주 묻는 FAQ 중 일부에 대한 답변을 제공합니다.

## 1. Cloud Manager 빌드에 Java 11을 사용할 수 있습니까?{#java-11-cloud-manager}

Java 8에서 Java 11로 빌드를 전환할 때 AEM Cloud Manager 빌드가 실패합니다. 이 문제는 많은 원인을 가질 수 있으며 가장 일반적인 원인은 아래에 설명되어 있습니다.

* 문서화된 [여기](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/getting-started/create-application-project/using-the-wizard.html?lang=en#getting-started)에 Java 11에 대한 올바른 설정으로 maven-toolchain-plugin을 추가합니다.  예를 들어 [샘플 프로젝트 코드](https://github.com/adobe/aem-guides-wknd/commit/6cb5238cb6b932735dcf91b21b0d835ae3a7fe75)를 참조하십시오.

* 아래 오류가 발생하면 maven-scr-plugin의 사용을 제거하고 모든 OSGi 주석을 OSGi R6 주석으로 변환해야 합니다. 자세한 내용은 [여기](https://cqdump.wordpress.com/2019/01/03/from-scr-annotations-to-osgi-annotations/)를 참조하십시오.

   `[main] [ERROR] Failed to execute goal org.apache.felix:maven-scr-plugin:1.26.4:scr (generate-scr-scrdescriptor) on project helloworld.core: /build_root/build/testsite/src/main/java/com/adobe/HelloWorldServiceImpl.java : Unable to load compiled class: com.adobe.HelloWorldServiceImpl: com/adobe/HelloWorldServiceImpl has been compiled by a more recent version of the Java Runtime (class file version 55.0), this version of the Java Runtime only recognizes class file versions up to 52.0 -> [Help 1]`

* Cloud Manager의 경우 마비성 플러그인이 실패하여 `"[main] [WARNING] Rule 1: org.apache.maven.plugins.enforcer.RequireJavaVersion"` 오류가 발생합니다. 코드 컴파일 외에 maven 명령을 실행하기 위해 다른 버전의 java를 사용하는 클라우드 관리자로 인해 알려진 문제입니다. 이제 maven-enforcer-plugin 구성에서 `requireJavaVersion`을(를) 생략합니다.

## 2. 코드 품질 검사가 실패하여 배포가 중단됩니다. 이 수표를 우회할 방법이 있습니까?{#deployment-stuck}

*보안 등급*&#x200B;을 제외한 모든 코드 품질 오류는 중요하지 않은 지표이므로 결과 UI에서 항목을 확장하여 무시할 수 있습니다.

[배포 관리자, 프로젝트 관리자 또는 비즈니스 소유자](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/requirements/setting-up-users-and-roles.html?lang=en#requirements) 역할을 가진 사용자는 파이프라인이 진행되는 경우 문제를 무시하거나 문제를 허용할 수 있습니다. 이 경우 파이프라인이 실패로 중단됩니다.  자세한 내용은 파이프라인 실행 중 [3계층 게이츠](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/how-to-use/understand-your-test-results.html?lang=en#how-to-use)를 참조하십시오.

## 3. Adobe Managed Services 환경에서 성능 테스트 단계에서 Cloud Manager를 배포하지 못합니다. 중요한 지표를 전달하기 위해 이 문제를 어떻게 디버그합니까?{#debug-critical-metrics}

결과를 이해하려면 [테스트 결과 이해](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/how-to-use/understand-your-test-results.html?lang=en#how-to-use)를 참조하십시오.

성능 테스트 단계에 대한 일부 참고 사항:

* *성능 단계*&#x200B;는 웹 성능 단계입니다. 즉, 웹 브라우저를 사용하여 페이지를 로드할 때입니다.
* 결과 CSV 파일에 나열된 URL은 테스트 중에 클라우드 관리자 인프라의 Chrome 브라우저에 로드됩니다.
* 실패하는 일반적인 지표는 *오류 비율*&#x200B;입니다. URL이 전달되려면 기본 URL이 200초 이내에 20초 이내에 로드되어야 합니다. 20초를 초과하는 페이지 로드는 504 오류로 표시됩니다.
* 사이트에 사용자 인증이 필요한 경우 이 설명서를 참조하여 테스트를 구성하여 사이트에 인증할 수 있습니다.

## 4. 마스터 프로젝트 버전에서 스냅샷을 사용할 수 있습니까? 패키지 및 번들 jar 파일의 버전 관리가 단계 및 프로덕션에서 어떻게 작동합니까?{#snapshot-version}

1. 개발 배포의 경우 git 분기 pom.xml 파일은 `<version>` 값 끝에 -SNAPSHOT을 포함해야 합니다. 따라서 버전이 변경되지 않고 계속 설치되는 후속 배포가 가능합니다. 개발 배포에서 마스터 빌드에 대해 자동 버전이 추가 또는 생성되지 않습니다.

1. 단계 및 제작 과정에서 여기에 설명된 대로 자동 버전이 생성됩니다.

1. 스테이지와 프로덕션에서 사용자 정의 버전 관리를 수행하려면 `1.0.0`과 같은 3부 적합한 마스터 버전을 설정하십시오. 다른 제작 배포 작업을 수행할 때마다 버전을 늘립니다.

1. Cloud Manager는 스테이지와 프로덕션 빌드에 버전을 자동으로 추가하고 git 분기까지 만듭니다. 특별한 구성이 필요하지 않습니다. 위의 3단계를 건너뛸 경우 배포는 여전히 정상적으로 작동하며 버전은 자동으로 설정됩니다.

1. 스테이지와 프로덕션 빌드를 위해 `-SNAPSHOT`을(를) 사용하여 버전을 그대로 두는 경우, 그것도 괜찮습니다. Cloud Manager는 올바른 버전 번호를 자동으로 설정하고 git에서 태그를 만듭니다. 필요한 경우 이 태그를 나중에 참조할 수 있습니다.

1. 개발 시 일부 시험적 코드를 시도하려는 경우 새 git 분기를 만들고 파이프라인을 설정하여 다른 분기를 사용할 수 있습니다.  이 기능은 배포가 실패할 때 이전 버전의 코드를 테스트하여 언제 중단했는지 확인할 때 유용합니다.

   아래의 git 명령은 기존 특정 커밋 `485548e4fbafbc83b11c3cb12b035c9d26b6532b`에 대해 *testbranch1*&#x200B;이라는 원격 분기를 만듭니다.  이 특수 분기는 다른 분기에는 영향을 주지 않고 Cloud Manager에서 사용할 수 있습니다.

   `git push origin 485548e4fbafbc83b11c3cb12b035c9d26b6532b:refs/heads/testbranch1`

   자세한 내용은 [Git 설명서](https://git-scm.com/book/en/v2/Git-Internals-Git-References)를 참조하십시오.

   나중에 테스트 분기를 삭제하려면 delete 명령을 사용합니다(분명히 이 명령을 사용하여 주의).

   `git push origin --delete testbranch1`

## 5. Cloud Manager에서 전문적인 빌드가 배포되지 않지만 오류 없이 로컬에서 빌드됩니다. 디버깅하는 방법{#maven-build-fail}

자세한 내용은 [Git 리소스](https://github.com/cqsupport/cloud-manager/blob/main/cm-build-step-fails.md)를 참조하십시오.

## 6. aio cloud manager 세트 파이프라인 변수를 통해 변수를 설정할 수 없습니다. 이러한 문제를 디버깅하는 방법?{#set-variable}

아래 명령과 유사한 명령을 통해 파이프라인 변수를 나열하거나 설정할 때 403 오류가 발생하는 경우 관리 콘솔에서 *배포 관리자* 클라우드 관리자 제품 역할로 추가해야 합니다.\
자세한 내용은 [API 권한](https://www.adobe.io/apis/experiencecloud/cloud-manager/docs.html#!AdobeDocs/cloudmanager-api-docs/master/permissions.md)을 참조하십시오.

관련 명령 및 오류:

`$ aio cloudmanager:list-pipeline-variables 222`

오류: `Cannot get variables: https://cloudmanager.adobe.io/api/program/111/pipeline/222/variables (403 Forbidden)`

`$ aio cloudmanager:set-pipeline-variables 222 --variable TEST 1`

오류: `Cannot get variables: https://cloudmanager.adobe.io/api/program/111/pipeline/222/variables (403 Forbidden)`
