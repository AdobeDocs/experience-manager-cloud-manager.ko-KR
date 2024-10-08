---
title: 소스 코드 저장소
description: Cloud Manager에서 보유하고 있는 각 프로그램에 대해 프로비저닝된 Git 저장소에 대해 알아보십시오.
exl-id: af551e33-3623-4fcd-8d25-4362d8871411
source-git-commit: 984269e5fe70913644d26e759fa21ccea0536bf4
workflow-type: ht
source-wordcount: '245'
ht-degree: 100%

---


# 소스 코드 저장소 {#source-code-repository}

Cloud Manager에서 보유하고 있는 각 프로그램에 대해 프로비저닝된 Git 저장소에 대해 알아보십시오.

## Cloud Manager 저장소 {#cloud-manager-repository}

[!UICONTROL AEM Managed Services] 구독에는 Adobe에서 프로비저닝하고 관리하는 소스 코드 저장소가 포함되어 있습니다. 각 프로그램에는 연결된 코드가 저장되고 보호되는 단일 고유 Git 저장소가 할당됩니다.

항상 Cloud Manager의 Git 저장소를 사용해야 합니다. 이 저장소는 분기 구성이나 샘플 프로젝트 없이 빈 상태로 제공됩니다. Cloud Manager는 Git 저장소에 대한 개인 액세스 토큰을 제공하여 Git 클라이언트를 사용한 분기를 만들고 코드를 관리하고 커밋 기록을 검색하는 등의 작업을 수행할 수 있습니다.

Git에서 분기를 설정하는 방법에 대한 자세한 내용은 [릴리스 분기 구성](/help/getting-started/configuring-branches.md)을 참조하십시오.

Cloud Manager의 Git 저장소를 CI/CD 파이프라인과 함께 사용하는 방법에 대한 자세한 내용은 [프로덕션 파이프라인 구성](/help/using/production-pipelines.md) 및 [비프로덕션 파이프라인 구성](/help/using/non-production-pipelines.md)을 참조하십시오.

## On-Premise 저장소 {#on-premise-repository}

기존 Git 저장소가 있을 수 있으며 이 경우 여러 원격 저장소에 Git 기능을 사용할 수 있습니다. 일상적인 개발은 Git 저장소에서 계속 발생합니다. 릴리스 분기가 프로덕션 환경에 배포할 준비가 되면 Cloud Manager의 Git 저장소에 최신 코드를 푸시하고 Cloud Manager CI/CD 파이프라인을 트리거할 수 있습니다.

일반적인 Git 명령을 보려면 [Git 치트 시트](https://education.github.com/git-cheat-sheet-education.pdf)를 참조하십시오.
