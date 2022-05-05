---
title: 2022.5.0 릴리스 정보
description: 다음은 Cloud Manager 릴리스 2022.5.0의 릴리스 노트입니다.
feature: Release Information
exl-id: 2d38abb1-cfc7-44a9-b303-b555e2827eea
source-git-commit: 84cc4352488002ad40102ea2c507af652d9012a1
workflow-type: tm+mt
source-wordcount: '210'
ht-degree: 29%

---


# Cloud Manager 릴리스 2022.5.0의 릴리스 노트 {#release-notes}

이 페이지에서는 다음에 대한 릴리스 노트를 문서화합니다 [!UICONTROL Cloud Manager] 릴리스 2022.5.0.

>[!NOTE]
>
>AEM as a Cloud Service의 Cloud Manager 최신 릴리스 노트는 을 참조하십시오 [AEM as a Cloud Service의 현재 릴리스 노트에 있는 Cloud Manager.](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/release-notes-cloud-manager/release-notes-cm-current.html)

## 릴리스 날짜 {#release-date}

에 대한 릴리스 날짜 [!UICONTROL Cloud Manager] 릴리스 2022.5.0은 2022년 5월 5일입니다. 다음 릴리스는 2022년 6월 9일에 예정되어 있습니다.

## 새로운 기능 {#what-is-new}

이제 자산 테스트의 아웃바운드 HTTP 요청이 고정 IP 범위에서 제공됩니다.

## 버그 수정 {#bug-fixes}

* &quot;로드 밸런서 건너뛰기&quot; 변경 옵션을 사용하지 않도록 설정할 수 없습니다.
* 로드 밸런서 변경 건너뛰기 옵션이 AMS 개발 배포 편집 파이프라인 워크플로우에 표시되지 않았습니다.
* 수동으로 만든 GIT 저장소의 하위 집합에 잘못된 이름 값이 있어서 빌드 아티팩트 재사용 기능이 적용되지 않았습니다. 이들 저장소 이름이 변경되어 Cloud Manager API/UI에 수정한 이름이 표시됩니다.
* 비프로덕션 파이프라인의 빌드 아티팩트가 프로덕션 전체 스택 파이프라인에서 부적절하게 재사용되었습니다.
* 코드 품질 파이프라인을 추가 또는 편집하는 경우 지표 오류를 처리할 옵션이 더 이상 표시되지 않습니다.
* 일부 예기치 않은 파이프라인 변수 구성으로 인해 빌드 단계에서 오류가 발생할 수 있습니다.
