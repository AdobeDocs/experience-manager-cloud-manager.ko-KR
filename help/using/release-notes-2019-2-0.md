---
title: 2019.2.0용 릴리스 노트
seo-title: 2019.2.0용 AEM Cloud Manager 릴리스 노트
description: Cloud Manager 릴리스 2019.2.0에 대한 정보를 얻으려면 이 페이지를 따르십시오.
seo-description: AEM Cloud Manager 릴리스 2019.2.0에 대한 정보를 얻으려면 이 페이지를 따르십시오.
translation-type: tm+mt
source-git-commit: 98395c4413b1b6bfbb3a565388ffa32dc3880dff

---


# 2019.2.0용 릴리스 노트 {#release-notes-for}

2019. [!UICONTROL Cloud Manager] 2.0 릴리스에는 새로운 시스템 모니터링 기능이 추가되었습니다. 따라서 고객은 Adobe Managed Services 환경의 상태를 시스템 수준에서 볼 수 있습니다.


## 릴리스 날짜 {#release-date}

버전 2019.2.0 [!UICONTROL Cloud Manager] 의 릴리스 날짜는 2019년 2월 21일입니다.

## 새로운 기능 {#whats-new}

* 새로운 시스템 모니터링 기능. 자세한 [내용은 환경](monitor-your-environments.md) 모니터링을 참조하십시오.
* The dispatcher module in wizard-generated projects now contains a README file.
* 코드 스캔 문제의 정렬 순서가 문제 우선순위와 일치하도록 개선되었습니다.
* Stage instances are now always restored to the load balancer even in the case of a deployment failure.
* A new API Developer role is available in the Admin Console which allows specific users to be granted the permission to create integrations in the Adobe I/O console. Refer to [Manage Developers](https://www.adobe.com/go/aac_api_prod_learn) to learn more.
* The version of the Maven Archetype was updated to version 16.
* The version of Maven was updated to version 3.6.0.

## Bug Fixes {#bug-fixes}

* In some circumstances, pipelines would not execute when the target environment was hosted in Azure.
* Ordering of environments was inconsistent.
* Performance testing could fail when discovered page paths contained a comma character.
* When a pipeline execution was started from the web UI, the browser back button did not function correctly.
* The Learn More links on the Overview page didn't open a new tab.
* When uploading a program thumbnail, it may not have been immediately visible.
* In some cases, Code Scanning failed because of project-specific configuration.
* The Learn More link on the Non-Production Pipelines card went to the wrong location.
* 품질 게이트가 무시되면 상태가 일관되게 표시되지 않았습니다.
* 콜드 대기 토폴로지를 사용하는 고객이 보안 테스트에 대해 잘못된 결과를 받았습니다.
* 마법사를 사용하여 새 프로젝트를 만들 때 대시 문자가 포함된 분기를 만들 수 없었습니다.

## 알려진 문제 {#known-issues}

* 모니터링 데이터가 새로 고쳐지면 숨겨진 모든 시리즈가 숨겨지지 않습니다.
* 기존 SLA 보고서를 보려는 고객은 다음 릴리스까지 수동으로 탐색해야 합니다.

   이 URL을 작성하려면 패턴(`https://<Experience Cloud URL>/content/mac/<Experience Cloud Tenant>/managedservices/sla.html`)을 따르십시오. 예를 들어, Experience Cloud의 URL이 (`https://weretailprod.experiencecloud.adobe.com`)이면 SLA 보고서 URL은 (`https://weretailprod.experiencecloud.adobe.com/content/mac/weretailprod/managedservices/sla/html`)입니다.

   이 문제는 다음 릴리스에서 SLA 보고서를 사용할 수 있게 됨에 따라 해결될 것으로 [!UICONTROL Cloud Manager]예상됩니다.
