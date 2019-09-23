---
title: 2018.9.0용 릴리스 노트
seo-title: 2018.9.0용 AEM Cloud Manager 릴리스 노트
description: Cloud Manager 릴리스 2018.9.0에 대한 정보를 얻으려면 이 페이지를 따르십시오.
seo-description: AEM Cloud Manager 릴리스 2018.9.0에 대한 정보를 얻으려면 이 페이지를 따르십시오.
uuid: 3af5808f-828f-4846-bee4-1e62194b48ad
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: 릴리스 노트
discoiquuid: 85a1dcf3-2eef-4ba8-b4d1-09e4a88c7bd0
translation-type: tm+mt
source-git-commit: 949d3cf0239a02875ba4ad1888e081f104dec2e2

---


# 2018.9.0용 릴리스 노트 {#release-notes-for}

2018. [!UICONTROL Cloud Manager] 9.0 릴리스에서는 Events를 비롯한 Adobe I/O 기반 API에 대한 지원이 추가되어 [!UICONTROL Cloud Manager]의 CI/CD 파이프라인을 다른 시스템과 통합할 수 있습니다. 또한 [반응]에서 UI 레이어의 다시 쓰기를 시작합니다.

## 릴리스 날짜 {#release-date}

버전 2018.9.0 [!UICONTROL Cloud Manager] 의 릴리스 날짜는 2018년 11월 1일입니다.

## 새로운 기능 {#whats-new}

* **CI/CD 파이프라인** - 새로운 API 및 이벤트 시스템을 [!UICONTROL Cloud Manager]사용하여 CI/CD 파이프라인을 다른 시스템과 통합할 수 있습니다. 자세한 내용은 API [!UICONTROL Cloud Manager] 설명서(https://www.adobe.io/apis/experiencecloud/cloud-manager/docs.html)를 참조하십시오.

* **UI** - 보다 응답 속도가 빠른 새로운 UI 레이어 소개

## 버그 수정 {#bug-fixes}

* 2018. [!UICONTROL Cloud Manager] 8.0에서는 활동 페이지 기간이 분 및 시간 단위로 표시되었지만 해당 정보가 테이블 머리글에 반영되지 않았습니다.
* 드문 경우이지만 고객이 새 응용 프로그램 프로젝트 마법사를 시작할 수 없었습니다.
* 새 응용 프로그램 프로젝트 마법사 대화 상자의 단추 레이블이 잘못 지정되었습니다.
* 경우에 따라 활동 페이지에서 세부 사항 단추를 클릭하면 개요 페이지로 리디렉션됩니다.
* 드물고 예기치 않은 몇 가지 상황으로 인해 개요 페이지에 카드가 누락되었습니다.
* 모든 고객의 프로그램 목록 페이지에 자산 아이콘이 표시되었습니다.
* 백엔드 오류가 발생하면 파이프라인 실행이 유효성 검사 단계에 남아 *있는 것처럼* 보입니다.
* 특정 상황에서 프로그램 설명의 길이가 잘못 계산되었습니다.

## 알려진 문제 {#known-issues}

* 응용 프로그램 프로젝트 마법사를 사용하여 만든 분기에는 대시를 포함할 수 없습니다.
* Adobe [!UICONTROL Experience Cloud] 알림 사이드바가 알림을 일관되게 로드하지 못할 수 있습니다. 그러나 알림은 Adobe에서 볼 수 [!UICONTROL Experience Cloud] 있으며, 구성된 경우 여전히 이메일을 통해 전송됩니다.

