---
title: 소스 코드 저장소
seo-title: Adobe AEM Cloud Manager용 소스 코드 저장소
description: Cloud Manager에 있는 각 프로그램에 대해 프로비저닝된 git 리포지토리에 대해 알려면 이 페이지를 따르십시오.
seo-description: Adobe AEM Cloud Manager에 있는 각 프로그램에 대해 프로비저닝된 git 리포지토리에 대해 알려면 이 페이지를 따르십시오.
uuid: 2c42775f-8703-43f7-bad2-7dc086ea9dd7
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: requirements
discoiquuid: f90f0f4c-c1ff-47f6-8d97-ff5018561bf2
feature: Provisioning
translation-type: tm+mt
source-git-commit: fb10d775c930b5bb475b497aac2fd59b053a9a00
workflow-type: tm+mt
source-wordcount: '280'
ht-degree: 2%

---


# 소스 코드 저장소 {#source-code-repository}

## 클라우드 관리자 저장소 {#cloud-manager-repository}

[!UICONTROL AEM Managed Services] 구독에는 Adobe에서 프로비저닝하고 관리하는 소스 코드 저장소가 포함됩니다. 각 고객의 프로그램은 단일 및 고유한 **Git 리포지토리**&#x200B;에 할당되며, 여기서 연결된 코드는 저장 및 보관됩니다.

가장 좋은 방법은 Cloud Manager의 Git 리포지토리를 항상 사용해야 합니다. 이때 분기가 구성되거나 샘플 프로젝트가 없으면 비어 있습니다. 클라우드 관리자의 Git 리포지토리를 사용하려면 Git 호환 클라이언트를 사용하여 분기 생성, 코드 저장 및 검색, 커밋 기록 목록 지정 등을 위해 **개인 액세스 토큰**&#x200B;이 제공됩니다.

Git에서 분기를 설정하는 방법에 대한 자세한 내용은 [릴리스 분기 구성](configure-your-release-branches.md)을 참조하십시오.

클라우드 관리자의 **Git 리포지토리**&#x200B;를 CI/CD 파이프라인과 함께 사용하는 방법에 대한 자세한 내용은 [CI/CD 파이프라인 구성](configuring-pipeline.md)을 참조하십시오.

## 온-프레미스 저장소 {#on-premise-repository}

경우에 따라 기존 Git 리포지토리가 있고 계속 사용하려고 합니다. 이러한 경우 여러 원격 리포지토리에 Git의 지원 기능을 사용할 수 있습니다. Git 리포지토리에서 일상적인 개발 작업이 계속 진행됩니다. 출시 분기가 프로덕션에 배포할 준비가 되면 최신 코드를 Cloud Manager의 Git 리포지토리로 푸시하고 Cloud Manager CI/CD 파이프라인을 트리거합니다.

>[!NOTE]
>
>일반적인 Git 명령을 보려면 [Git 요약서](https://education.github.com/git-cheat-sheet-education.pdf)를 참조하십시오.

