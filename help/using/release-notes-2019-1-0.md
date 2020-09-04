---
title: 2019.1.0 릴리스 노트
seo-title: AEM Cloud Manager 2019.1.0용 릴리스 노트
description: Cloud Manager 릴리스 2019.1.0에 대한 정보를 얻으려면 이 페이지를 따르십시오.
seo-description: AEM Cloud Manager 릴리스 2019.1.0에 대한 정보를 얻으려면 이 페이지를 따르십시오.
uuid: 3af5808f-828f-4846-bee4-1e62194b48ad
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: release-notes
discoiquuid: 85a1dcf3-2eef-4ba8-b4d1-09e4a88c7bd0
translation-type: tm+mt
source-git-commit: c35398110e9d8311bf58f217efdd082cf0cfd90a
workflow-type: tm+mt
source-wordcount: '335'
ht-degree: 4%

---


# 2019.1.0 릴리스 노트 {#release-notes-for}

2018.9.0 릴리스는 AEM Assets 프로그램 및 빌드 및 코드 품질 단계를 실행하는 추가 파이프라인 유형을 비롯하여 비프로덕션 환경에 선택적으로 배포할 수 있는 지원을 추가합니다. [!UICONTROL Cloud Manager]

## 릴리스 날짜 {#release-date}

버전 2019.1.0 [!UICONTROL Cloud Manager] 의 릴리스 날짜는 2019년 1월 17일입니다.

## 새로운 기능 {#whats-new}

* AEM Assets의 성능 테스트에 대한 지원이 추가되었습니다. 자세한 내용은 [CI/CD](configuring-pipeline.md)파이프라인 구성을 참조하십시오.
* 비프로덕션 환경에 배포되는 빌드 및 코드 품질 단계만 실행되는 파이프라인에 대한 지원이 추가되었습니다. 자세한 내용은 **CI/CD 파이프라인** 구성의 비프로덕션 및 코드 품질만 파이프라인 [](configuring-pipeline.md) 섹션을 참조하십시오.
* 빌드 환경에서 사용자 지정 환경 변수에 대한 지원을 추가했습니다.
* 여러 단계 또는 프로덕션 환경을 보유한 고객의 경우 프로덕션 파이프라인의 일부로 배포될 환경을 선택할 수 있습니다. CI/ [CD 파이프라인](configuring-pipeline.md) 구성 페이지에서 사용할 수 있습니다.
* httxt2dbm이 빌드 컨테이너에 추가되었습니다.
* 모든 도움말 메뉴 항목이 새 탭을 엽니다.

## 버그 수정 {#bug-fixes}

* 프로그램을 편집하는 동안 모든 페이지 세트를 선택 해제할 수 있었습니다.
* 승인 단계의 제목이 잘못 지정되었습니다.
* 경우에 따라 프로그램 로고가 잘못 매팅되었습니다.
* 발송자 구성 패키지만 빌드하면 배포 단계가 실패합니다.
* 콜드 대기 인스턴스가 포함된 환경이 올바르게 처리되지 않았습니다.
* 프로그램 전환기에 일부 종료된 프로그램이 나타났다.
* 파이프라인을 편집하는 동안 새 분기가 git 리포지토리에 추가된 경우 즉시 선택 가능하지 않았을 수 있습니다.
* 일부 화면에서 도움말 메뉴의 개발자 연결 아이콘이 표시되지 않았습니다.
* 발송자 플러싱 구성 대화 상자에서 탭 키가 제대로 처리되지 않았습니다.

## 알려진 문제 {#known-issues}

* KPI가 설정된 사이트(자산)가 아닌 사이트를 포함하는 프로그램을 열 때 모든 사용자는 프로그램 **설정** 단추가 있는 클릭 유도 문안을 볼 수 있습니다. 하지만 비즈니스 소유자 역할의 사용자만 프로그램 **설정 단추를 실제로 클릭할 수** 있습니다.