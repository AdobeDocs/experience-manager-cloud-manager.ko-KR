---
title: 2018.6.0 릴리스 노트
seo-title: AEM Cloud Manager 2018.6.0용 릴리스 노트
description: Cloud Manager 릴리스 2018.6.0에 대한 정보를 보려면 이 페이지를 클릭하십시오.
seo-description: AEM Cloud Manager 릴리스 2018.6.0에 대한 정보를 얻으려면 이 페이지를 따르십시오.
uuid: 211b6e1b-10fb-46b0-b591-44d5e44abd77
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: release-notes
discoiquuid: 8584f467-3e61-41ea-98e4-f79e68c86469
translation-type: tm+mt
source-git-commit: 15f75ca67c3d52ae511357c5b564daaa3d9def6b
workflow-type: tm+mt
source-wordcount: '334'
ht-degree: 3%

---


# 2018.6.0 릴리스 노트 {#release-notes-for}

다음 섹션에서는 [!UICONTROL Cloud Manager] 릴리스 2018.6.0에 대한 일반 릴리스 노트에 대한 개요를 설명하고 배포 중 무효화에 대한 지원, 추가 알림 및 유용성 개선 기능을 추가합니다.

## 릴리스 날짜 {#release-date}

[!UICONTROL Cloud Manager] 버전 2018.6.0의 릴리스 날짜는 2018년 8월 9일입니다.

## 새로운 기능 {#what-s-new}

* **CI/CD 파이프라인**  - CI/CD 파이프라인 실행 중 스테이지와 프로덕션 모두에서 구성 가능한 디스패처 무효화 및 캐시 플러싱. 자세한 내용은 [CI/CD 파이프라인 구성](configuring-pipeline.md)을 참조하십시오.

* **CI/CD 파이프라인**  - 이제 파이프라인을 설정하는 동안 품질 문 중 하나에서 중요 오류가 발생할 때 파이프라인이 어떻게 작동하는지 정의할 수 있습니다. 자세한 내용은 [CI/CD 파이프라인 구성](configuring-pipeline.md)을 참조하십시오.

* **CI/CD 파이프라인**  - 이제 파이프라인 설정 중에 CSE 감독을 CSE 또는 사용 가능한 CSE에서 수행할지 여부를 선택할 수 있습니다. 자세한 내용은 [CI/CD 파이프라인 구성](configuring-pipeline.md)을 참조하십시오.

* **CI/CD 파이프라인**  - CI/CD 파이프라인이 비즈니스 승인 단계에 도달하면 배포를 승인할 권한이 있는 사용자에게 알림이 전송됩니다. 자세한 내용은 [알림](notifications.md)을 참조하십시오.

* **CI/CD 파이프라인**  - CI/CD 파이프라인이 일정 세트에 도달하면 일정을 설정할 수 있는 권한이 있는 사용자에게 알림이 전송됩니다. 자세한 내용은 [알림](notifications.md)을 참조하십시오.

* **코드 품질 분석**  - 잘못 구성된 아웃바운드 HTTP/HTTPS 요청을 식별하는 새로운 규칙입니다. 자세한 내용은 [사용자 지정 코드 품질 규칙](custom-code-quality-rules.md)을 참조하십시오.

## 버그 수정 {#bug-fixes}

* 경우에 따라 성능 테스트가 여러 디스패처 및 게시 인스턴스에 걸쳐 완전히 배포되지 않았습니다.
* 좁은 브라우저 창에서 헤더 내비게이션이 사라졌습니다.
* 파이프라인이 실행되는 동안 일부 파이프라인 설정을 사용하지 않도록 설정하지 않았습니다.
* AEM 및 프로그램 목록 화면에서 모니터링에 대한 링크가 현재 브라우저 탭을 대체하고 새 탭을 열었습니다.
* 특정 상황에서 긴 승인 기간이 길면 배포에 실패할 수 있습니다.
