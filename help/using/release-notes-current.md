---
title: 2021.7.0 릴리스 노트
description: Cloud Manager 릴리스 2021.7.0에 대한 정보를 보려면 이 페이지를 따르십시오
feature: 릴리스 정보
source-git-commit: 1da4ceef0d89223580800d9018c46aaec51f8927
workflow-type: tm+mt
source-wordcount: '259'
ht-degree: 6%

---

# 2021.7.0 릴리스 노트 {#release-notes-for}

다음 섹션에서는 [!UICONTROL Cloud Manager] 릴리스 2021.7.0에 대한 일반 릴리스 노트를 간략하게 설명합니다.

>[!NOTE]
>AEM as a Cloud Service에서 Cloud Manager에 대한 최신 릴리스 노트를 보려면 [현재 릴리스 노트](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/getting-access/release-notes-cloud-manager/release-notes-cm-current.html?lang=en#getting-access)를 참조하십시오.

## 릴리스 날짜 {#release-date}

[!UICONTROL Cloud Manager] 버전 2021.7.0의 출시일은 2021년 7월 15일입니다.
다음 릴리스는 2021년 8월 12일에 예정되어 있습니다.

## 새로운 기능 {#whats-new}

* 고객은 이제 Cloud Manager 빌드 프로세스에 Azul 8 및 11개의 JDK를 사용할 수 있으며 이러한 JDK 중 하나를 도구 체인 호환 Maven 플러그인 *또는 전체 Maven 프로세스 실행에 사용하도록 선택할 수 있습니다.*

* 이제 아웃바운드 송신 IP가 빌드 단계 로그 파일에 기록됩니다.

* **Git** 관리 단추가 **Access Git Info**&#x200B;로 변경되었으며 대화 상자가 시각적으로 새로 고침되었습니다.

* Cloud Manager에서 사용하는 AEM Project Archetype 버전이 버전 28로 업데이트되었습니다.

* 일부 예기치 않은 토폴로지 재구성으로 인해 파이프라인 실행 세부 정보 페이지에서 더 이상 세부 테스트 보고서를 사용할 수 없게 될 수 있습니다.

## 버그 수정 {#bug-fixes}

* 존재하지 않는 실행을 위한 실행 세부 사항 페이지로 수동으로 탐색해도 오류가 표시되지 않고 끝없이 로드되는 화면만 표시됩니다.

* 경우에 따라 사이트 성능에 사용된 실패한 컨테이너에 대한 자동 재시도는 2시간 동안 적용되지 않아 테스트 오류가 발생합니다.

## 알려진 문제 {#known-issues}

Azul JDK를 사용하도록 전환하는 고객은 Azul JDK에 오류가 없는 모든 기존 애플리케이션이 컴파일되는 것은 아니라는 것을 알고 있어야 합니다. 전환하기 전에 로컬로 테스트하는 것이 좋습니다.