---
title: 2019.2.0 릴리스 노트
seo-title: AEM Cloud Manager 2019.2.0용 릴리스 노트
description: Cloud Manager 릴리스 2019.2.0에 대한 정보를 보려면 이 페이지를 따르십시오.
seo-description: AEM Cloud Manager 릴리스 2019.2.0에 대한 정보를 보려면 이 페이지를 따르십시오.
feature: 릴리스 정보
exl-id: e7198efa-4a73-42e5-bb17-8dea255e056e
source-git-commit: 43bb3c477ef9c1ce178509b8180479d7616edc66
workflow-type: tm+mt
source-wordcount: '399'
ht-degree: 4%

---

# 2019.2.0 릴리스 노트 {#release-notes-for}

[!UICONTROL Cloud Manager] 2019.2.0 릴리스는 새 시스템 모니터링 기능을 추가합니다. 이를 통해 고객은 시스템 수준에서 Adobe Managed Services 환경의 상태를 볼 수 있습니다.


## 릴리스 날짜 {#release-date}

[!UICONTROL Cloud Manager] 버전 2019.2.0의 출시일은 2019년 2월 21일입니다.

## 새로운 기능 {#whats-new}

* 새로운 시스템 모니터링 기능. 자세한 내용은 [환경 모니터링](monitor-your-environments.md)을 참조하십시오.
* 이제 마법사가 생성한 프로젝트의 디스패처 모듈에 README 파일이 포함되어 있습니다.
* 문제 우선 순위에 맞게 코드 스캔 문제의 정렬 순서가 개선되었습니다.
* 이제 배포 실패 경우에도 스테이지 인스턴스가 항상 로드 밸런서에 복원됩니다.
* 새 API 개발자 역할을 Admin Console에서 사용할 수 있습니다. 이 역할을 통해 특정 사용자에게 Adobe I/O 콘솔에서 통합을 만들 수 있는 권한을 부여할 수 있습니다. 자세한 내용은 [개발자 관리](https://www.adobe.com/go/aac_api_prod_learn) 를 참조하십시오.
* Maven Archetype 버전이 버전 16으로 업데이트되었습니다.
* Maven 버전이 버전 3.6.0으로 업데이트되었습니다.

## 버그 수정 {#bug-fixes}

* 일부 경우에는 대상 환경이 Azure에서 호스팅되면 파이프라인이 실행되지 않습니다.
* 환경 순서가 일치하지 않습니다.
* 검색된 페이지 경로에 쉼표 문자가 포함된 경우 성능 테스트가 실패할 수 있습니다.
* 웹 UI에서 파이프라인 실행을 시작할 때 브라우저 뒤로 단추가 제대로 작동하지 않았습니다.
* 개요 페이지의 추가 정보 링크가 새 탭을 열지 않았습니다.
* 프로그램 축소판을 업로드할 때 즉시 표시되지 않았을 수 있습니다.
* 프로젝트별 구성으로 인해 코드 스캔에 실패한 경우도 있습니다.
* 비프로덕션 파이프라인 카드의 추가 정보 링크가 잘못된 위치로 이동되었습니다.
* 품질 게이트가 재정의되었을 때 상태가 비일관되게 표시되었습니다.
* 콜드 대기 토폴로지를 사용하는 고객은 보안 테스트에 대해 잘못된 결과를 받았습니다.
* 마법사를 사용하여 새 프로젝트를 만들 때 대시 문자가 포함된 분기를 만들 수 없었습니다.

## 알려진 문제 {#known-issues}

* 모니터링 데이터를 새로 고치면 숨겨진 모든 시리즈가 숨김 취소됩니다.
* 기존 SLA 보고서를 보려면 다음 릴리스까지 수동으로 탐색해야 합니다.

   이 URL을 만들려면 패턴(`https://<Experience Cloud URL>/content/mac/<Experience Cloud Tenant>/managedservices/sla.html`)을 따르십시오. 예를 들어, Experience Cloud의 URL이 (`https://weretailprod.experiencecloud.adobe.com`)이면 SLA 보고서 URL은 (`https://weretailprod.experiencecloud.adobe.com/content/mac/weretailprod/managedservices/sla/html`)입니다.

   이 문제는 [!UICONTROL Cloud Manager] 내의 SLA 보고서를 사용할 수 있는 다음 릴리스에서 해결될 것으로 예상됩니다.
