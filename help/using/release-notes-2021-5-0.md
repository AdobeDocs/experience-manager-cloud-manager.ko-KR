---
title: 2021.5.0 릴리스 노트
description: Cloud Manager 릴리스 2021.5.0에 대한 정보를 보려면 이 페이지를 따르십시오
feature: 릴리스 정보
source-git-commit: 5111a918b8063ab576ef587dc3c8d66ad976fc1a
workflow-type: tm+mt
source-wordcount: '235'
ht-degree: 5%

---

# 2021.5.0 릴리스 노트 {#release-notes-for}

다음 섹션에서는 [!UICONTROL Cloud Manager] 릴리스 2021.5.0에 대한 일반 릴리스 노트를 간략하게 설명합니다.

>[!NOTE]
>AEM as a Cloud Service에서 Cloud Manager에 대한 최신 릴리스 노트를 보려면 [현재 릴리스 노트](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/getting-access/release-notes-cloud-manager/release-notes-cm-current.html?lang=en#getting-access)를 참조하십시오.

## 릴리스 날짜 {#release-date}

[!UICONTROL Cloud Manager] 버전 2021.5.0의 출시일은 2021년 5월 6일입니다.
다음 릴리스는 2021년 6월 10일에 예정되어 있습니다.

## 새로운 기능 {#whats-new}

* 이제 PackageOverlap 품질 규칙은 동일한 패키지가 동일한 배포된 패키지 세트에서 여러 포함된 위치에 여러 번 배포된 사례를 검색합니다.

* 이제 공용 API의 저장소 끝점에 Git URL이 포함됩니다.

* 프로그램 편집 워크플로우에서는 사용자가 십진수가 아닌 KPI 값만 설정할 수 있습니다.

* 코드를 Git Adobe으로 푸시하는 동안 발생하는 간헐적인 오류가 이제 해결되었습니다.

* 프로그램 편집 경험이 새로 고침되었습니다.

## 버그 수정 {#bug-fixes}

* 파이프라인 변수 API는 &#39;삭제됨&#39; 변수를 제거하는 대신 &#39;삭제됨&#39; 상태로만 표시합니다.

* 일부 코드 냄새 유형 품질 문제가 안정성 등급에 잘못 영향을 주었습니다.

* 자정~오전 1UTC 사이에 파이프라인 실행이 시작되면 Cloud Manager에서 생성한 아티팩트 버전이 전날 작성된 버전보다 클 수 없습니다.

* 특정 AMS(Adobe Managed Services) 고객이 Cloud Manager API를 사용하여 Adobe I/O 개발자 콘솔에서 새 프로젝트를 만들 수 없었습니다.
