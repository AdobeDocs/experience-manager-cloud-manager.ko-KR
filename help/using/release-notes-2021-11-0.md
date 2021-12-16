---
title: 2021.11.0 릴리스 노트
description: Cloud Manager 릴리스 2021.11.0에 대한 정보를 보려면 이 페이지를 따르십시오
feature: Release Information
exl-id: 2d38abb1-cfc7-44a9-b303-b555e2827eea
source-git-commit: 6852df51d4b9b4947f1d5ce0b5a284bef94d0589
workflow-type: tm+mt
source-wordcount: '368'
ht-degree: 3%

---

# 2021.11.0 릴리스 노트 {#release-notes-for}

다음 섹션에서는 다음에 대한 일반 릴리스 노트를 간략하게 설명합니다 [!UICONTROL Cloud Manager] 릴리스 2021.11.0.

>[!NOTE]
>을(를) 참조하십시오. [현재 릴리스 노트](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/getting-access/release-notes-cloud-manager/release-notes-cm-current.html?lang=en#getting-access) AEM as a Cloud Service에서 Cloud Manager에 대한 최신 릴리스 노트를 보려면 확인하십시오.

## 릴리스 날짜 {#release-date}

에 대한 릴리스 날짜 [!UICONTROL Cloud Manager] 버전 2021.11.0은 2021년 11월 4일입니다.
다음 릴리스는 2021년 12월 16일에 예정되어 있습니다.

## 새로운 기능 {#whats-new}

* 이제 Git 커밋 ID가 파이프라인 실행 세부 사항에 표시되므로 빌드된 코드를 쉽게 추적할 수 있습니다.

* 다음 `x-request-id` 이제 응답 헤더가 의 API Playground에 표시됩니다. [www.adobe.io](https://www.adobe.io/). 이 헤더는 문제 해결을 위해 고객 지원 문제를 제출할 때 유용합니다.

* 사용자는 파이프라인이 없는 파이프라인 카드에 적절한 지침이 제공됩니다.

* 이제 연관된 세부 사항과 함께 파이프라인 및 코드 실행과 같은 활동을 볼 수 있는 새로운 활동 페이지를 사용할 수 있습니다. 시간이 지나면서 이 페이지에 나열된 활동은 제공된 세부 정보와 함께 범위가 확장됩니다.

* 이제 세부 사항 요약을 쉽게 볼 수 있도록 마우스로 가리키면 상태 팝오버가 있는 새 파이프라인 페이지를 사용할 수 있습니다. 파이프라인 실행은 연관된 세부 정보와 함께 볼 수 있습니다.

* 이제 파이프라인 편집 API에서 디스패처 무효화 및 플러시 경로 설정을 지원합니다.

* 이제 파이프라인 편집 API에서 배포 단계에서 사용되는 환경 변경을 지원합니다.

* 큰 패키지에 대해 OakPal 검색 프로세스의 최적화가 도입되었습니다.

* 이제 품질 문제 CSV 파일에 각 품질 문제에 대한 타임스탬프가 포함됩니다.

* 환경 페이지의 관리 단추는 더 이상 UI에 표시되지 않습니다.

## 버그 수정 {#bug-fixes}

* 특정 비정형 빌드 구성은 빌드 컨테이너를 시작 및 중지할 때 외부 네트워크 I/O를 발생시킨 파이프라인의 Maven 아티팩트 캐시에 불필요한 파일이 저장되었습니다.

* 배포 단계가 없는 경우 파이프라인 PATCH API가 실패합니다.

* 다음 `ClientlibProxyResourceCheck` 일반적인 기본 경로가 있는 클라이언트 라이브러리가 있을 때 품질 규칙이 긍정 오류(false positive)를 생성하는 것이었습니다.

* 최대 저장소 수에 도달했을 때 오류 메시지에 오류 이유를 지정하지 않았습니다.

* 드문 경우이지만 특정 응답 코드를 잘못 처리하여 파이프라인이 실패했습니다.
