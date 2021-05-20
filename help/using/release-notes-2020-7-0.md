---
title: 2020.7.0 릴리스 노트
seo-title: AEM Cloud Manager 2020.7.0용 릴리스 노트
description: Cloud Manager 릴리스 2020.7.0에 대한 정보를 보려면 이 페이지를 따르십시오
seo-description: AEM Cloud Manager 릴리스 2020.7.0에 대한 정보를 보려면 이 페이지를 따르십시오
feature: 릴리스 정보
exl-id: c0272d9d-0a6d-4abd-add1-f82280b7ecec
source-git-commit: 43bb3c477ef9c1ce178509b8180479d7616edc66
workflow-type: tm+mt
source-wordcount: '212'
ht-degree: 52%

---

# 2020.7.0 릴리스 노트 {#release-notes-for}

다음 섹션에서는 [!UICONTROL Cloud Manager] 릴리스 2020.9.0에 대한 일반 릴리스 노트를 간략하게 설명합니다.

## 릴리스 날짜 {#release-date}

[!UICONTROL Cloud Manager] 버전 2020.7.0의 출시일은 2020년 7월 9일입니다.

## 새로운 기능 {#whats-new}

* 이제 프로덕션 배포 시 로드 밸런서에서 디스패처 인스턴스를 분리 및 첨부하는 것이 보다 일관된 방식으로 작동합니다.

* 이제 Cloud Manager 빌드 컨테이너가 Java 8과 Java 11을 모두 지원합니다.

* 이제 Cloud Manager 파이프라인이 고객 설정 변수 및 기밀을 지원합니다.
자세한 내용은 [파이프라인 변수](/help/using/build-environment-details.md#pipeline-variables)를 참조하십시오.

## 버그 수정 {#bug-fixes}

* 비프로덕션 파이프라인 편집 페이지의 **취소** 및 **저장** 옵션이 항상 표시되는 것은 아닙니다.

* 코드 품질 프로세스의 일부 오류로 인해 로그 파일이 올바로 생성되지 않을 수 있습니다.

* 일부 큰 파이프라인 단계 로그를 사용자 인터페이스를 통해 일관되게 다운로드할 수 없습니다.

## 알려진 문제 {#known-issues}

* AMS 환경에 대기 인스턴스가 포함되어 있으면 로그된 메시지는 대기 모드와는 반대로 인스턴스가 다운되었음을 나타냅니다.

* 코드 검사 계산 방식의 변경으로 인해 Jacoco 플러그인의 _최소_ 버전은 이제 0.7.5.201505241946(2015년 5월 릴리스)입니다. 이전 버전을 명시적으로 참조하는 고객은 코드 품질 프로세스에서 오류 메시지를 받게 됩니다.
