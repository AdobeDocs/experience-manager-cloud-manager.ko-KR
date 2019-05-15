---
title: 2018.6.0 릴리스 노트
seo-title: 2018.6.0 용 AEM Cloud Manager 릴리스 노트
description: Ollow 이 페이지를 참조하십시오.
seo-description: AEM Cloud Manager 릴리스 2018.6.0에 대한 정보를 얻으려면 이 페이지를 따르십시오.
uuid: 211 B 6 E 1 B -10 FB -46 B 0-B 591-44 D 5 E 44 ABD 77
contentOwner: Jsyal
products: sg_ Experiencemanager/Cloudmanager
topic-tags: 릴리스 노트
discoiquuid: 8584 F 467-3 E 61-41 EA -98 E 4-F 79 E 68 C 86469
translation-type: tm+mt
source-git-commit: 1dfb065c09569f811e5a006d3d74825d3bd7cc8d

---


# 2018.6.0 릴리스 노트 {#release-notes-for}

다음 섹션에서는 릴리스 2018.6.0에 대한 [!UICONTROL Cloud Manager] 일반 릴리스 노트에 대해 설명하고 배포, 추가 알림 및 유용성 개선 시 Dispatcher 무효화에 대한 지원을 추가합니다.

## 릴리스 날짜 {#release-date}

버전 2018.6.0 릴리스 [!UICONTROL Cloud Manager] 날짜는 2018 년 8 월 9 일입니다.

## 새로운 기능 {#what-s-new}

* **CI/CD 파이프라인** - CI/CD 파이프라인 실행 동안 스테이지와 프로덕션 모두에서 구성 가능한 Dispatcher Invalidation 및 캐시 플러싱을 수행할 수 있습니다. 자세한 내용은 [CI/CD 파이프라인](configuring-pipeline.md) 구성을 참조하십시오.

* **CI/CD 파이프라인** - 파이프라인 설정 중에 이제 품질 게이트 중 하나에서 중요한 실패가 발생하면 파이프라인이 작동 방식을 정의할 수 있습니다. 자세한 내용은 [CI/CD 파이프라인](configuring-pipeline.md) 구성을 참조하십시오.

* **CI/CD 파이프라인** - Pipeline 설정 중에 CSE 또는 사용 가능한 CSE에서 CSE Manager를 수행할지 여부를 선택할 수 있습니다. 자세한 내용은 [CI/CD 파이프라인](configuring-pipeline.md) 구성을 참조하십시오.

* **CI/CD 파이프라인** - CI/CD 파이프라인이 비즈니스 승인 단계에 도달하면 배포를 승인할 권한이 있는 사용자에게 알림이 전송됩니다. 자세한 내용은 [알림을](notifications.md) 참조하십시오.

* **CI/CD 파이프라인** - CI/CD 파이프라인이 예약 세트에 도달하면 일정을 설정할 권한이 있는 사용자에게 알림이 전송됩니다. 자세한 내용은 [알림을](notifications.md) 참조하십시오.

* **코드 품질 분석** - 잘못된 구성된 아웃바운드 HTTP/HTTPS 요청을 식별하는 새 규칙입니다. 자세한 내용은 [사용자 지정 코드 품질 규칙을](custom-code-quality-rules.md) 참조하십시오.

## 버그 수정 {#bug-fixes}

* 경우에 따라 성능 테스트가 여러 디스패처 및 게시 인스턴스에 완전히 배포되지 않았습니다.
* 좁은 브라우저 창에서 헤더 탐색이 사라졌습니다.
* 파이프라인이 실행 중일 때 일부 파이프라인 설정이 비활성화되지 않았습니다.
* 프로그램 목록 화면에서 AEM 및 모니터링에 대한 링크가 현재 브라우저 탭을 대체하고 새 탭을 열었습니다.
* 경우에 따라 장기간의 승인 기간이 길어질 경우 배포에 실패할 수 있습니다.
