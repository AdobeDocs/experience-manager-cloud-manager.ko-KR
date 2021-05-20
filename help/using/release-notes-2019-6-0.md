---
title: 2019.6.0 릴리스 노트
seo-title: AEM Cloud Manager 2019.6.0용 릴리스 노트
description: Cloud Manager 릴리스 2019.6.0에 대한 정보를 보려면 이 페이지를 따르십시오.
seo-description: AEM Cloud Manager 릴리스 2019.6.0에 대한 정보를 보려면 이 페이지를 따르십시오.
feature: 릴리스 정보
exl-id: 5a87f191-8203-4cb9-a810-247aece41605
source-git-commit: 43bb3c477ef9c1ce178509b8180479d7616edc66
workflow-type: tm+mt
source-wordcount: '164'
ht-degree: 9%

---

# 2019.6.0 릴리스 노트 {#release-notes-for}

[!UICONTROL Cloud Manager] 2019.6.0 릴리스는 새로운 코드 품질 규칙과 새 제품 업데이트 마법사를 추가합니다. 자세한 내용은 아래 섹션을 참조하십시오.

## 릴리스 날짜 {#release-date}

[!UICONTROL Cloud Manager] 버전 2019.6.0의 출시일은 2019년 6월 20일입니다.

## 새로운 기능 {#whats-new}

* 고객이 AEM 업데이트를 성공적으로 실행할 수 있도록 지원하기 위한 새 제품 업데이트 마법사. 자세한 내용은 [제품 업데이트 마법사](overview-productupdate-wizard.md)를 참조하십시오.
* 컨텐츠 구조를 검사하는 코드 품질 규칙. 자세한 내용은 [사용자 지정 코드 품질 규칙](custom-code-quality-rules.md)을 참조하십시오.
* Git 푸시의 최대 크기가 1GB로 증가했습니다.

## 버그 수정 {#bug-fixes}

* 이전에 오류가 발생하여 파이프라인을 시작할 수 없는 경우가 있습니다.

## 알려진 문제 {#known-issues}

* 코드 품질 CSV 다운로드가 항상 심각도에 따라 정렬되지는 않습니다.
* OSGi 구성이 *config* 폴더 아래의 중첩된 폴더에 배치된 경우 *ConfigAndInstallShouldOnlyContainOsgiNodes* 규칙이 긍정 오류(false positive)를 보고할 수 있습니다.
