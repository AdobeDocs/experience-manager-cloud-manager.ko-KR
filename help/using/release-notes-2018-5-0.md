---
title: 2018.5.0 릴리스 노트
seo-title: AEM Cloud Manager 2018.5.0용 릴리스 노트
description: Cloud Manager 릴리스 2018.5.0에 대한 정보를 보려면 이 페이지를 따르십시오.
seo-description: AEM Cloud Manager 릴리스 2018.5.0에 대한 정보를 보려면 이 페이지를 따르십시오.
uuid: 37f8b155-6984-454d-83a8-3f5fb081be97
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: release-notes
discoiquuid: 6d1e7098-b56e-4172-8373-486f186f3d53
feature: 릴리스 정보
exl-id: 0034bcaf-00d3-410d-b2f6-a2a232888a2b
source-git-commit: 43bb3c477ef9c1ce178509b8180479d7616edc66
workflow-type: tm+mt
source-wordcount: '181'
ht-degree: 8%

---

# 2018.5.0 릴리스 노트 {#release-notes-for}

다음 섹션에서는 [!UICONTROL Cloud Manager] 릴리스 2018.5.0에 대한 일반 릴리스 노트를 간략하게 설명합니다.

## 릴리스 날짜 {#release-date}

[!UICONTROL Cloud Manager] 버전 2018.5.0의 출시일은 2018년 7월 12일입니다.

## 새로운 기능 {#what-s-new}

* **CI/CD 파이프라인 알림**  - 이제 사용자 [!UICONTROL Experience Cloud] 에게 파이프라인 이벤트에 대한 알림이 표시됩니다. 자세한 내용은 [알림](notifications.md)을 참조하십시오.

* **예약된 프로덕션 배포**  - 이제 사용자는 프로덕션 배포를 위해 날짜 또는 시간을 예약할 수 있습니다. 자세한 내용은 [코드 배포](deploying-code.md)를 참조하십시오.

* **** 활동으로 검색되는 시작  **페이지입니다**.

* 파이프라인 실행 중에 발생한 문제에 대해 홈 페이지에 표시되는 보다 구체적인 정보입니다.
* 성능 테스트 인프라 개선.

## 버그 수정 {#bug-fixes}

* 일부 상황에서 잘못된 SonarQube 프로필이 사용되어 잘못된 코드 품질 지표가 발생했습니다.
* SonarQube 검사는 CQBP-75에서 특정 OSGi 주석을 무시했습니다.
* CI/CD 파이프라인이 취소되었을 때 상태가 일관되게 표시되지 않았습니다.

## 알려진 문제 {#known-issues}

* 프로그램 목록 화면에서 **AEM** 및 **Monitoring**&#x200B;에 대한 링크는 현재 브라우저 탭을 대체하고 새 탭으로 열립니다.
