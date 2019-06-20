---
title: 2019.6.0 릴리스 노트
seo-title: 2019.6.0 용 AEM Cloud Manager 릴리스 노트
description: Cloud Manager 릴리스 2019.6.0에 대한 정보를 얻으려면 이 페이지를 따르십시오.
seo-description: AEM Cloud Manager 릴리스 2019.6.0에 대한 정보를 얻으려면 이 페이지를 따르십시오.
translation-type: tm+mt
source-git-commit: 75563d3f4b2a27d943c052993c97d830338ead9c

---

# Release Notes for 2019.6.0 {#release-notes-for}

[!UICONTROL Cloud Manager] 2019.6.0 릴리스에는 중요한 기능 변경 사항이 포함되지 않습니다. 자세한 내용은 아래 섹션을 참조하십시오.

## Release Date {#release-date}

The Release Date for [!UICONTROL Cloud Manager] Version 2019.6.0 is .

## 새로운 기능 {#whats-new}

* 새 제품 업데이트 마법사를 사용하여 고객이 AEM 업데이트를 성공적으로 실행할 수 있도록 합니다. (제품 업데이트 마법사 페이지에 링크)
* 컨텐츠 구조를 검사하는 코드 품질 규칙입니다. (사용자 지정 코드 품질 규칙 페이지에 링크)
* Git 푸시 최대 크기가 1 GB로 증가했습니다.

## Bug Fixes {#bug-fixes}

* 일부 경우에는 이전 오류로 인해 파이프라인을 시작할 수 없었습니다.

## 알려진 문제 {#known-issues}

* 코드 품질 CSV 다운로드가 항상 심각도에 따라 정렬되는 것은 아닙니다.
* Osgi 구성이 Config 폴더 아래의 중첩 폴더에 배치되는 경우 false positives가 configandinstallshouldonlycontainosginodes 규칙에 의해 보고될 수 있습니다.
