---
title: 2023.9.0 릴리스 정보
description: 다음은 Cloud Manager 릴리스 2023.9.0의 릴리스 정보입니다.
feature: Release Information
exl-id: 2d38abb1-cfc7-44a9-b303-b555e2827eea
source-git-commit: 74381d5d154f7c61135a990d2806fa9e39be7690
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# Cloud Manager 릴리스 2023.9.0의 릴리스 정보 {#release-notes}

이 페이지는 [!UICONTROL Cloud Manager] 릴리스 2023.9.0에 대한 릴리스 정보를 설명합니다.

>[!NOTE]
>
>AEM as a Cloud Service에서 Cloud Manager에 대한 최신 릴리스 정보는 [AEM as a Cloud Service의 Cloud Manager 현재 릴리스 정보](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/release-notes-cloud-manager/release-notes-cm-current.html)를 참조하십시오.

## 릴리스 일자 {#release-date}

[!UICONTROL Cloud Manager] 릴리스 2023.9.0의 릴리스 날짜는 2023년 9월 7일입니다. 다음 릴리스는 2023년 10월 5일에 예정되어 있습니다.

## 새로운 기능 {#what-is-new}

이 릴리스에는 버그 수정이 포함됩니다.

## 버그 수정 {#bug-fixes}

* 프로그램이 삭제되면 연결된 실행 중인 파이프라인도 모두 삭제되어 파이프라인이 실패 상태로 잘못 지정되지 않도록 합니다.
* 경우에 따라 파이프라인 실행의 모든 단계가 &#39;완료&#39;되면 파이프라인의 상태가 &#39;실행 중&#39;으로 표시되어 중단 상태로 보일 수 있습니다. 이제 &#39;완료&#39;로 표시됩니다.
* 코드 생성기 Archetype을 사용하여 생성된 저장소 분기의 경우 CI/CD 파이프라인이 실패합니다.
