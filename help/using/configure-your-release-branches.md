---
title: 릴리스 분기 구성
seo-title: 릴리스 분기 구성
description: AEM Cloud Manager용 Git의 릴리스 분기 구성
seo-description: git에서 릴리스 분기를 구성하는 방법에 대해 알아보려면 이 페이지를 따르십시오.
uuid: d12a8b85-b7fd-4b55-a05a-a0f874ce598c
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: getting-started
discoiquuid: 53807ea6-9464-429d-9322-85c9f405dff6
translation-type: tm+mt
source-git-commit: 9c0df236c1e800802d62dea09996bb8e1e7033f7
workflow-type: tm+mt
source-wordcount: '307'
ht-degree: 3%

---


# 릴리스 분기 구성 {#configure-your-release-branches}

## Git {#setting-up-your-first-branch-in-git}에서 첫 번째 분기 설정

처음에 비어 있는 단일 Git 리포지토리가 Cloud Manager에서 온보드 각 프로그램에 대해 프로비저닝됩니다. **** 이 저장소에는 개발 프로세스에 따라 분기가 많거나 적은 수의 분기가 포함될 수 있지만 응용 프로그램 코드를 스테이지와 프로덕션에 배포하려면 CI/CD 파이프라인에서 사용하는 분기가 하나 이상 있어야 합니다. 가장 좋은 방법은 `master`을 이 분기의 이름으로 사용하는 것입니다. 편리하게 이것은 새 프로젝트를 설정할 때 Git 클라이언트의 기본 동작입니다.

예를 들어 새 프로젝트를 설정할 때 다음과 같은 명령 세트를 실행합니다.

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
>명령줄 클라이언트를 사용할 필요가 없습니다. 독립 실행형 애플리케이션으로 또는 Eclipse 또는 IntelliJ와 같은 IDE(Integrated Development Environment)의 일부로 사용할 수 있는 다양한 그래픽 Git 클라이언트가 있습니다. 클라이언트 응용 프로그램이 HTTPS를 사용하여 Git을 지원하는 경우 [!UICONTROL Cloud Manager]와 호환되어야 합니다.

## 첫 번째 분기 푸시 {#pushing-your-first-branch}

하나 이상의 개정을 완료하고 나면 [!UICONTROL Cloud Manager] 리포지토리를 **remote**&#x200B;로 추가한 다음 커밋을 해당 수정에 푸시할 수 있습니다.

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
>자격 증명과 함께 특정 URL이 [!UICONTROL Cloud Manager] 온보딩 도중 고객 성공 엔지니어링에서 제공합니다.

## 추가 분기 {#additional-branches}

단일 `master` 분기로 매우 간단한 프로젝트를 수행할 수 있지만 대부분의 경우 보다 복잡한 분기 전략을 사용해야 합니다. 많은 고객은 배포 시간이 되면 `develop`이라는 분기에서 일상적인 개발 활동이 수행되고 개발 분기는 `master` 분기로 병합되는 프로세스를 따릅니다.

>[!NOTE]
>
>일반적인 git 명령을 보려면 [Git 요약서](https://github.github.com/training-kit/downloads/github-git-cheat-sheet)를 참조하십시오.
