---
title: 소스 코드 저장소
seo-title: AEM Cloud Manager를 위한 소스 코드 저장소
description: Cloud Manager에 있는 각 프로그램에 대해 프로비저닝된 Git 리포지토리에 대해 알려면 이 페이지를 따르십시오.
seo-description: Adobe AEM Cloud Manager에 있는 각 프로그램에 대해 프로비저닝된 Git 리포지토리에 대해 알려면 이 페이지를 따르십시오.
uuid: 2c42775f-8703-43f7-bad2-7dc086ea9dd7
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: requirements
discoiquuid: f90f0f4c-c1ff-47f6-8d97-ff5018561bf2
feature: 프로비저닝
exl-id: af551e33-3623-4fcd-8d25-4362d8871411
source-git-commit: 43bb3c477ef9c1ce178509b8180479d7616edc66
workflow-type: tm+mt
source-wordcount: '280'
ht-degree: 2%

---

# 소스 코드 저장소 {#source-code-repository}

## Cloud Manager 저장소 {#cloud-manager-repository}

[!UICONTROL AEM Managed Services] 구독에는 Adobe이 프로비저닝하고 관리하는 소스 코드 저장소가 포함됩니다. 각 고객의 프로그램에는 하나의 고유한 **Git 리포지토리**&#x200B;가 할당됩니다. 여기서 연관된 코드가 저장되고 보안됩니다.

가장 좋은 방법은 항상 Cloud Manager의 Git 리포지토리를 사용해야 하며, 구성 또는 샘플 프로젝트 없이 비어 있습니다. Cloud Manager의 Git 리포지토리를 사용하려면 Git 호환 클라이언트를 사용하여 분기를 만들고, 코드를 저장하고, 검색하고, 커밋 내역을 나열하는 등 작업을 수행할 수 있는 **개인 액세스 토큰**&#x200B;이 제공됩니다.

Git에서 분기를 설정하는 방법에 대한 자세한 내용은 [릴리스 분기 구성](configure-your-release-branches.md) 을 참조하십시오.

Cloud Manager의 **Git 리포지토리**&#x200B;를 CI/CD 파이프라인과 함께 사용하는 방법에 대한 자세한 내용은 [CI/CD 파이프라인 구성](configuring-pipeline.md)을 참조하십시오.

## 온-프레미스 저장소 {#on-premise-repository}

경우에 따라 기존 Git 리포지토리가 있으며 계속 사용하려고 합니다. 이러한 경우 여러 원격 리포지토리에 Git의 지원 기능을 사용할 수 있습니다. 일상적인 개발은 Git 리포지토리에서 계속 발생합니다. 릴리스 분기가 프로덕션에 배포할 준비가 되면 최신 코드를 Cloud Manager의 Git 리포지토리에 푸시하고 Cloud Manager CI/CD 파이프라인을 트리거합니다.

>[!NOTE]
>
>일반적인 Git 명령을 보려면 [Git 치트 시트](https://education.github.com/git-cheat-sheet-education.pdf)를 참조하십시오.
