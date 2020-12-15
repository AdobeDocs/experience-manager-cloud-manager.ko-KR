---
title: 2020.8.0 릴리스 노트
seo-title: 2020.8.0용 AEM Cloud Manager 릴리스 노트
description: Cloud Manager 릴리스 2020.8.0에 대한 정보를 얻으려면 이 페이지를 따르십시오.
seo-description: AEM Cloud Manager 릴리스 2020.8.0에 대한 정보를 얻으려면 이 페이지를 따르십시오.
translation-type: tm+mt
source-git-commit: c1d07c95088a279376ef495001a5165c7e459642
workflow-type: tm+mt
source-wordcount: '192'
ht-degree: 6%

---

# 2020.8.0 릴리스 노트 {#release-notes-for}

다음 섹션에서는 [!UICONTROL Cloud Manager] 릴리스 2020.8.0에 대한 일반 릴리스 노트에 대해 간략하게 설명합니다.

## 릴리스 날짜 {#release-date}

[!UICONTROL Cloud Manager] 버전 2020.8.0의 릴리스 날짜는 2020년 8월 06일입니다.

## 새로운 기능 {#whats-new}

이제 인증 바인딩된 개인 정보 저장소가 지원됩니다.

## 버그 수정 {#bug-fixes}

* 불필요하고 원하지 않는 일부 SonarQube 플러그인이 코드 품질 스캐닝의 일부로 실행 중이었습니다.

* 파이프라인 실행 페이지에서 분기 이름의 형식이 잘못되었습니다.

* 단일 게시, 단일 디스패처 및 콜드 대기 작성자가 있는 토폴로지에 배포할 때 디스패처가 부하 균형 조정기에서 잘못 제거되었습니다.

* 경우에 따라 완료된 파이프라인 실행이 완료된 것으로 기록되지 않아 파이프라인의 새로운 실행을 방지할 수 없습니다.

* 내부 통신 문제로 인해 파이프라인 실행이 *중단되는 경우가 있습니다.*

* 프로그램 카드의 도구 설명이 일관되게 올바르지 않습니다.

* **개요** 페이지에 색상 불일치가 있습니다.

* 사이트 성능 테스트는 이제 선택적 인증 사용을 지원합니다.

* 작성자 인스턴스용 Dispatcher 캐시는 Cloud Manager를 통해 디스패처 구성이 배포될 때 자동으로 플러시됩니다.

