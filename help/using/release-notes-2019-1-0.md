---
title: 2019.1.0 릴리스 정보
seo-title: AEM Cloud Manager Release Notes for 2019.1.0
description: Cloud Manager 릴리스 2019.1.0에 대한 정보를 보려면 이 페이지를 따르십시오.
seo-description: Follow this page to get information for AEM Cloud Manager Release 2019.1.0.
uuid: 3af5808f-828f-4846-bee4-1e62194b48ad
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: release-notes
discoiquuid: 85a1dcf3-2eef-4ba8-b4d1-09e4a88c7bd0
feature: Release Information
exl-id: 383ca5a0-4b0b-48e9-aa48-1d1388875329
source-git-commit: 4f0e1d163001fd18cfa838256c813152d65c3b4c
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# 2019.1.0 릴리스 정보 {#release-notes-for}

다음 [!UICONTROL Cloud Manager] 2018.9.0 릴리스에는 AEM Assets 프로그램 테스트 및 빌드 및 코드 품질 단계를 실행하는 추가 파이프라인 유형이 추가되며, 선택적으로 비프로덕션 환경에 배포할 수 있습니다.

## 릴리스 날짜 {#release-date}

에 대한 릴리스 날짜 [!UICONTROL Cloud Manager] 버전 2019.1.0은 2019년 1월 17일입니다.

## 새로운 기능 {#whats-new}

* AEM Assets의 성능 테스트에 대한 지원이 추가되었습니다. 문서를 참조하십시오 [프로덕션 파이프라인 구성](configuring-production-pipelines.md) 추가 정보
* 비프로덕션 환경에 배포하는 빌드 및 코드 품질 단계와 파이프라인만 실행하는 파이프라인에 대한 지원이 추가되었습니다. 문서를 참조하십시오 [비프로덕션 파이프라인 구성](configuring-non-production-pipelines.md) 추가 정보
* 빌드 환경에서 사용자 지정 환경 변수에 대한 지원을 추가했습니다.
* 여러 단계 또는 프로덕션 환경을 사용하는 고객의 경우 프로덕션 파이프라인의 일부로 이 환경에 배포될 환경을 선택할 수 있습니다. 문서를 참조하십시오 [프로덕션 파이프라인 구성](configuring-production-pipelines.md) 추가 정보
* httxt2dbm이 빌드 컨테이너에 추가되었습니다.
* 모든 도움말 메뉴 항목에서 새 탭을 엽니다.

## 버그 수정 {#bug-fixes}

* 프로그램을 편집하는 동안 모든 페이지 세트를 선택 취소할 수 있었습니다.
* 승인 단계의 제목이 잘못 지정되었습니다.
* 경우에 따라 프로그램 로고가 잘못 매팅되었습니다.
* Dispatcher 구성 패키지만 빌드하면 배포 단계가 실패합니다.
* 콜드 대기 인스턴스가 포함된 환경이 올바르게 처리되지 않았습니다.
* 프로그램 전환기에 일부 종료된 프로그램이 나타났다.
* 파이프라인을 편집하는 동안 새 분기를 Git 리포지토리에 추가한 경우 즉시 선택할 수 없었을 수도 있습니다.
* 일부 화면에서 도움말 메뉴의 개발자 연결 아이콘이 표시되지 않았습니다.
* 탭 키가 Dispatcher 플러시 구성 대화 상자에서 제대로 처리되지 않았습니다.

## 알려진 문제 {#known-issues}

* Assets, KPI가 설정되지 않은 사이트가 있는 프로그램을 열면 모든 사용자는 **설치 프로그램** 버튼을 클릭합니다. 하지만 비즈니스 소유자 역할의 사용자만 실제로 **설치 프로그램** 버튼을 클릭합니다.
