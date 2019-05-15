---
title: 2018.7.0 릴리스 노트
seo-title: 2018.7.0 릴리스 노트
description: 'null'
seo-description: Cloud Manager 릴리스 2018.7.0에 대한 정보를 얻으려면 이 페이지를 따르십시오.
uuid: D 7 B 49 E 32-01 DC -48 CE-B 744-E 6 A 806 FBDD 8 A
contentOwner: Jsyal
topic-tags: 릴리스 노트
products: sg_ Experiencemanager/Cloudmanager
discoiquuid: b 64 bf 9 ab -27 ed -4 f 33-adc 8-d 73 d 34094 f 1 b
translation-type: tm+mt
source-git-commit: 1dfb065c09569f811e5a006d3d74825d3bd7cc8d

---


# 2018.7.0 릴리스 노트 {#release-notes-for}

다음 섹션에서는 [!UICONTROL Cloud Manager]*자동 크기 조절* 기능을 제공하는 2018.7.0 릴리스를 간략하게 설명합니다.

**프로덕션** 환경에서 `Dispatcher/Publish` 수평 크기 조정을 통해 자동 크기 조절이 활성화되어 로드, 볼륨, 액세스 및 기타 정의된 모니터링되는 지표의 급격한 증가를 지원합니다.

## 릴리스 날짜 {#release-date}

버전 2018.7.0 릴리스 [!UICONTROL Cloud Manager] 날짜는 2018 년 9 월 10 일입니다.

## 새로운 기능 {#what-s-new}

* **프로비저닝** - [!UICONTROL Cloud Manager] 이제 Dispatcher/Publish 세그먼트를 사용하여 수평 크기를 조절하여 고객 프로그램에서 프로덕션 환경의 크기를 자동 조정할 수 있습니다. UI의 새로운 부분은 고객 프로그램에서 자동 크기 조정을 사용하는 경우 표시되는 프로그램 설정의 프로비저닝 섹션입니다. 자세한 내용은 [프로그램](setting-up-program.md) 설정을 참조하십시오.

* **환경** - 이제 각 환경과 연관된 노드의 크기, 저장소, 영역 및 상태와 함께 프로덕션 및 스테이지 환경의 세부 보기를 볼 수 있습니다. 자세한 내용은 환경 [관리를](manage-your-environment.md) 참조하십시오.

* **코드 품질 분석** - 잘못된 API 사용을 식별하는 새 규칙입니다. 자세한 내용은 [사용자 지정 코드 품질 규칙을](custom-code-quality-rules.md) 참조하십시오.

* **성능 테스트** - 성능 테스트 결과를 보는 동안 CPU 사용률, 디스크 I/O 대기 시간, 디스크 I/O 대기 시간, 페이지 오류율, 네트워크 대역폭 사용률, 최대 페이지 응답 시간 및 95 번째 백분위수 페이지 응답 시간을 볼 수 있습니다. 테스트 [결과](understand-your-test-results.md) 페이지 이해에 대한 자세한 내용은 * Performance Testing * 섹션을 참조하십시오.

* **성능 테스트** - 성능 테스트 결과를 보는 동안 페이지 오류 및 느린 요청 목록을 다운로드할 수 있습니다. 테스트 [결과](understand-your-test-results.md) 페이지 이해에 대한 자세한 내용은 * Performance Testing * 섹션을 참조하십시오.

## 버그 수정 {#bug-fixes}

* 특정 상황에서 내부 시스템 동기화가 부적절하게 실패하여 일관되지 않은 데이터 보기로 이어졌습니다.
* 경우에 따라 수동 파이프라인 트리거가 자동으로 선택되지 않아 양식 유효성 검사 문제가 해결되었습니다.
* 특정 고객 빌드 스크립트가 플러그인 비호환성을 기반으로 하는 빌드 단계 중에 오류를 발생시킬 수 있습니다.

## 알려진 문제 {#known-issues}

* 고객이 커밋 트리거를 선택할 수 있지만, 파이프라인은 새 커밋을 기반으로 실제로 시작되지 않을 수 있습니다.
* [!UICONTROL Experience Cloud] 알림 사이드바는 알림을 일관되게 로드할 수 없습니다. 그러나 알림은에 [!UICONTROL Experience Cloud] 표시되며 구성된 경우 이메일을 통해 계속 전송됩니다.

