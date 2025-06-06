---
title: Adobe Cloud Manager와 Git 통합
description: 이 비디오 시리즈는 Adobe Cloud Manager와 함께 고객 관리(On-Premise) Git 저장소를 설정하고 통합하는 과정을 안내합니다.
exl-id: e517f8a4-23f0-4486-8278-91396dba76ec
source-git-commit: 51bd685a17eb9d68b1ec8245e6167cab02101fc1
workflow-type: ht
source-wordcount: '331'
ht-degree: 100%

---


# Adobe Cloud Manager와 Git 통합

Adobe Cloud Manager는 Cloud Manager의 CI/CD 파이프라인을 사용하여 코드를 배포하는 데 사용되는 단일 Git 저장소와 함께 제공됩니다. Cloud Manager의 Git 저장소를 즉시 사용할 수 있으며 또한 On-Premise 또는 고객 관리 Git 저장소를 Cloud Manager와 통합하는 옵션도 있습니다.

## Git 통합 개요

>[!VIDEO](https://video.tv.adobe.com/v/31279?captions=kor)

이 비디오 시리즈에서는 고객 관리 Git 저장소를 Cloud Manager와 통합에 관한 여러 사용 사례를 살펴봅니다.

* [최초 동기화](#initial-sync)
* [기본 분기 전략](#branching-strategy)
* [기능 분기 개발](#feature-development)
* [프로덕션 배포](#production-deployment)
* [릴리스 태그 동기화](#sync-tags)

이 비디오 시리즈는 Git 및 소스 제어 관리에 대한 기본 지식이 있다고 가정합니다. Git에 대한 자세한 내용은 [아래의 추가 리소스](#additional-resources)를 참조하십시오.

이 비디오 시리즈에 설명된 단계 및 명명 규칙은 고객 관리 Git 저장소와 Cloud Manager를 사용하기 위한 몇 가지 모범 사례를 나타냅니다. 표시된 규칙과 워크플로는 개별 개발 팀에 맞게 조정되어야 합니다.

Cloud Manager에 대한 전체 개요는 [Cloud Manager 소개](/help/introduction.md)를 참조하십시오.

## 최초 동기화 {#initial-sync}

고객 관리 Git 저장소를 Cloud Manager의 Git 저장소와 동기화하는 첫 번째 단계입니다.

>[!VIDEO](https://video.tv.adobe.com/v/31278/?quality=12&captions=kor)

## 기본 분기 전략 {#branching-strategy}

Cloud Manager의 [프로덕션](/help/using/production-pipelines.md) 및 [비프로덕션 파이프라인](/help/using/non-production-pipelines.md)을 활용하기 위해 기본 분기 전략을 설정합니다.

>[!VIDEO](https://video.tv.adobe.com/v/31277/?quality=12&captions=kor)

## 기능 분기 개발 {#feature-development}

기능 분기를 사용하여 고객 관리 Git 저장소에서 코드 변경 사항을 격리하고 Cloud Manager의 Git 저장소와 동기화하여 비프로덕션 파이프라인을 통해 코드 품질 및 유효성 검사 테스트를 수행합니다.

>[!VIDEO](https://video.tv.adobe.com/v/31276/?quality=12&captions=kor)

## 프로덕션 배포 {#production-deployment}

고객 관리 Git 저장소에서 프로덕션 릴리스용 코드를 준비하고 Cloud Manager의 Git 저장소와 동기화하여 스테이징 및 프로덕션 환경에 배포합니다.

>[!VIDEO](https://video.tv.adobe.com/v/31275/?quality=12&captions=kor)

## 릴리스 태그 동기화 {#sync-tags}

릴리스 태그를 Cloud Manager Git 저장소에서 고객 관리 Git 저장소와 동기화할 수 있습니다. 이 기능을 사용하면 스테이징 및 프로덕션 환경 모두에 배포된 코드를 파악할 수 있습니다.

>[!VIDEO](https://video.tv.adobe.com/v/31274/?quality=12&captions=kor)

## 추가 리소스 {#additional-resources}

* [Cloud Manager 소개](/help/introduction.md)
* [GitHub 리소스](https://docs.github.com/en/get-started/getting-started-with-git/set-up-git)
* [Atlassian Git 튜토리얼](https://www.atlassian.com/git/tutorials/what-is-version-control)
* [Git 치트 시트](https://education.github.com/git-cheat-sheet-education.pdf)
