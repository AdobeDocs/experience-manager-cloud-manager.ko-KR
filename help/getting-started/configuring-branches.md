---
title: 분기 구성
description: Git에서 첫 번째 분기를 설정하는 방법과 CI/CD 파이프라인에서 애플리케이션 코드를 배포하는 데 이 분기를 사용하는 방법을 알아봅니다.
exl-id: ff2ae28f-902e-4fb2-aeb1-3636cb5cd9bb
source-git-commit: 4c051cd1696f8a00d0278131c9521ad4dcb956a3
workflow-type: tm+mt
source-wordcount: '323'
ht-degree: 0%

---


# 분기 구성 {#configuring-branches}

Git에서 첫 번째 분기를 설정하는 방법과 CI/CD 파이프라인에서 애플리케이션 코드를 배포하는 데 이 분기를 사용하는 방법을 알아봅니다.

## Git에서 첫 번째 분기 설정 {#setting-up-your-first-branch-in-git}

처음에 비어 있는 단일 Git 리포지토리 [프로비저닝됨](/help/requirements/environment-provisioning.md) Cloud Manager에서 온보딩된 각 프로그램에 대해 이 저장소는 개발 프로세스에 필요한 만큼 분기를 포함할 수 있지만 스테이지와 프로덕션에 애플리케이션 코드를 배포하려면 CI/CD 파이프라인에서 사용하는 분기가 하나 이상 있어야 합니다. 가장 좋은 방법은 `main` 이 분기의 이름으로 사용됩니다. 새로운 프로젝트를 설정할 때 편리하게 Git 클라이언트의 기본 동작입니다.

예를 들어 새 프로젝트를 설정할 때 다음과 유사한 명령 세트가 실행됩니다.

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
>명령줄 클라이언트를 사용할 필요는 없습니다. 독립형 애플리케이션으로 또는 Eclipse 또는 IntelliJ와 같은 IDE(통합 개발 환경)의 일부로 사용할 수 있는 다양한 그래픽 Git 클라이언트가 있습니다. 클라이언트 애플리케이션이 HTTPS를 사용하여 git을 지원하는 한 와 호환되어야 합니다. [!UICONTROL Cloud Manager].

## 첫 번째 분기 밀어넣기 {#pushing-your-first-branch}

하나 이상의 개정을 커밋한 후에는 [!UICONTROL Cloud Manager] 리포지토리를 원격으로 만든 다음 커밋을 푸시합니다.

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
>자격 증명과 함께 특정 URL은 다음 기간 동안 고객 성공 엔지니어링 센터에서 제공합니다 [!UICONTROL Cloud Manager] 온보딩.

## 추가 분기 {#additional-branches}

단일 `main` 분기로 하면 아주 간단한 프로젝트로 충분하지만, 대부분의 경우에는 더 복잡한 분기 전략이 필요하다. 많은 고객이 `develop` 개발 분기는 `main` 배포할 시간일 때 분기합니다.

>[!TIP]
>
>일반적인 git 명령을 보려면 [Git 치트 시트](https://github.github.com/training-kit/downloads/github-git-cheat-sheet).
