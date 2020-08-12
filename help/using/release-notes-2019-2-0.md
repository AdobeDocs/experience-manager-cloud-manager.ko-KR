---
title: 2019.2.0용 릴리스 노트
seo-title: 2019.2.0용 AEM Cloud Manager 릴리스 노트
description: Cloud Manager 릴리스 2019.2.0에 대한 정보를 얻으려면 이 페이지를 따르십시오.
seo-description: AEM Cloud Manager 릴리스 2019.2.0에 대한 정보를 얻으려면 이 페이지를 따르십시오.
translation-type: tm+mt
source-git-commit: 98395c4413b1b6bfbb3a565388ffa32dc3880dff

---


# 2019.2.0용 릴리스 노트 {#release-notes-for}

&#x200B;2019. [!UICONTROL Cloud Manager] 2.0 릴리스에는 새로운 시스템 모니터링 기능이 추가되었습니다. 따라서 고객은 Adobe Managed Services 환경의 상태를 시스템 수준에서 볼 수 있습니다.


## 릴리스 날짜 {#release-date}

버전 2019.2.0 [!UICONTROL Cloud Manager] 의 릴리스 날짜는 2019년 2월 21일입니다.

## 새로운 기능 {#whats-new}

* 새로운 시스템 모니터링 기능. 자세한 [내용은 환경](monitor-your-environments.md) 모니터링을 참조하십시오.
* 이제 마법사가 생성한 프로젝트의 디스패처 모듈에 README 파일이 포함되어 있습니다.
* 코드 스캔 문제의 정렬 순서가 문제 우선순위와 일치하도록 개선되었습니다.
* 이제 배포 오류가 발생하는 경우에도 스테이지 인스턴스가 로드 밸런서에 항상 복원됩니다.
* Adobe I/O 콘솔에서 통합을 만들 수 있는 권한을 특정 사용자에게 부여하는 새 API 개발자 역할을 관리 콘솔에서 사용할 수 있습니다. 자세한 내용은 [개발자](https://www.adobe.com/go/aac_api_prod_learn) 관리를 참조하십시오.
* Maven Tranype 버전이 버전 16으로 업데이트되었습니다.
* Maven 버전이 3.6.0 버전으로 업데이트되었습니다.

## 버그 수정 {#bug-fixes}

* 경우에 따라 대상 환경이 Azure에서 호스팅되면 파이프라인이 실행되지 않습니다.
* 환경 순서가 일관되지 않았습니다.
* 검색된 페이지 경로에 쉼표 문자가 포함된 경우 성능 테스트가 실패할 수 있습니다.
* 웹 UI에서 파이프라인 실행을 시작할 때 브라우저 뒤로 버튼이 제대로 작동하지 않았습니다.
* 개요 페이지의 추가 정보 링크가 새 탭을 열지 못했습니다.
* 프로그램 축소판을 업로드할 때 즉시 표시되지 않았을 수 있습니다.
* 프로젝트별 구성으로 인해 코드 검사가 실패하는 경우가 있습니다.
* 비프로덕션 파이프라인 카드의 자세한 내용 링크가 잘못된 위치로 이동되었습니다.
* 품질 게이트가 무시되면 상태가 일관되게 표시되지 않았습니다.
* 콜드 대기 토폴로지를 사용하는 고객이 보안 테스트에 대해 잘못된 결과를 받았습니다.
* 마법사를 사용하여 새 프로젝트를 만들 때 대시 문자가 포함된 분기를 만들 수 없었습니다.

## 알려진 문제 {#known-issues}

* 모니터링 데이터가 새로 고쳐지면 숨겨진 모든 시리즈가 숨겨지지 않습니다.
* 기존 SLA 보고서를 보려는 고객은 다음 릴리스까지 수동으로 탐색해야 합니다.

   이 URL을 작성하려면 패턴(`https://<Experience Cloud URL>/content/mac/<Experience Cloud Tenant>/managedservices/sla.html`)을 따르십시오. 예를 들어, Experience Cloud의 URL이 (`https://weretailprod.experiencecloud.adobe.com`)이면 SLA 보고서 URL은 (`https://weretailprod.experiencecloud.adobe.com/content/mac/weretailprod/managedservices/sla/html`)입니다.

   이 문제는 다음 릴리스에서 SLA 보고서를 사용할 수 있게 됨에 따라 해결될 것으로 [!UICONTROL Cloud Manager]예상됩니다.
