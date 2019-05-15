---
title: 2018.8.0 릴리스 노트
seo-title: 2018.8.0 용 AEM Cloud Manager 릴리스 노트
description: Cloud Manager 릴리스 2018.8.0에 대한 정보를 얻으려면 이 페이지를 따르십시오.
seo-description: AEM Cloud Manager 릴리스 2018.8.0에 대한 정보를 얻으려면 이 페이지를 따르십시오.
uuid: E 8 AABA 32-89 B 4-4 BC 5-B 295-09 B 753252612
contentOwner: Jsyal
products: sg_ Experiencemanager/Cloudmanager
topic-tags: 릴리스 노트
discoiquuid: 9222 AC 3 B -525 E -47 C 1-B 481-AC 9 D 22 E 3 D 559
translation-type: tm+mt
source-git-commit: 1dfb065c09569f811e5a006d3d74825d3bd7cc8d

---


# 2018.8.0 릴리스 노트 {#release-notes-for}

[!UICONTROL Cloud Manager] 2018.8.0 릴리스에서는 Git 커밋 시 CI/CD 파이프라인을 자동으로 트리거하는 지원 및 AEM Project Archetype를 기반으로 Git에서 애플리케이션 프로젝트를 만드는 새로운 마법사가 추가되었습니다.

## 릴리스 날짜 {#release-date}

버전 2018.8.0 릴리스 [!UICONTROL Cloud Manager] 날짜는 2018 년 10 월 4 일입니다.

## 새로운 기능 {#what-s-new}

* **프로그램 설정** - 새 마법사를 사용하여 AEM Project Archetype를 사용하여 Git에서 애플리케이션 프로젝트를 만드는 경우 자세한 내용은 [AEM 애플리케이션 프로젝트](create-an-application-project.md) 만들기를 참조하십시오.

* **CI/CD 파이프라인** - CI/CD 파이프라인에 다음 변경 사항이 추가됩니다. 자세한 내용은 [CI/CD 파이프라인](configuring-pipeline.md) 구성을 참조하십시오.

   * Git 변경 시 트리거된 Git 분기에 커밋이 추가될 때마다 CI/CD 파이프라인이 시작됩니다.
   * 이제 홈 화면의 카드를 파이프라인 실행 페이지의 특정 섹션에 연결합니다.
   * 활동 페이지에는 이제 각 실행에 사용된 특정 분기를 나열합니다.
   * 이제 활동 페이지에 시간 및 분 단위의 지속 시간이 표시됩니다.
   * 이제 파이프라인 실행 페이지에 실행에 대해 만들어진 버전/태그 이름이 표시됩니다.
   * Apache Maven 버전이 3.5.3로 업데이트되었습니다.

* **탐색** - 다음 변경 사항이에 [!UICONTROL Cloud Manager]추가됩니다.

   * 전역 탐색의 리소스 링크는 Sharepoint에서 Runbook로 이동합니다.
   * 도움말 메뉴가 더 많은 [!UICONTROL Cloud Manager]특정 컨텐츠를 포함하도록 재구성되었습니다.

## 버그 수정 {#bug-fixes}

* 성능 테스트 대화 상자의 일부 세부 사항이 Firefox에서 표시되지 않았습니다.
* 내부 시스템 간 시간 초과는 때때로 배포 실패가 보고되는 원인이 됩니다.
* 활동 페이지의 아이콘 색상이 일부 성공적인 파이프라인 실행에 대해 올바르지 않았습니다.
* 경우에 따라 성능 테스트 대화 상자에 동일한 지표가 여러 번 나열되었습니다.
* CI/CD 파이프라인 시작 후 새 인스턴스가 추가된 경우 새로 만든 인스턴스에서 배포가 실행되지 않습니다.

## 알려진 문제 {#known-issues}

* 응용 프로그램 프로젝트 마법사를 사용하여 만든 분기에 대시 (dash) 를 포함할 수 없습니다.
* [!UICONTROL Experience Cloud] 알림 사이드바는 알림을 일관되게 로드할 수 없습니다. 그러나 알림은에 [!UICONTROL Experience Cloud] 표시되며 구성된 경우 이메일을 통해 계속 전송됩니다.

