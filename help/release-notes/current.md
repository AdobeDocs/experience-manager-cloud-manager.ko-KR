---
title: 2022.9.0 릴리스 정보
description: 다음은 Cloud Manager 릴리스 2022.9.0의 릴리스 노트입니다.
feature: Release Information
exl-id: 2d38abb1-cfc7-44a9-b303-b555e2827eea
source-git-commit: e74d386d0b2d50a7e276bb7ead7594ef448742ae
workflow-type: tm+mt
source-wordcount: '196'
ht-degree: 4%

---


# Cloud Manager 릴리스 2022.9.0 릴리스 노트 {#release-notes}

이 페이지에서는 다음에 대한 릴리스 노트를 문서화합니다 [!UICONTROL Cloud Manager] 릴리스 2022.9.0.

>[!NOTE]
>
>AEM as a Cloud Service의 Cloud Manager 최신 릴리스 노트는 을 참조하십시오 [AEM as a Cloud Service의 현재 릴리스 노트에 있는 Cloud Manager.](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/release-notes-cloud-manager/release-notes-cm-current.html)

## 릴리스 날짜 {#release-date}

에 대한 릴리스 날짜 [!UICONTROL Cloud Manager] 릴리스 2022.9.0은 2022년 9월 8일입니다. 다음 릴리스는 2022년 10월 6일에 예정되어 있습니다.

## 새로운 기능 {#what-is-new}

* 수평 다중 영역 자동 크기 조절을 위한 Cloud Manager 지원.
* AEM 환경 및 제한된 프로그램 액세스 방법에 대해 안내하는 Cloud Manager 사용자 역할만 있는 사용자를 위해 사용자 지정된 새로운 시작 페이지 카드.
* Cloud Manager 역할이 없는 고객은 프로그램 세부 사항에 액세스할 수 없습니다. 그러나 CM 랜딩 페이지에서 작성자 끝점(Author end point)으로 이동할 수 있습니다.
* 복원력을 강화하여 재시도에서 발생하는 파이프라인 실패를 제거합니다.

## 버그 수정 {#bug-fixes}

* maven이 개인 보고서에 대한 연결 문제가 발생할 때 customer AEM 앱 빌드와 관련된 고객 피드백이 개선되었습니다.
* 드문 경우이지만 상태 확인 시스템에서 유효한 상태 점수를 검색할 수 없는 경우 자동 크기 조정 이벤트가 트리거되지 않습니다.
