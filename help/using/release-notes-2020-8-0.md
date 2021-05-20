---
title: 2020.8.0 릴리스 노트
seo-title: AEM Cloud Manager 2020.8.0용 릴리스 노트
description: Cloud Manager 릴리스 2020.8.0에 대한 정보를 보려면 이 페이지를 따르십시오
seo-description: AEM Cloud Manager 릴리스 2020.8.0에 대한 정보를 보려면 이 페이지를 따르십시오
feature: 릴리스 정보
exl-id: 94163e28-5c29-4a00-9a2b-e45bf6f71098
source-git-commit: 43bb3c477ef9c1ce178509b8180479d7616edc66
workflow-type: tm+mt
source-wordcount: '194'
ht-degree: 7%

---

# 2020.8.0 릴리스 노트 {#release-notes-for}

다음 섹션에서는 [!UICONTROL Cloud Manager] 릴리스 2020.8.0에 대한 일반 릴리스 노트를 간략하게 설명합니다.

## 릴리스 날짜 {#release-date}

[!UICONTROL Cloud Manager] 버전 2020.8.0의 출시일은 2020년 8월 6일입니다.

## 새로운 기능 {#whats-new}

이제 인증 바인딩된 Private Maven 리포지토리가 지원됩니다.

## 버그 수정 {#bug-fixes}

* 일부 불필요하고 원치 않는 SonarQube 플러그인이 코드 품질 스캔의 일부로 실행되었습니다.

* 파이프라인 실행 페이지에서 분기 이름의 형식이 잘못되었습니다.

* 단일 게시, 단일 디스패처 및 콜드 대기 작성자가 있는 토폴로지에 배포할 때 로드 밸런서에서 디스패처가 잘못 제거되었습니다.

* 경우에 따라 완료된 파이프라인 실행이 완료된 것으로 기록되지 않아 파이프라인의 새로운 실행이 방지됩니다.

* 내부 통신 문제로 인해 파이프라인 실행이 *멈춥니다.*

* 프로그램 카드의 도구 설명이 일관되게 올바르지 않습니다.

* **개요** 페이지에 색상이 일치하지 않습니다.

* 사이트 성능 테스트는 이제 선택적 인증 사용을 지원합니다.

* 작성자 인스턴스에 대한 Dispatcher 캐시는 Cloud Manager를 통해 Dispatcher 구성을 배포하면 자동으로 초기화됩니다.
