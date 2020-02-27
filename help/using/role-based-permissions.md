---
title: 역할 기반 권한
description: 역할 기반 권한에 대해 알려면 이 페이지를 따르십시오.
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: introduction
discoiquuid: 67a54bae-99a9-4405-91e3-9a0a8b3ccc98
translation-type: tm+mt
source-git-commit: a038a3d6e35ff28190441e9d11d9c539641a85af

---


# 역할 기반 권한 {#role-based-permissions}

[!UICONTROL Cloud Manager] 에 적절한 권한이 있는 사전 구성된 역할이 있습니다. 예를 들어 개발자는 코드를 개발하고 코드를 Git 리포지토리로 푸시할 수 있는 권한을 **갖습니다**. 또는 비즈니스 소유자는 KPI(Key Performance Indicator)를 정의하고 배포를 승인할 수 있는 다양한 권한을 갖습니다.

## 사용자 역할 {#user-roles}

의 역할 관리는 [!UICONTROL Cloud Manager] Adobe Admin Console에서 [수행됩니다](https://helpx.adobe.com/enterprise/using/admin-console.html). 모든 사용자는 고객의 IMS 조직에 소속되어 있고 Adobe Managed Services 제품 컨텍스트를 가지고 있어야 [!UICONTROL Cloud Manager] 합니다. 관리 콘솔에서 사용자를 제품 프로필에 추가하여 특정 [!UICONTROL Cloud Manager] 역할 멤버십이 제공됩니다.

역할을 설정하는 방법에 대한 자세한 내용은 사용자 및 [역할 설정을 참조하십시오](setting-up-users-and-roles.md).

다음 표 목록은 관리 콘솔에서 지정할 수 있는 역할을 정의합니다.

| **[!UICONTROL Cloud Manager]역할&#x200B;** | **설명** |
|---|---|
| 비즈니스 소유자 | 초기 [!UICONTROL Cloud Manager] 설정을 완료한 주 사용자. KPI 정의, 프로덕션 배포 승인, 중요한 3단계 장애 무시 등의 책임입니다. |
| 프로그램 관리자 | 팀 설정을 [!UICONTROL Cloud Manager] 수행하고 상태를 검토하고 KPI를 보는 데 사용합니다. 중요한 3단계 오류를 승인할 수 있습니다. |
| 배포 관리자 | 배포 작업을 관리합니다. 스테이지 및 프로덕션 배포를 실행하는 [!UICONTROL Cloud Manager] 데 사용됩니다. 중요한 3단계 오류를 승인할 수 있습니다. Git 리포지토리에 액세스 권한이 있습니다. |
| 개발자 | 사용자 정의 애플리케이션 코드를 개발하고 테스트합니다. 주로 상태를 보는 [!UICONTROL Cloud Manager] 데 사용됩니다. Git 리포지토리에 대한 액세스 권한을 커밋했습니다. |
| 고객 성공 엔지니어 | 일반적으로 AMS 고객의 성공을 지원합니다. CSE(Customer Success Engineer) 감독을 필요로 하는 배포 실행을 [!UICONTROL Cloud Manager] 위한 목적으로 상호 작용합니다. |
| 컨텐츠 작성자 | 일반적으로 상호 작용하지 않습니다 [!UICONTROL Cloud Manager]. 이 사용자는 프로그램 전환기( [!UICONTROL Cloud Manager] 이동 중)를 사용하여 AEM(Adobe Experience Manager) [!UICONTROL Experience Cloud]에 액세스할 수 있습니다. |

## 사용자 권한 {#user-permissions}

각 역할에는 각 역할과 연관된 특정 권한, 사전 구성된 작업 또는 권한이 있습니다. 이 표에는 사용할 수 있는 기능과 함수를 실행할 수 있는 역할이 나열됩니다.

사용자를 설정하는 방법에 대한 자세한 내용은 사용자 및 역할 [설정을 참조하십시오](setting-up-users-and-roles.md).

| 권한 | 설명 | 비즈니스 소유자 | 배포 관리자 | 프로그램 관리자 | 개발자 | CSE |
|--- |--- |--- |--- |--- |--- |--- |
| 애플리케이션 읽기 | 프로그램 KPI 읽기 | x | x | x | x | x |
| 애플리케이션 쓰기 | 프로그램 설정 또는 편집 | x |  |  |  |  |
| 읽기 환경 | 환경 세부 사항을 참조하십시오. | x | x | x | x | x |
| 실행 만들기 | 파이프라인 시작을 참조하십시오. | x | x | x |  |  |
| 읽기 실행 | 실행 상태를 참조하십시오. | x | x | x | x | x |
| 실행 다시 시작 | 일시 중지 시 실행을 다시 시작할 수 있습니다. | x | x | x |  | x |
| 프로덕션에 배포 승인 실행 | GoLive 승인을 제공합니다. | x | x | x |  |  |
| 프로덕션에 배포 실행 일정 | 프로덕션 배포 일정을 참조하십시오. | x | x | x |  | x |
| 프로덕션에 배포 실행 | CSE 감독을 위해 애플리케이션을 일시 중지하면 프로덕션에 배포 |  |  |  |  | x |
| 실행 취소 | 현재 실행을 취소합니다. | x | x | x |  |  |
| 실행 재정의 품질 게이트 실패 | 중요 품질 게이트 실패 승인. | x | x | x |  |  |
| 파이프라인 만들기 | 파이프라인 설정/편집을 참조하십시오. |  | x |  |  |  |
| 파이프라인 읽기 | 자세한 내용은 파이프라인 세부 정보를 참조하십시오. | x | x | x | x | x |
| 파이프라인 쓰기 | 파이프라인 설정/편집을 참조하십시오. |  | x |  |  |  |
| 파이프라인 수정 승인 | 비즈니스 소유자 옵션을 편집할 수 있습니다. |  | x |  |  |  |
| 파이프라인 수정 관리 배포 | CSE 감독 옵션을 편집할 수 있습니다. |  | x |  |  |  |
| 단계 읽기 | 단계 품질 지표 결과를 참조하십시오. | x | x | x | x | x |
