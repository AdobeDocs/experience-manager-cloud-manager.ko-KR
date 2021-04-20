---
title: 2019.10.0 릴리스 노트
seo-title: 2019.10.0용 AEM Cloud Manager 릴리스 노트
description: Cloud Manager 릴리스 2019.10.0에 대한 정보를 얻으려면 이 페이지를 따르십시오.
seo-description: AEM Cloud Manager 릴리스 2019.10.0에 대한 정보를 얻으려면 이 페이지를 따르십시오.
feature: Release Information
translation-type: tm+mt
source-git-commit: fb10d775c930b5bb475b497aac2fd59b053a9a00
workflow-type: tm+mt
source-wordcount: '248'
ht-degree: 5%

---

# 2019.10.0 릴리스 노트 {#release-notes-for}

다음 섹션에서는 [!UICONTROL Cloud Manager] 릴리스 2019.10.0에 대한 일반적인 릴리스 노트에 대해 간략하게 설명하고 배포 단계 및 고급 프로젝트 버전 처리에 대한 업데이트를 추가합니다.
자세한 내용은 아래 섹션을 참조하십시오.

## 릴리스 날짜 {#release-date}

[!UICONTROL Cloud Manager] 버전 2019.10.0의 릴리스 날짜는 2019년 10월 10일입니다.

## 새로운 기능 {#whats-new}

* 배포 단계의 중요한 부분이 더 높은 성능을 발휘했습니다.
* 해당되는 경우 빌드 Maven 프로젝트의 버전이 이제 git에 프로젝트 버전을 통합합니다.
* 작성 시 새 환경 변수를 사용할 수 있습니다.
* 비프로덕션 파이프라인은 API뿐만 아니라 **개요** 페이지의 카드에서 삭제할 수 있습니다.
* 단계 배포 단계 직후에 보안 테스트 단계 바로 전에 새로운 선택적 승인 단계가 있습니다.
* CI/CD 파이프라인을 구성할 때 개발 및 스테이지 환경에 대해 로드 밸런서에서 발송자 인스턴스 분리 및 연결을 건너뛸 수 있습니다.
자세한 내용은 **[배포 프로세스](deploying-code.md#deployment-process)**&#x200B;를 참조하십시오.
* 실행 단계 로그 액세스를 지원하기 위해 Cloud Manager CLI가 보강되었습니다.
* 이제 클라우드 관리자 API에서 파이프라인의 구성된 분기 편집을 지원합니다.
* 이제 성능 테스트 중에 실행되는 요청에 사용자 에이전트의 특정 토큰 ***CloudManagerTest***&#x200B;이 포함됩니다.

## 버그 수정 {#bug-fixes}

* **개요** 페이지의 일부 카드가 세로로 정렬되지 않았습니다.
* 특정 실패 조건으로 인해 파이프라인 실행이 제대로 표시되지 않고 후속 실행을 방지할 수 없습니다.
