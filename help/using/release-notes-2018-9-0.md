---
title: 2018.9.0 릴리스 노트
seo-title: 2018.9.0 용 AEM Cloud Manager 릴리스 노트
description: Cloud Manager 릴리스 2018.9.0에 대한 정보를 얻으려면 이 페이지를 따르십시오.
seo-description: AEM Cloud Manager 릴리스 2018.9.0에 대한 정보를 얻으려면 이 페이지를 따르십시오.
uuid: 3 AF 5808 F -828 F -4846-BEE 4-1 E 62194 B 48 AD
contentOwner: Jsyal
products: sg_ Experiencemanager/Cloudmanager
topic-tags: 릴리스 노트
discoiquuid: 85 a 1 DCF 3-2 EEF -4 BA 8-B 4 D 1-09 E 4 A 88 C 7 BD 0
translation-type: tm+mt
source-git-commit: 1dfb065c09569f811e5a006d3d74825d3bd7cc8d

---


# 2018.9.0 릴리스 노트 {#release-notes-for}

[!UICONTROL Cloud Manager] 2018.9.0 릴리스에는 타사의 CI/CD 파이프라인을 다른 시스템과 통합하는 [!UICONTROL Cloud Manager]이벤트를 포함하여 Adobe I/O 기반의 API에 대한 지원이 추가되었습니다. 또한 UI 레이어 재작성을 반응형으로 시작합니다.

## 릴리스 날짜 {#release-date}

버전 2018.9.0 릴리스 [!UICONTROL Cloud Manager] 날짜는 2018 년 11 월 1 일입니다.

## 새로운 기능 {#whats-new}

* **CI/CD 파이프라인** -&#39; CI/CD 파이프라인&#39;을 다른 시스템과 통합하는 [!UICONTROL Cloud Manager]새로운 API 및 이벤트 시스템. 자세한 내용은 [!UICONTROL Cloud Manager] API 설명서 (https://www.adobe.io/apis/experiencecloud/cloud-manager/docs.html)를 참조하십시오.

* **UI** - 응답 속도가 빠른 새로운 UI 레이어 소개

## 버그 수정 {#bug-fixes}

* 2018.8.0 에서는 [!UICONTROL Cloud Manager] 활동 페이지 기간이 분 및 시간에 표시되었지만 해당 정보가 테이블 헤더에 반영되지 않았습니다.
* 드문 경우이지만, 고객은 새 응용 프로그램 프로젝트 마법사를 시작할 수 없었습니다.
* 새 응용 프로그램 프로젝트 마법사 대화 상자의 단추 레이블이 잘못 표시되었습니다.
* 일부 상황에서는 활동 페이지에서 세부 사항 단추를 클릭하면 개요 페이지로 리디렉션됩니다.
* 드물거나 예기치 않은 상황으로 인해 개요 페이지에 카드가 누락되었습니다.
* 모든 고객을 위한 프로그램 목록 페이지에 자산 아이콘이 표시되었습니다.
* 백엔드 오류가 있는 경우 때때로 파이프라인 실행이 *유효성 검사* 단계에 남아 있을 수 있습니다.
* 특정 상황에서 프로그램 설명 길이가 잘못 계산되었습니다.

## 알려진 문제 {#known-issues}

* 응용 프로그램 프로젝트 마법사를 사용하여 만든 분기에 대시 (dash) 를 포함할 수 없습니다.
* Adobe [!UICONTROL Experience Cloud] 알림 사이드바는 알림을 일관되게 로드할 수 없습니다. 그러나 알림은 Adobe [!UICONTROL Experience Cloud] 에 표시되며 구성된 경우 이메일을 통해 전송됩니다.

