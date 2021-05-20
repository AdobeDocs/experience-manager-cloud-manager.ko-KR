---
title: 2019.10.0 릴리스 노트
seo-title: 2019.10.0용 AEM Cloud Manager 릴리스 노트
description: Cloud Manager 릴리스 2019.10.0에 대한 정보를 보려면 이 페이지를 따르십시오.
seo-description: AEM Cloud Manager 릴리스 2019.10.0에 대한 정보를 보려면 이 페이지를 따르십시오.
feature: 릴리스 정보
exl-id: b58f7a1b-2063-4ac8-b676-bb74200d7ac9
source-git-commit: 43bb3c477ef9c1ce178509b8180479d7616edc66
workflow-type: tm+mt
source-wordcount: '248'
ht-degree: 5%

---

# 2019.10.0 릴리스 노트 {#release-notes-for}

다음 섹션에서는 [!UICONTROL Cloud Manager] 릴리스 2019.10.0에 대한 일반 릴리스 노트를 간략하게 설명하고 배포 단계 및 전문 프로젝트 버전 처리에 대한 업데이트를 추가합니다.
자세한 내용은 아래 섹션을 참조하십시오.

## 릴리스 날짜 {#release-date}

[!UICONTROL Cloud Manager] 버전 2019.10.0의 릴리스 날짜는 2019년 10월 10일입니다.

## 새로운 기능 {#whats-new}

* 배포 단계의 상당 부분이 더 성능이 향상되었습니다.
* 적절한 경우 빌드 Maven 프로젝트의 버전이 이제 git의 프로젝트 버전을 통합합니다.
* 빌드 시 새 환경 변수를 사용할 수 있습니다.
* API와 **개요** 페이지의 카드에서 비프로덕션 파이프라인을 삭제할 수 있습니다.
* 단계 배포 단계 직후, 보안 테스트 단계 전에 새로운 선택적 승인 단계가 있습니다.
* CI/CD 파이프라인을 구성할 때 개발 및 스테이지 환경에서 로드 밸런서에서 디스패처 인스턴스 분리 및 첨부를 건너뛸 수 있습니다.
자세한 내용은 **[배포 프로세스](deploying-code.md#deployment-process)**&#x200B;를 참조하십시오.
* 실행 단계 로그 액세스를 지원하기 위해 Cloud Manager CLI가 확장되었습니다.
* 이제 Cloud Manager API에서 파이프라인의 구성된 분기 편집을 지원합니다.
* 이제 성능 테스트 중에 실행된 요청에 사용자 에이전트의 특정 토큰 ***CloudManagerTest***&#x200B;가 포함됩니다.

## 버그 수정 {#bug-fixes}

* **개요** 페이지의 일부 카드가 세로로 제대로 정렬되지 않았습니다.
* 특정 실패 조건으로 인해 파이프라인 실행이 제대로 표시되고 후속 실행이 차단되지 않았습니다.
