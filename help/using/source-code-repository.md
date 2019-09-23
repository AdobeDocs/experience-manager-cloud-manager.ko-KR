---
title: 소스 코드 저장소
seo-title: Adobe AEM Cloud Manager용 소스 코드 저장소
description: 이 페이지에서 Cloud Manager에 있는 각 프로그램에 대해 제공된 git 리포지토리에 대해 알아보십시오.
seo-description: 이 페이지에서 Adobe AEM Cloud Manager에 있는 각 프로그램에 대해 제공된 git 리포지토리에 대해 알아보십시오.
uuid: 2c42775f-8703-43f7-bad2-7dc086ea9dd7
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: 요구 사항
discoiquuid: f90f0f4c-c1ff-47f6-8d97-ff5018561bf2
translation-type: tm+mt
source-git-commit: 697311cd00ef96568f6befd2fe76febafc27961e

---


# 소스 코드 저장소 {#source-code-repository}

## Cloud Manager 저장소 {#cloud-manager-repository}

사용자의 [!UICONTROL AEM Managed Services] 구독에는 Adobe에서 프로비저닝하고 관리하는 소스 코드 저장소가 포함됩니다. 각 고객의 프로그램에는 하나의 고유한 **Git**&#x200B;저장소가 할당되며, 여기에서 관련 코드를 저장하고 보호할 수 있습니다.

가장 좋은 방법은 Cloud Manager의 Git 리포지토리를 항상 사용하는 것입니다. 단, 구성된 분기 또는 샘플 프로젝트 없이도 비어 있는 상태로 표시됩니다. Cloud Manager의 Git 리포지토리를 사용하려면 Git 호환 클라이언트를 사용하여 분기를 만들고 코드를 저장 및 검색하며 커밋 기록 등을 나열할 수 있는 **개인 액세스 토큰이** 제공됩니다.

Git에서 분기를 설정하는 방법에 대한 자세한 내용은 릴리스 [분기 구성을 참조하십시오](configure-your-release-branches.md).

Cloud Manager의 Git 리포지토리를 CI/CD **파이프라인과** 함께 사용하는 방법에 대한 자세한 내용은 CI/CD [파이프라인](configuring-pipeline.md)구성을 참조하십시오.

## 온-프레미스 저장소 {#on-premise-repository}

경우에 따라 기존 Git 리포지토리를 사용하고 계속 사용하려고 합니다. 이러한 경우 여러 원격 리포지토리에 Git의 지원 기능을 사용할 수 있습니다. 일상적인 개발 작업은 Git 리포지토리에서 계속 진행됩니다. 릴리스 분기가 프로덕션에 배포할 준비가 되면 최신 코드를 Cloud Manager의 Git 리포지토리로 푸시하고 Cloud Manager CI/CD 파이프라인을 트리거합니다.

>[!NOTE]
>
>일반적인 Git 명령을 보려면 Git 요약서를 [참조하십시오](https://education.github.com/git-cheat-sheet-education.pdf).

