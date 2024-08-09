---
title: 주요 개념
description: 모든 강력한 도구와 마찬가지로 Cloud Manager는 많은 개념과 용어를 포함합니다. 이 문서에서는 Cloud Manager 사용을 시작할 때 가장 중요한 몇 가지를 요약합니다.
exl-id: 86dfc976-f3da-479a-9faa-08f40ca909e0
source-git-commit: 200366e5db92b7ffc79b7a47ce8e7825b29b7969
workflow-type: tm+mt
source-wordcount: '413'
ht-degree: 70%

---


# 주요 개념 {#key-concepts}

모든 강력한 도구와 마찬가지로 Cloud Manager는 많은 개념과 용어를 포함합니다. 이 문서에서는 Cloud Manager 사용을 시작할 때 가장 중요한 몇 가지를 요약합니다.

## 애플리케이션 {#application}

애플리케이션은 고객이 특정 사용 사례와 필요에 따라 기본 [솔루션](#solution)(예: AEM Sites 또는 AEM Assets)을 조정하기 위해 만든 일련의 사용자 정의 및 구성입니다. 응용 프로그램은 여러 [아티팩트](#artifact)로 구성될 수 있는 논리 단위입니다.

예제 애플리케이션은 가상의 [WKND 라이프스타일 애플리케이션](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-wknd-tutorial-develop/overview.html)입니다.

## 아티팩트 {#artifact}

아티팩트는 배포 가능한 단위이며 소스 코드를 단일 단위로 변환하는 일부 빌드 프로세스의 결과입니다. 예를 들어 소스 코드가 포함된 .zip 파일입니다.

## 아티팩트 저장소 {#artifact-repository}

아티팩트 저장소는 고객별 [아티팩트](#artifact)를 저장하고 보안을 유지하는 저장소 위치입니다.

## 환경 {#environment}

환경은 [program](#program) 내의 가상 컴퓨터의 단일 클러스터입니다. AEM의 경우 작성 인스턴스(선택적으로 추가 콜드 대기 작성 인스턴스 포함), 0개 이상의 게시 인스턴스, 하나 이상의 Dispatcher 인스턴스 및 로드 밸런서로 구성됩니다.

## git 저장소 {#git-repository}

git 저장소는 고객별 소스 코드가 저장되고 [git을 사용](https://git-scm.com)하여 액세스할 수 있는 위치입니다.

## 인스턴스 {#instance}

인스턴스는 AEM [솔루션](#solution)을 실행하는 특정 가상 서버입니다. 인스턴스는 배포 관점에서 단일의 논리적 단위를 나타냅니다.

## 조직 {#organization}

조직은 기업 고객을 대표하는 Adobe 구성입니다. Adobe의 Identity Management System(IMS)에서 프로비저닝된 방식에 따라 한 회사는 여러 조직을 가질 수 있습니다.

## 파이프라인 {#pipeline}

파이프라인은 순차적으로 실행되는 배포 단계의 집합입니다.

## 제품 {#product}

제품은 조직에서 라이선스를 부여한 [솔루션](#solution) 내의 특정 기능 집합입니다. 조직 내의 다른 [프로그램](#program)이 AEM Sites, AEM Assets 또는 AEM Forms와 같은 다양한 제품 집합을 이용할 수 있습니다.

## 프로그램 {#program}

프로그램은 일반적으로 구매 서비스 수준 계약(SLA)에 해당하는 고객 이니셔티브의 논리적 그룹화를 지원하는 일련의 환경입니다. 각 프로그램에는 정확히 하나의 프로덕션 환경이 있으며 많은 비프로덕션 환경이 있을 수 있습니다.

## 솔루션 {#solution}

솔루션은 Adobe [!UICONTROL Experience Cloud] 솔루션 중 하나입니다. 예를 들어 Adobe Experience Manager, Adobe Target 또는 Adobe Analytics가 있습니다.

## 단계 {#step}

단계는 [파이프라인](#pipeline)의 빌딩 블록으로서 작업의 일부 단위를 수행하는 구성된 명령 집합입니다.
