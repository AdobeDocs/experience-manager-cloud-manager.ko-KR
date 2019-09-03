---
title: 릴리스 분기 구성
seo-title: 릴리스 분기 구성
description: AEM 클라우드 관리자를 위한 Git에서 릴리스 분기 구성
seo-description: Git에서 릴리스 분기를 구성하는 방법에 대해 알려면 이 페이지를 따르십시오.
uuid: d 12 a 8 b 85-b 7 fd -4 b 55-a 05 a-a 0 f 874 ce 598 c
contentOwner: Jsyal
products: sg_ Experiencemanager/Cloudmanager
topic-tags: Getting-Started
discoiquuid: 53807 EA 6-9464-429 D -9322-85 C 9 F 405 DFF 6
translation-type: tm+mt
source-git-commit: 9c0df236c1e800802d62dea09996bb8e1e7033f7

---


# 릴리스 분기 구성 {#configure-your-release-branches}

## Git에서 첫 번째 분기 설정 {#setting-up-your-first-branch-in-git}

초기에 빈 **Git 리포지토리는** 클라우드 관리자에서 온보딩된 각 프로그램에 대해 제공됩니다. 이 저장소에는 개발 프로세스에 따른 분기가 많거나 몇 개 이상 포함될 수 있지만, CI/CD 파이프라인에서 스테이지 및 프로덕션에 애플리케이션 코드를 배포하는 데 사용되는 분기가 하나 이상 있어야 합니다. 이 분기의 이름으로 사용하는 `master` 것이 가장 좋습니다. 편리하게 새 프로젝트를 설정할 때 Git 클라이언트의 기본 동작입니다.

예를 들어 새 프로젝트를 설정할 때 다음과 같이 명령 세트를 실행합니다.

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
>명령줄 클라이언트를 사용해야 하는 것은 아닙니다. 독립 실행형 애플리케이션이나 Eclipse 또는 intellij와 같은 IDE (Integrated Development Environment) 의 일부로 사용할 수 있는 다양한 그래픽 Git 클라이언트가 있습니다. 클라이언트 애플리케이션이 HTTPS를 사용하여 Git를 지원하는 한과 호환되어야 [!UICONTROL Cloud Manager]합니다.

## 첫 번째 분기 푸시 {#pushing-your-first-branch}

한 번 이상의 개정판을 작성한 후에는 [!UICONTROL Cloud Manager] 저장소를 **원격** 저장소로 추가한 다음 커밋을 푸시할 수 있습니다.

```shell
$ git remote add adobe <url>
$ git push adobe master
Counting objects: 36, done.
Delta compression using up to 8 threads.
Compressing objects: 100% (27/27), done.
Writing objects: 100% (36/36), 7.31 KiB | 1.83 MiB/s, done.
Total 36 (delta 6), reused 0 (delta 0)
To <url>
 * [new branch]      master -> master
```

>[!NOTE]
>
>자격 증명과 함께 특정 URL는 온보딩 동안 [!UICONTROL Cloud Manager] 고객 성공 엔지니어링을 통해 제공됩니다.

## 추가 분기 {#additional-branches}

`master` 단일 분기는 매우 간단한 프로젝트에는 충분할 수 있지만 대부분의 경우 더 복잡한 분기 전략이 필요합니다. 많은 고객들은 분기별로 개발 활동이 수행되고 `develop` 배포 시점이 배포 시 `master` 분기에 병합되는 프로세스를 따릅니다.

>[!NOTE]
>
>일반적인 Git 명령을 보려면 [Git 요약서를](https://github.github.com/training-kit/downloads/github-git-cheat-sheet)참조하십시오.
