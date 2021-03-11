---
title: 2021.2.0 릴리스 노트
seo-title: 2021.2.0용 AEM Cloud Manager 릴리스 노트
description: Cloud Manager 릴리스 2021.2.0에 대한 정보를 얻으려면 이 페이지를 따르십시오.
seo-description: AEM Cloud Manager 릴리스 2021.2.0에 대한 정보를 얻으려면 이 페이지를 따르십시오.
translation-type: tm+mt
source-git-commit: b5233e1932888b515d8dc26a6493cbd26686bc3c
workflow-type: tm+mt
source-wordcount: '244'
ht-degree: 4%

---

# 2021.2.0 릴리스 노트 {#release-notes-for}

다음 섹션에서는 [!UICONTROL Cloud Manager] 릴리스 2021.2.0에 대한 일반 릴리스 노트에 대해 간략하게 설명합니다.

## 릴리스 날짜 {#release-date}

[!UICONTROL Cloud Manager] 버전 2021.2.0의 릴리스 날짜는 2021년 2월 11일입니다.

## 새로운 기능 {#whats-new}

* 프로젝트 및 샌드박스 제작에서 사용되는 AEM 프로젝트 원형이 버전 25로 업데이트되었습니다.

* 코드 스캔 중에 식별된 가치 없는 API 목록은 최신 Cloud Service SDK 릴리스에서 사용되지 않는 추가 클래스 및 메서드를 포함하도록 개선되었습니다.

* 이제 프로덕션 배포가 쌍을 이룬 게시 및 디스패처 인스턴스와 동시에 배포됩니다.

* Cloud Manager용 SonarQube 프로필이 Sonar 규칙 `squid:S2142`을(를) 제거하도록 업데이트되었습니다. 더 이상 스레드 중단 검사와 충돌하지 않습니다.

* 음파 탐지 접두사가 있는 고객 `pom.xml` 파일에 설정된 속성은 이제 빌드 및 품질 스캔 오류를 방지하기 위해 동적으로 제거됩니다.

* Cloud Service 호환성 문제를 다루는 추가 코드 품질 규칙이 추가되었습니다.

## 버그 수정 {#bug-fixes}

* 경우에 따라 로드 테스트를 실행하는 컨테이너가 오류가 발생하여 성능 테스트 단계 중에 CI/CD(배포) 파이프라인이 실패했습니다.

* 경우에 따라 로드 테스트 컨테이너는 하나의 예외가 발생하더라도 실패한 것으로 실행을 보고할 수 있습니다. 테스트 프로세스를 복원할 수 없는 경우에만 오류가 보고됩니다.

* 환경 이름을 저장하는 방법 간에 일치하지 않는 경우 성능 테스트 오류가 발생합니다.

* 일부 파이프라인 오류가 파이프라인 오류로 잘못 보고되었습니다.