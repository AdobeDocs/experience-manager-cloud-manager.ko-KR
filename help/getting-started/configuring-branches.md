---
title: 분기 구성
description: Git에서 첫 번째 분기를 설정하는 방법과 CI/CD 파이프라인에서 애플리케이션 코드를 배포하는 데 어떻게 사용되는지 알아보십시오.
exl-id: ff2ae28f-902e-4fb2-aeb1-3636cb5cd9bb
source-git-commit: fb3c2b3450cfbbd402e9e0635b7ae1bd71ce0501
workflow-type: tm+mt
source-wordcount: '323'
ht-degree: 95%

---


# 분기 구성 {#configuring-branches}

Git에서 첫 번째 분기를 설정하는 방법과 CI/CD 파이프라인에서 애플리케이션 코드를 배포하는 데 어떻게 사용되는지 알아보십시오.

## Git에서 첫 분기 설정 {#setting-up-your-first-branch-in-git}

Cloud Manager에 온보딩된 각 프로그램에 대해 처음에는 비어 있던 단일 Git 저장소가 [프로비저닝됩니다](/help/requirements/environment-provisioning.md). 이 저장소에는 개발 프로세스에 필요한 만큼의 분기가 포함될 수 있지만 CI/CD 파이프라인에서 스테이징 및 프로덕션으로 애플리케이션 코드를 배포하는 데 사용되는 분기가 하나 이상 있어야 합니다. 이 분기의 이름으로 `main`을 사용하는 것이 좋습니다. 편리하게, 이 접근 방식은 새 프로젝트를 설정할 때 Git 클라이언트의 기본 비헤이비어입니다.

예를 들어 새 프로젝트를 설정할 때 다음과 유사한 명령 집합을 실행합니다.

```shell
$ git init
Initialized empty Git repository in /Users/myname/workspace/new-project/.git/
... steps which add Maven build files and source code ...
$ git add pom.xml core/pom.xml core/src ui.apps/pom.xml ui.apps/src
$ git commit -m "initial commit"
 19 files changed, 777 insertions(+)
 create mode 100644 core/pom.xml
 create mode 100644 pom.xml
 create mode 100644 ui.apps/pom.xml
 create mode 100644 ui.apps/src/main/content/META-INF/vault/config.xml
 create mode 100644 ui.apps/src/main/content/META-INF/vault/definition/.content.xml
 create mode 100644 ui.apps/src/main/content/META-INF/vault/filter.xml
 create mode 100644 ui.apps/src/main/content/META-INF/vault/nodetypes.cnd
 create mode 100644 ui.apps/src/main/content/META-INF/vault/properties.xml
 create mode 100644 ui.apps/src/main/content/jcr_root/apps/my-aem-project/install/.vltignore
 create mode 100644 ui.apps/src/main/content/jcr_root/conf/.content.xml
 create mode 100644 ui.apps/src/main/content/jcr_root/conf/my-aem-project/.content.xml
 create mode 100644 ui.apps/src/main/content/jcr_root/conf/my-aem-project/settings/.content.xml
 create mode 100644 ui.apps/src/main/content/jcr_root/conf/my-aem-project/settings/wcm/.content.xml
 create mode 100644 ui.apps/src/main/content/jcr_root/conf/my-aem-project/settings/wcm/policies/.content.xml
 create mode 100644 ui.apps/src/main/content/jcr_root/conf/my-aem-project/settings/wcm/policies/_rep_policy.xml
 create mode 100644 ui.apps/src/main/content/jcr_root/conf/my-aem-project/settings/wcm/template-types/.content.xml
 create mode 100644 ui.apps/src/main/content/jcr_root/conf/my-aem-project/settings/wcm/template-types/_rep_policy.xml
 create mode 100644 ui.apps/src/main/content/jcr_root/conf/my-aem-project/settings/wcm/templates/.content.xml
 create mode 100644 ui.apps/src/main/content/jcr_root/conf/my-aem-project/settings/wcm/templates/_rep_policy.xml
```

>[!NOTE]
>
>명령줄 클라이언트를 사용할 필요는 없습니다. 독립 실행형 애플리케이션이나 Eclipse 또는 IntelliJ와 같은 통합 개발 환경(IDE)의 일부로 사용할 수 있는 다양한 그래픽 Git 클라이언트가 있습니다. 클라이언트 애플리케이션이 HTTPS를 사용하여 Git을 지원하는 한 [!UICONTROL Cloud Manager]와 호환되어야 합니다.

## 첫 분기 푸시 {#pushing-your-first-branch}

수정본을 하나 이상 커밋했다면 [!UICONTROL Cloud Manager] 저장소를 원격으로 추가한 다음 커밋을 푸시할 수 있습니다.

```shell
$ git remote add adobe <url>
$ git push adobe master
Counting objects: 36, done.
Delta compression using up to 8 threads.
Compressing objects: 100% (27/27), done.
Writing objects: 100% (36/36), 7.31 KiB | 1.83 MiB/s, done.
Total 36 (delta 6), reused 0 (delta 0)
To <url>
 * [new branch]      main -> main
```

>[!NOTE]
>
>특정 URL은 Adobe CSE(고객 성공 엔지니어)에서 [!UICONTROL Cloud Manager] 온보딩 중에 자격 증명과 함께 제공됩니다.

## 추가 분기 {#additional-branches}

매우 간단한 프로젝트에는 `main` 분기 하나로 충분할 수 있지만 대부분의 경우 보다 복잡한 분기 전략이 필요합니다. 많은 고객이 `develop`이라고 불리는 분기에서 일상적인 개발 활동을 수행하는 프로세스를 따릅니다. 그런 다음 배포 시간이 되면 `develop` 분기가 `main` 분기로 병합됩니다.

>[!TIP]
>
>일반적인 Git 명령을 보려면 [Git 치트 시트](https://training.github.com/downloads/github-git-cheat-sheet)를 참조하십시오.
