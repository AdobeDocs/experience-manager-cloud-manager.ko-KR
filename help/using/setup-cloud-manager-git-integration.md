---
title: Adobe Cloud Manager와 Git 통합
description: Adobe Cloud Manager와 고객 관리(온-프레미스) git 리포지토리의 설정 및 통합을 살펴보는 비디오 시리즈입니다.
seo-title: Adobe Cloud Manager와 Git 통합
seo-description: Adobe Cloud Manager와 고객 관리(온-프레미스) git 리포지토리의 설정 및 통합을 살펴보는 비디오 시리즈입니다.
translation-type: tm+mt
source-git-commit: 519f43ff16e0474951f97798a8e070141e5c124b

---


# Adobe Cloud Manager와 Git 통합

Adobe Cloud Manager는 Cloud Manager의 CI/CD 파이프라인을 사용하여 코드를 배포하는 데 사용되는 단일 Git 리포지토리와 함께 제공됩니다. 고객은 즉시 Cloud Manager의 git 리포지토리를 사용할 수 있습니다. 또한 고객은 온-프레미스 또는 **고객 관리** Git 리포지토리를 Cloud Manager와 통합할 수 있습니다.

## Git 통합 개요

>[!VIDEO](https://video.tv.adobe.com/v/28710/?captions=kor)

이 비디오 시리즈에서는 다음을 비롯하여 고객 관리 Git 리포지토리를 Cloud Manager와 통합하는 데 있어 여러 가지 사용 사례를 소개합니다.

* [초기 동기화](#initial-sync)
* [기본 분기 전략](#branching-strategy)
* [기능 분기 개발](#feature-development)
* [프로덕션 배포](#production-deployment)
* [릴리스 태그 동기화](#sync-tags)

전체 개요를 보려면 Cloud Manager [사용 안내서를 참조하십시오](https://docs.adobe.com/content/help/en/experience-manager-cloud-manager/using/introduction-to-cloud-manager.html). 이 비디오 시리즈에서는 git 및 소스 제어 관리에 대한 기본적인 지식을 보유하고 있습니다. git에 대한 자세한 내용은 아래 [추가 리소스를](#additional-resources) 참조하십시오.

>[!NOTE]
>
> 이 비디오 시리즈에서 설명한 단계 및 이름 지정 규칙은 고객 관리 Git 리포지토리 및 Cloud Manager를 사용하여 작업하기 위한 몇 가지 모범 사례를 보여줍니다. 묘사된 규칙과 워크플로우는 개별 개발 팀에 맞게 조정될 것으로 예상됩니다.

## 초기 동기화 {#initial-sync}

고객 관리 Git 리포지토리를 Cloud Manager의 Git 리포지토리와 동기화하는 첫 번째 단계입니다.

>[!VIDEO](https://video.tv.adobe.com/v/28711/?quality=12&captions=kor)

## 기본 분기 전략 {#branching-strategy}

Cloud Manager의 [프로덕션 및 비프로덕션 파이프라인을](https://docs.adobe.com/content/help/en/experience-manager-cloud-manager/using/how-to-use/configuring-pipeline.html)활용하려면 기본 분기 전략을 설정합니다.

>[!VIDEO](https://video.tv.adobe.com/v/28712/?quality=12&captions=kor)

## 기능 분기 개발 {#feature-development}

기능 분기를 사용하여 고객 관리 git 리포지토리에서 코드 변경 내용을 분리하고 Cloud Manager의 git 리포지토리와 동기화하여 코드 품질 및 유효성 검사 테스트를 위한 비프로덕션 파이프라인을 사용할 수 있습니다.

>[!VIDEO](https://video.tv.adobe.com/v/28723/?quality=12&captions=kor)

## 프로덕션 배포 {#production-deployment}

스테이지와 프로덕션 환경에 배포할 수 있도록 고객 관리 Git 리포지토리에서 프로덕션 릴리스의 코드를 준비하고 Cloud Manager의 git 리포지토리와 동기화합니다.

>[!VIDEO](https://video.tv.adobe.com/v/28724/?quality=12&captions=kor)

## 릴리스 태그 동기화 {#sync-tags}

스테이지와 프로덕션 환경에 배포된 코드에 대한 가시성을 제공하기 위해 Cloud Manager Git 리포지토리의 릴리스 태그를 고객이 관리하는 Git 리포지토리에 동기화합니다.

>[!VIDEO](https://video.tv.adobe.com/v/28725/?quality=12&captions=kor)

## 추가 리소스 {#additional-resources}

* [Cloud Manager 설명서](https://docs.adobe.com/content/help/en/experience-manager-cloud-manager/using/introduction-to-cloud-manager.html)
* [GitHub 리소스](https://try.github.io)
* [Atlasian Git 튜토리얼](https://www.atlassian.com/git/tutorials/what-is-version-control)
* [Git 요약서](https://education.github.com/git-cheat-sheet-education.pdf)