---
title: 2018.9.0 릴리스 노트
seo-title: AEM Cloud Manager 2018.9.0용 릴리스 노트
description: Cloud Manager 릴리스 2018.9.0에 대한 정보를 보려면 이 페이지를 따르십시오.
seo-description: AEM Cloud Manager 릴리스 2018.9.0에 대한 정보를 보려면 이 페이지를 따르십시오.
uuid: 3af5808f-828f-4846-bee4-1e62194b48ad
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: release-notes
discoiquuid: 85a1dcf3-2eef-4ba8-b4d1-09e4a88c7bd0
feature: 릴리스 정보
exl-id: bf611743-ded2-4503-97c8-12b12454c7b7
source-git-commit: 43bb3c477ef9c1ce178509b8180479d7616edc66
workflow-type: tm+mt
source-wordcount: '277'
ht-degree: 9%

---

# 2018.9.0 릴리스 노트 {#release-notes-for}

[!UICONTROL Cloud Manager] 2018.9.0 릴리스에서는 이벤트를 포함한 Adobe I/O 기반 API와 [!UICONTROL Cloud Manager] 의 CI/CD 파이프라인과 다른 시스템의 통합을 지원합니다. 또한 반응으로 UI 레이어의 재작성을 시작합니다.

## 릴리스 날짜 {#release-date}

[!UICONTROL Cloud Manager] 버전 2018.9.0의 출시일은 2018년 11월 1일입니다.

## 새로운 기능 {#whats-new}

* **CI/CD 파이프라인**  -  [!UICONTROL Cloud Manager]의 CI/CD 파이프라인과 다른 시스템을 통합하는 새로운 API 및 이벤트 시스템. 자세한 내용은 [!UICONTROL Cloud Manager] API 설명서 (https://www.adobe.io/apis/experiencecloud/cloud-manager/docs.html)을 참조하십시오.

* **UI**  - 반응형 새로운 UI 레이어 소개

## 버그 수정 {#bug-fixes}

* [!UICONTROL Cloud Manager] 2018.8.0에서는 활동 페이지 기간이 분 및 시간 단위로 표시되었지만 해당 정보가 테이블 헤더에 반영되지 않았습니다.
* 고객이 새 응용 프로그램 프로젝트 마법사를 시작할 수 없는 경우가 드물게 나타납니다.
* 새 응용 프로그램 프로젝트 마법사 대화 상자의 단추 레이블이 잘못 표시되었습니다.
* 일부 상황에서 활동 페이지에서 세부 사항 단추를 클릭하면 개요 페이지로 리디렉션됩니다.
* 드물지만 예기치 않은 일부 상황으로 인해 개요 페이지에 카드가 누락되었습니다.
* 모든 고객의 프로그램 목록 페이지에 자산 아이콘이 표시되었습니다.
* 백엔드 오류가 발생한 경우 파이프라인 실행이 *유효성 검사* 단계에 남아 있는 것처럼 보일 수 있습니다.
* 특정 상황에서 프로그램 설명의 길이가 잘못 계산되었습니다.

## 알려진 문제 {#known-issues}

* 응용 프로그램 프로젝트 마법사를 사용하여 만든 분기에는 대시를 포함할 수 없습니다.
* Adobe [!UICONTROL Experience Cloud] 알림 사이드바가 일관되게 알림을 로드하지 못할 수 있습니다. 그러나 알림은 [!UICONTROL Experience Cloud] Adobe에 표시되며, 구성된 경우 여전히 이메일을 통해 전송됩니다.
