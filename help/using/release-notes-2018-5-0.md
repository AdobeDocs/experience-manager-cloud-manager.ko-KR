---
title: 2018.5.0용 릴리스 노트
seo-title: 2018.5.0용 AEM Cloud Manager 릴리스 노트
description: Cloud Manager 릴리스 2018.5.0에 대한 정보를 얻으려면 이 페이지를 따르십시오.
seo-description: AEM Cloud Manager 릴리스 2018.5.0에 대한 정보를 얻으려면 이 페이지를 따르십시오.
uuid: 37f8b155-6984-454d-83a8-3f5fb081be97
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: 릴리스 노트
discoiquuid: 6d1e7098-b56e-4172-8373-486f186f3d53
translation-type: tm+mt
source-git-commit: 15f75ca67c3d52ae511357c5b564daaa3d9def6b

---


# 2018.5.0용 릴리스 노트 {#release-notes-for}

다음 섹션에서는 릴리스 2018.5.0 [!UICONTROL Cloud Manager] 에 대한 일반 릴리스 노트에 대해 간략하게 설명합니다.

## 릴리스 날짜 {#release-date}

버전 2018.5.0 [!UICONTROL Cloud Manager] 의 릴리스 날짜는 2018년 7월 12일입니다.

## 새로운 기능 {#what-s-new}

* **CI/CD 파이프라인 알림** - 이제 사용자는 파이프라인 이벤트에 대한 [!UICONTROL Experience Cloud] 알림을 볼 수 있습니다. 자세한 내용은 [알림을](notifications.md) 참조하십시오.

* **예약된 프로덕션** 배포 - 사용자는 이제 프로덕션 배포를 위한 날짜 또는 시간을 예약할 수 있습니다. 자세한 내용은 [코드](deploying-code.md) 배포를 참조하십시오.

* **상태** 페이지가 활동에 **변경되었습니다**.

* 파이프라인 실행 중 발생한 문제에 대한 자세한 정보가 홈 페이지에 표시됩니다.
* 향상된 성능 테스트 인프라

## 버그 수정 {#bug-fixes}

* 일부 상황에서 잘못된 SonarQube 프로필이 사용되어 잘못된 코드 품질 지표가 발생했습니다.
* SonarQube 검사는 CQBP-75에서 특정 OSGi 주석을 무시했습니다.
* CI/CD 파이프라인이 취소되면 상태가 일관되게 표시되지 않았습니다.

## 알려진 문제 {#known-issues}

* [프로그램 **목록** ] **화면에서 AEM 및** 모니터링에 대한 링크가 모두 현재 브라우저 탭을 대체하고 새 탭으로 열립니다.

