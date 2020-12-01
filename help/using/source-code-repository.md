---
title: 소스 코드 저장소
seo-title: Adobe AEM Cloud Manager용 소스 코드 저장소
description: 이 페이지에서 Cloud Manager에 있는 각 프로그램에 대해 제공되는 git 리포지토리에 대해 자세히 알아보십시오.
seo-description: Adobe AEM Cloud Manager에 있는 각 프로그램에 대해 제공되는 git 리포지토리에 대해 자세히 알아보려면 이 페이지를 따르십시오.
uuid: 2c42775f-8703-43f7-bad2-7dc086ea9dd7
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: requirements
discoiquuid: f90f0f4c-c1ff-47f6-8d97-ff5018561bf2
translation-type: tm+mt
source-git-commit: 697311cd00ef96568f6befd2fe76febafc27961e
workflow-type: tm+mt
source-wordcount: '279'
ht-degree: 2%

---


# 소스 코드 저장소 {#source-code-repository}

## 클라우드 관리자 저장소 {#cloud-manager-repository}

[!UICONTROL AEM Managed Services] 구독에는 Adobe에서 프로비저닝하고 관리하는 소스 코드 저장소가 포함됩니다. 각 고객의 프로그램에는 단일 및 고유한 **Git 리포지토리**&#x200B;가 지정되며, 여기에서 관련 코드가 저장되고 보안됩니다.

Cloud Manager의 Git 리포지토리는 구성된 분기나 샘플 프로젝트 없이 항상 비어 있는 것이 좋습니다. 클라우드 관리자의 Git 리포지토리를 사용하려면 Git 호환 클라이언트를 사용하여 분기를 만들고 코드를 저장 및 검색하고 커밋 내역을 나열하는 등 모든 작업을 수행할 수 있는 **개인 액세스 토큰**&#x200B;이 제공됩니다.

Git에서 분기를 설정하는 방법에 대한 자세한 내용은 [릴리스 분기 구성](configure-your-release-branches.md)을 참조하십시오.

클라우드 관리자의 **Git 리포지토리**&#x200B;를 CI/CD 파이프라인과 함께 사용하는 방법에 대한 자세한 내용은 [CI/CD 파이프라인 구성](configuring-pipeline.md)을 참조하십시오.

## 온-프레미스 저장소 {#on-premise-repository}

어떤 경우에는 기존 Git 리포지토리를 사용하고 계속 사용하려고 합니다. 이러한 경우 여러 원격 저장소에 대해 Git의 지원 기능을 사용할 수 있습니다. Git 리포지토리에서 일상적인 개발 작업이 계속 이루어집니다. 출시 분기가 프로덕션에 배포할 준비가 되면 최신 코드를 Cloud Manager의 Git 리포지토리로 푸시하고 Cloud Manager CI/CD 파이프라인을 트리거합니다.

>[!NOTE]
>
>일반적인 Git 명령을 보려면 [Git 요약서](https://education.github.com/git-cheat-sheet-education.pdf)를 참조하십시오.

