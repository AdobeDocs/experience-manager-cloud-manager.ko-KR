---
title: 2018.8.0용 릴리스 노트
seo-title: 2018.9.0용 AEM Cloud Manager 릴리스 노트
description: Cloud Manager 릴리스 2018.8.0에 대한 정보를 얻으려면 이 페이지를 따르십시오.
seo-description: AEM Cloud Manager 릴리스 2018.8.0에 대한 정보를 얻으려면 이 페이지를 따르십시오.
uuid: e8aaba32-89b4-4bc5-b295-09b753252612
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: 릴리스 노트
discoiquuid: 9222ac3b-525e-47c1-b481-ac9d22e3d559
translation-type: tm+mt
source-git-commit: 15f75ca67c3d52ae511357c5b564daaa3d9def6b

---


# 2018.8.0용 릴리스 노트 {#release-notes-for}

2018. [!UICONTROL Cloud Manager] 8.0 릴리스에는 git 커밋에 자동으로 CI/CD 파이프라인을 트리거하는 지원과 AEM 프로젝트 전형 기반의 git에서 애플리케이션 프로젝트를 만드는 새로운 마법사가 추가되었습니다.

## 릴리스 날짜 {#release-date}

버전 2018.8.0 [!UICONTROL Cloud Manager] 의 릴리스 날짜는 2018년 10월 4일입니다.

## 새로운 기능 {#what-s-new}

* **프로그램 설정** - AEM Project Tranype을 사용하여 git에서 응용 프로그램 프로젝트를 만드는 새로운 마법사 [자세한 내용은 AEM 응용 프로그램 프로젝트](create-an-application-project.md) 만들기를 참조하십시오.

* **CI/CD 파이프라인** - 다음 변경 사항이 CI/CD 파이프라인에 추가됩니다. 자세한 내용은 [CI/CD 파이프라인](configuring-pipeline.md) 구성을 참조하십시오.

   * Git 변경 트리거에서, 구성된 git 분기에 커밋이 추가될 때마다 CI/CD 파이프라인을 시작합니다.
   * 이제 홈 화면의 카드는 파이프라인 실행 페이지의 특정 섹션에 대한 심층적인 링크를 제공합니다.
   * 이제 활동 페이지에 각 실행에 사용된 특정 분기가 나열됩니다.
   * 이제 활동 페이지에 시간 및 분 단위의 지속 시간이 표시됩니다.
   * 이제 파이프라인 실행 페이지에 실행에 대해 생성된 버전/태그 이름이 표시됩니다.
   * Apache Maven 버전이 3.5.3으로 업데이트되었습니다.

* **탐색** - 다음 변경 사항이 에 추가됩니다 [!UICONTROL Cloud Manager].

   * 전역 탐색의 리소스 링크는 Sharepoint의 Runbook으로 이동합니다.
   * 도움말 메뉴가 더 [!UICONTROL Cloud Manager]특정 컨텐츠를 포함하도록 재구성되었습니다.

## 버그 수정 {#bug-fixes}

* 성능 테스트 대화 상자의 일부 세부 사항이 Firefox에서 표시되지 않았습니다.
* 내부 시스템 간의 시간 초과로 인해 배포 오류가 보고되는 경우가 있습니다.
* 활동 페이지의 아이콘 색상이 일부 파이프라인 실행에 대해 올바르지 않습니다.
* 경우에 따라 성능 테스트 대화 상자에 동일한 지표가 여러 번 나열되기도 했습니다.
* CI/CD 파이프라인이 시작된 후 새 인스턴스가 추가된 경우 새로 생성된 인스턴스에서 배포가 실행되지 않습니다.

## 알려진 문제 {#known-issues}

* 응용 프로그램 프로젝트 마법사를 사용하여 만든 분기에는 대시를 포함할 수 없습니다.
* 알림 사이드바가 일관되게 알림을 로드하지 못할 수 [!UICONTROL Experience Cloud] 있습니다. 그러나 알림은 에서 볼 수 [!UICONTROL Experience Cloud] 있으며, 구성된 경우 여전히 이메일을 통해 전송됩니다.

