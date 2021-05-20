---
title: Cloud Manager와 Git 통합
description: Cloud Manager를 통해 고객 관리(온-프레미스) git 리포지토리의 설정 및 통합을 거치는 비디오 시리즈입니다.
seo-title: Cloud Manager와 Git 통합
seo-description: Cloud Manager를 통해 고객 관리(온-프레미스) git 리포지토리의 설정 및 통합을 거치는 비디오 시리즈입니다.
feature: Git 리포지토리
exl-id: e517f8a4-23f0-4486-8278-91396dba76ec
source-git-commit: 43bb3c477ef9c1ce178509b8180479d7616edc66
workflow-type: tm+mt
source-wordcount: '405'
ht-degree: 5%

---

# Cloud Manager와 Git 통합

Adobe Cloud Manager에는 Cloud Manager의 CI/CD 파이프라인을 사용하여 코드를 배포하는 데 사용되는 단일 git 리포지토리가 제공됩니다. 고객은 Cloud Manager의 git 리포지토리를 즉시 사용할 수 있습니다. 또한 고객은 온-프레미스 또는 **고객 관리** git 리포지토리를 Cloud Manager와 통합할 수 있습니다.

## Git 통합 개요

>[!VIDEO](https://video.tv.adobe.com/v/28710/)

이 비디오 시리즈는 다음을 포함하여 고객 관리 Git 리포지토리와 Cloud Manager를 통합할 때 다음과 같은 몇 가지 사용 사례를 설명합니다.

* [초기 동기화](#initial-sync)
* [기본 분기 전략](#branching-strategy)
* [기능 분기 개발](#feature-development)
* [프로덕션 배포](#production-deployment)
* [릴리스 태그 동기화](#sync-tags)

전체 개요를 보려면 [Cloud Manager 사용 안내서](https://docs.adobe.com/content/help/ko-KR/experience-manager-cloud-manager/using/introduction-to-cloud-manager.html)를 검토하십시오. 이 비디오 시리즈는 Git 및 소스 제어 관리에 대한 기본적인 지식을 제공합니다. git에 대한 자세한 내용은 ](#additional-resources) 아래의 [추가 리소스를 참조하십시오.

>[!NOTE]
>
> 이 비디오 시리즈에 설명된 단계 및 이름 지정 규칙은 고객 관리 Git 리포지토리 및 Cloud Manager를 사용하기 위한 몇 가지 우수 사례를 나타냅니다. 표시된 규칙 및 워크플로우가 개별 개발 팀에 맞게 조정될 것으로 예상됩니다.

## 초기 동기화 {#initial-sync}

고객 관리 Git 리포지토리를 Cloud Manager의 Git 리포지토리와 동기화하는 첫 번째 단계입니다.

>[!VIDEO](https://video.tv.adobe.com/v/28711/?quality=12)

## 기본 분기 전략 {#branching-strategy}

Cloud Manager의 [프로덕션 및 비프로덕션 파이프라인](https://docs.adobe.com/content/help/en/experience-manager-cloud-manager/using/how-to-use/configuring-pipeline.html)을 활용하려면 기본 분기 전략을 설정하십시오.

>[!VIDEO](https://video.tv.adobe.com/v/28712/?quality=12)

## 기능 분기 개발 {#feature-development}

기능 분기를 사용하여 고객 관리 git 리포지토리에서 코드 변경 사항을 분리하고 코드 품질 및 유효성 검사 테스트를 위해 비프로덕션 파이프라인을 사용하기 위해 Cloud Manager의 git 리포지토리와 동기화합니다.

>[!VIDEO](https://video.tv.adobe.com/v/28723/?quality=12)

## 프로덕션 배포 {#production-deployment}

스테이지 및 프로덕션 환경에 배포하기 위해 고객 관리 Git 리포지토리에서 프로덕션 릴리스를 위한 코드를 준비하고 Cloud Manager의 git 리포지토리와 동기화합니다.

>[!VIDEO](https://video.tv.adobe.com/v/28724/?quality=12)

## 릴리스 태그 동기화 {#sync-tags}

단계 및 프로덕션 환경에 배포된 코드에 대한 가시성을 제공하기 위해 Cloud Manager git 리포지토리의 릴리스 태그를 고객 관리 Git 리포지토리에 동기화합니다.

>[!VIDEO](https://video.tv.adobe.com/v/28725/?quality=12)

## 추가 리소스 {#additional-resources}

* [Cloud Manager 설명서](https://docs.adobe.com/content/help/en/experience-manager-cloud-manager/using/introduction-to-cloud-manager.html)
* [GitHub 리소스](https://try.github.io)
* [Atlassian Git Tutorials](https://www.atlassian.com/git/tutorials/what-is-version-control)
* [Git 치트 시트](https://education.github.com/git-cheat-sheet-education.pdf)
