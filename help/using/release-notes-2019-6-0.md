---
title: 2019.6.0용 릴리스 노트
seo-title: 2019.8.0용 AEM Cloud Manager 릴리스 노트
description: Cloud Manager 릴리스 2019.6.0에 대한 정보를 얻으려면 이 페이지를 따르십시오.
seo-description: AEM Cloud Manager 릴리스 2019.6.0에 대한 정보를 얻으려면 이 페이지를 따르십시오.
translation-type: tm+mt
source-git-commit: 7cfa0cf66efd5891263bfcc83a5149daec5c8b67

---

# 2019.6.0용 릴리스 노트 {#release-notes-for}

&#x200B;2019. [!UICONTROL Cloud Manager] 6.0 릴리스에는 새로운 코드 품질 규칙과 새로운 제품 업데이트 마법사가 추가되었습니다. 자세한 내용은 아래 섹션을 참조하십시오.

## 릴리스 날짜 {#release-date}

버전 2019.6.0 [!UICONTROL Cloud Manager] 의 릴리스 날짜는 2019년 6월 20일입니다.

## 새로운 기능 {#whats-new}

* 새 제품 업데이트 마법사를 사용하여 고객이 AEM 업데이트를 성공적으로 실행할 수 있습니다. 자세한 내용은 [제품](overview-productupdate-wizard.md) 업데이트 마법사를 참조하십시오.
* 컨텐츠 구조를 검사하는 코드 품질 규칙. 자세한 내용은 [사용자 지정 코드](custom-code-quality-rules.md) 품질 규칙을 참조하십시오.
* Git 푸시의 최대 크기는 1GB로 증가했습니다.

## 버그 수정 {#bug-fixes}

* 일부의 경우, 이전 실패 때문에 파이프라인을 시작할 수 없었습니다.

## 알려진 문제 {#known-issues}

* 코드 품질 CSV 다운로드가 항상 심각도에 따라 정렬되는 것은 아닙니다.
* OSGi 구성이 *구성* 폴더 아래의 중첩된 폴더에 배치된 경우 ConfigAndInstallShouldOnlyContainOsgiNodes ** 규칙에서 잘못된 위치를 보고할 수 있습니다.