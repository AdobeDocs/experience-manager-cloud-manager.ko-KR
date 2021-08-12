---
title: 2021.8.0 릴리스 노트
description: Cloud Manager 릴리스 2021.8.0에 대한 정보를 보려면 이 페이지를 따르십시오
feature: 릴리스 정보
source-git-commit: 510c523423a8d7cf9ad4c5ba2af11ff12df2b1cc
workflow-type: tm+mt
source-wordcount: '169'
ht-degree: 8%

---

# 2021.8.0 릴리스 노트 {#release-notes-for}

다음 섹션에서는 [!UICONTROL Cloud Manager] 릴리스 2021.8.0에 대한 일반 릴리스 노트를 간략하게 설명합니다.

>[!NOTE]
>AEM as a Cloud Service에서 Cloud Manager에 대한 최신 릴리스 노트를 보려면 [현재 릴리스 노트](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/getting-access/release-notes-cloud-manager/release-notes-cm-current.html?lang=en#getting-access)를 참조하십시오.

## 릴리스 날짜 {#release-date}

[!UICONTROL Cloud Manager] 버전 2021.8.0의 출시일은 2021년 8월 12일입니다.
다음 릴리스는 2021년 9월 9일에 예정되어 있습니다.

## 새로운 기능 {#whats-new}

* 사용자가 Cloud Manager UI를 통해 여러 저장소를 만들고 관리할 수 있는 셀프 서비스 기능입니다.

* SonarQube가 불필요하게 Git 내역 데이터를 읽고 있었습니다. 큰 코드 베이스에서 이로 인해 불필요한 빌드 성능 벌금이 발생할 수 있습니다.

* 이제 파이프라인당 Maven 종속성 캐시를 무효화하는 데 사용할 수 있는 API가 있습니다.

* Cloud Manager에서 사용하는 AEM Project Archetype 버전이 버전 28로 업데이트되었습니다.

## 버그 수정 {#bug-fixes}

* 경우에 따라 파이프라인이 두 번 트리거되면 *이(가) 파이프라인 실행 상태* 오류로 인해 실행 중 하나가 실패하는 경우가 있습니다.
