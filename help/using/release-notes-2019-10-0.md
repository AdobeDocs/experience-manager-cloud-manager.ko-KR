---
title: 2019.10.0 릴리스 노트
seo-title: 2019.10.0용 AEM Cloud Manager 릴리스 노트
description: Cloud Manager 릴리스 2019.10.0에 대한 정보를 얻으려면 이 페이지를 따르십시오.
seo-description: AEM Cloud Manager 릴리스 2019.10.0에 대한 정보를 얻으려면 이 페이지를 따르십시오.
translation-type: tm+mt
source-git-commit: 52c54568d8ab7b5091c25b3b65b4baa126bf61f5

---

# 2019.10.0 릴리스 노트 {#release-notes-for}

다음 섹션에서는 릴리스 2019.10.0 [!UICONTROL Cloud Manager] 에 대한 일반 릴리스 노트에 대해 간략하게 설명하고 배포 단계 및 전문적인 프로젝트 버전 처리에 대한 업데이트를 추가합니다.
자세한 내용은 아래 섹션을 참조하십시오.

## 릴리스 날짜 {#release-date}

버전 2019.10.0 [!UICONTROL Cloud Manager] 의 릴리스 날짜는 2019년 10월 10일입니다.

## 새로운 기능 {#whats-new}

* 배포 단계의 상당 부분이 더 성능이 향상되었습니다.
* 적절한 경우 빌드 Maven 프로젝트의 버전이 이제 git에 프로젝트 버전을 통합합니다.
* 작성 시 새 환경 변수를 사용할 수 있습니다.
* 비프로덕션 파이프라인은 개요 페이지 및 API의 **카드에서** 삭제할 수 있습니다.
* 단계 배포 단계 직후에 보안 테스트 단계 바로 전에 새로운 선택적 승인 단계가 있습니다.
* CI/CD 파이프라인을 구성할 때 개발 및 스테이지 환경에 대해 로드 밸런서로부터 발송자 인스턴스 분리 및 연결을 건너뛸 수 있습니다.
자세한 내용은 **[배포](deploying-code.md#deployment-process)** 프로세스를 참조하십시오.
* 실행 단계 로그 액세스를 지원하기 위해 Cloud Manager CLI가 향상되었습니다.
* 이제 Cloud Manager API는 파이프라인의 구성된 분기 편집을 지원합니다.
* 이제 성능 테스트 중에 실행된 요청에 사용자 ***에이전트에 특정*** 토큰 CloudManagerTest가 포함됩니다.

## 버그 수정 {#bug-fixes}

* 개요 페이지의 카드 중 **일부가** 세로로 정렬되지 않았습니다.
* 특정 실패 조건으로 인해 파이프라인 실행이 제대로 표시되지 않고 후속 실행을 방지했습니다.