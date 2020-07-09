---
title: 2020.7.0 릴리스 노트
seo-title: 2020.7.0용 AEM Cloud Manager 릴리스 노트
description: Cloud Manager 릴리스 2020.7.0에 대한 정보를 얻으려면 이 페이지를 따르십시오
seo-description: AEM Cloud Manager 릴리스 2020.7.0에 대한 정보를 얻으려면 이 페이지를 따르십시오
translation-type: tm+mt
source-git-commit: 33aeba59c149e5ba3300b9d798356ec5e9bcd4b8
workflow-type: tm+mt
source-wordcount: '157'
ht-degree: 8%

---

# 2020.7.0 릴리스 노트 {#release-notes-for}

다음 섹션에서는 릴리스 2020.7.0 [!UICONTROL Cloud Manager] 에 대한 일반 릴리스 노트에 대해 간략하게 설명합니다.

## 릴리스 날짜 {#release-date}

버전 2020.7.0 [!UICONTROL Cloud Manager] 의 릴리스 날짜는 2020년 7월 09일입니다.

## 새로운 기능 {#whats-new}

* 프로덕션 배포 시 로드 밸런서에서 디스패처 인스턴스를 분리 및 첨부하면 보다 일관된 방식으로 작동합니다.

* 이제 클라우드 관리자 빌드 컨테이너가 Java 8과 Java 11을 모두 지원합니다.


## 버그 수정 {#bug-fixes}

* 비프로덕션 파이프라인 편집 페이지의 **취소** 및 **저장** 옵션이 항상 표시되는 것은 아닙니다.

* 코드 품질 프로세스의 일부 오류로 인해 로그 파일이 올바로 생성되지 않을 수 있습니다.

* 일부 큰 파이프라인 단계 로그를 사용자 인터페이스를 통해 일관되게 다운로드할 수 없습니다.

## 알려진 문제 {#known-issues}

* AMS 환경에 대기 인스턴스가 포함되어 있으면, 기록된 메시지는 대기 모드에 비해 인스턴스가 다운되었음을 나타냅니다.
