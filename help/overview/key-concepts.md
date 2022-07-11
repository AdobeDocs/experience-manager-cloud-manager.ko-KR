---
title: 주요 개념
description: 모든 강력한 도구와 마찬가지로 Cloud Manager는 많은 개념과 용어를 포함합니다. 이 문서에서는 Cloud Manager 사용을 시작할 때 가장 중요한 몇 가지 사항을 요약합니다.
exl-id: 86dfc976-f3da-479a-9faa-08f40ca909e0
source-git-commit: 73e322cf93dc7709b7581860974079c8d94034ba
workflow-type: tm+mt
source-wordcount: '417'
ht-degree: 4%

---


# 주요 개념 {#key-concepts}

모든 강력한 도구와 마찬가지로 Cloud Manager는 많은 개념과 용어를 포함합니다. 이 문서에서는 Cloud Manager 사용을 시작할 때 가장 중요한 몇 가지 사항을 요약합니다.

## 애플리케이션 {#application}

또한 애플리케이션이 고객이 기본 설정을 적용하기 위해 생성한 사용자 지정 및 구성 세트입니다 [솔루션](#solution) (예: AEM Sites 또는 AEM Assets) 을 사용하십시오. 응용 프로그램은 여러 개로 구성될 수 있는 논리 단위입니다 [객체.](#artifact)

예제 응용 프로그램은 가상의 응용 프로그램입니다 [WKND 라이프스타일 애플리케이션.](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-wknd-tutorial-develop/overview.html)

## 아티팩트 {#artifact}

아티팩트는 배포 가능한 단위이며 소스 코드를 단일 단위로 변환하는 일부 빌드 프로세스의 결과입니다. 예를 들어 소스 코드가 포함된 .zip 파일입니다.

## 객체 저장소 {#artifact-repository}

객체 저장소는 고객별로 지정된 저장 위치입니다 [객체](#artifact) 저장 및 보안

## 환경 {#environment}

환경은 단일 가상 시스템 클러스터로서 [프로그램.](#program) AEM의 경우 작성 인스턴스(선택적 추가 콜드 대기 작성 인스턴스 사용), 0개 이상의 게시 인스턴스, 하나 이상의 디스패처 인스턴스 및 로드 밸런서로 구성됩니다.

## git 리포지토리 {#git-repository}

Git 리포지토리는 고객별 소스 코드가 저장되고 액세스할 수 있는 위치입니다 [git 사용.](https://git-scm.com)

## 인스턴스 {#instance}

인스턴스는 AEM을 실행하는 특정 가상 서버입니다 [솔루션.](#solution) 인스턴스는 배포 관점에서 단일 논리 단위를 나타냅니다.

## 조직 {#organization}

조직은 엔터프라이즈 고객을 나타내는 Adobe 구성입니다. 한 회사에는 Adobe의 Identity Management 시스템(IMS)에서 프로비저닝된 방법에 따라 여러 조직이 있을 수 있습니다.

## 파이프라인 {#pipeline}

파이프라인은 순서대로 실행되는 배포 단계 세트입니다.

## 제품 {#product}

제품은 [솔루션](#solution) 조직에 의해 라이센스가 부여됨. 다름 [프로그램](#program) 조직 내에서 AEM Sites, AEM Assets 또는 AEM Forms과 같은 다양한 제품 세트를 사용할 수 있습니다.

## 프로그램 {#program}

프로그램은 고객 이니셔티브의 논리적 그룹화를 지원하는 환경 집합으로, 일반적으로 구매한 SLA(서비스 수준 계약)에 해당합니다. 각 프로그램에는 정확히 하나의 프로덕션 환경이 있으며 많은 비프로덕션 환경이 있을 수 있습니다.

## 솔루션 {#solution}

솔루션은 Adobe 중 하나입니다 [!UICONTROL Experience Cloud] 솔루션. 예: Adobe Experience Manager, Adobe Target 또는 Adobe Analytics

## 단계 {#step}

단계는 일부 작업 단위를 의 빌딩 블록으로 수행하는 구성된 명령 집합입니다 [파이프라인.](#pipeline)
