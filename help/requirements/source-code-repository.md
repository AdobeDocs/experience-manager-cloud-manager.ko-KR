---
title: 소스 코드 저장소
description: Cloud Manager에 있는 각 프로그램에 대해 프로비저닝된 Git 리포지토리에 대해 알아봅니다.
exl-id: af551e33-3623-4fcd-8d25-4362d8871411
source-git-commit: 6572c16aea2c5d2d1032ca5b0f5d75ade65c3a19
workflow-type: tm+mt
source-wordcount: '264'
ht-degree: 2%

---


# 소스 코드 저장소 {#source-code-repository}

Cloud Manager에 있는 각 프로그램에 대해 프로비저닝된 Git 리포지토리에 대해 알아봅니다.

## Cloud Manager 저장소 {#cloud-manager-repository}

사용자 [!UICONTROL AEM Managed Services] 구독에는 Adobe이 프로비저닝하고 관리하는 소스 코드 저장소가 포함되어 있습니다. 각 프로그램에는 연결된 코드가 저장되고 보안되는 하나의 고유한 Git 리포지토리가 할당됩니다.

가장 좋은 방법은 항상 Cloud Manager의 git 리포지토리를 사용해야 하며, 구성 또는 샘플 프로젝트 없이 비어 있습니다. Cloud Manager의 Git 리포지토리를 사용하려면 git 클라이언트를 사용하여 분기를 만들고, 코드를 저장하고, 검색하고, 커밋 내역을 나열하는 등의 작업을 수행할 수 있는 개인 액세스 토큰이 제공됩니다.

Git에서 분기를 설정하는 방법에 대한 자세한 내용은 다음을 참조하십시오 [릴리스 분기 구성](/help/getting-started/configuring-branches.md)

Cloud Manager의 git 리포지토리를 CI/CD 파이프라인과 함께 사용하는 방법에 대한 자세한 내용은 문서를 참조하십시오 [프로덕션 파이프라인 구성](/help/using/production-pipelines.md) 및 [비프로덕션 파이프라인 구성](/help/using/non-production-pipelines.md) 추가 정보

## On-Premise 저장소 {#on-premise-repository}

기존 Git 리포지토리가 있고 계속 사용하려고 할 수 있습니다. 이 경우 여러 원격 리포지토리에 Git의 기능을 사용할 수 있습니다. 일상적인 개발은 Git 리포지토리에서 계속 발생합니다. 릴리스 분기가 프로덕션에 배포할 준비가 되면 최신 코드를 Cloud Manager의 git 저장소에 푸시하고 Cloud Manager CI/CD 파이프라인을 트리거할 수 있습니다.

일반적인 git 명령을 보려면 [Git 치트 시트](https://education.github.com/git-cheat-sheet-education.pdf) ( GitHub 웹 사이트 참조).
