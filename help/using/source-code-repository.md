---
title: 소스 코드 저장소
seo-title: Adobe AEM 클라우드 관리자를 위한 소스 코드 저장소
description: 클라우드 관리자에서 제공하는 각 프로그램에 대해 제공되는 Git 리포지토리에 대해 알아보려면 이 페이지를 따르십시오.
seo-description: Adobe AEM 클라우드 관리자에서 제공하는 각 프로그램에 대해 제공되는 Git 리포지토리에 대해 알려면 이 페이지를 따르십시오.
uuid: 2 C 42775 F -8703-43 F 7-Bad 2-7 DC 086 EA 9 DD 7
contentOwner: Jsyal
products: sg_ Experiencemanager/Cloudmanager
topic-tags: 요구 사항
discoiquuid: f 90 f 0 f 4 c-c 1 ff -47 f 6-8 d 97-ff 5018561 bf 2
translation-type: tm+mt
source-git-commit: 1dfb065c09569f811e5a006d3d74825d3bd7cc8d

---


# 소스 코드 저장소 {#source-code-repository}

## Cloud Manager 저장소 {#cloud-manager-repository}

사용료 지불 옵션에는 [!UICONTROL AEM Managed Services] Adobe에서 제공하고 관리하는 소스 코드 저장소가 포함됩니다. 각 고객의 프로그램에는 관련 코드가 저장되고 보안이 적용되는 **단일 Git 리포지토리가**할당됩니다.

별도의 분기 또는 샘플 프로젝트를 거치지 않고 비어 있는 클라우드 관리자의 Git 리포지토리를 항상 사용해야 합니다. 클라우드 관리자의 Git 리포지토리를 사용하려면 모든 Git 호환 클라이언트를 사용하여 분기를 만들고, 코드를 저장 및 검색하고, 커밋 내역을 나열할 **수** 있는 개인 액세스 토큰이 제공됩니다.

Git에서 분기를 설정하는 방법에 대한 자세한 내용은 릴리스 분기 [구성을](configure-your-release-branches.md)참조하십시오.

CI/CD 파이프라인과 함께 Cloud Manager의 **Git 리포지토리를** 사용하는 방법에 대한 자세한 내용은 CI/CD 파이프라인 [구성을](configuring-pipeline.md)참조하십시오.

## 온프레미스 저장소 {#on-premise-repository}

경우에 따라 기존 Git 리포지토리를 사용하고 계속 사용할 수 있습니다. 이러한 경우 여러 원격 리포지토리에 Git에서 지원되는 기능을 사용할 수 있습니다. Git 저장소에서는 일상적인 개발 과정이 계속 진행됩니다. 배포 분기가 프로덕션에 배포할 준비가 되면 최신 코드를 클라우드 관리자의 Git 리포지토리로 푸시하고 클라우드 관리자 CI/CD 파이프라인을 트리거합니다.

>[!NOTE]
>
>일반적인 Git 명령을 보려면 [Git 요약서를](https://education.github.com/git-cheat-sheet-education.pdf)참조하십시오.

