---
title: 역할 기반 권한
description: 역할 기반 권한에 대해 알려면 이 페이지를 따르십시오.
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: introduction
discoiquuid: 67a54bae-99a9-4405-91e3-9a0a8b3ccc98
feature: 사용자 역할
exl-id: b66533fb-db93-40e8-919d-581261fdbf24
source-git-commit: 43bb3c477ef9c1ce178509b8180479d7616edc66
workflow-type: tm+mt
source-wordcount: '519'
ht-degree: 17%

---

# 역할 기반 권한 {#role-based-permissions}

[!UICONTROL Cloud Manager] 에는 적절한 권한이 있는 미리 구성된 역할이 있습니다. 예를 들어, 개발자는 코드를 개발하고 **Git 리포지토리**&#x200B;에 코드를 푸시할 수 있는 권한이 있습니다. 또는 비즈니스 소유자에게는 KPI(주요 성과 지표)를 정의하고 배포를 승인할 수 있는 다양한 권한이 있습니다.

## 사용자 역할 {#user-roles}

[!UICONTROL Cloud Manager]에 대한 역할 관리는 [Adobe Admin Console](https://helpx.adobe.com/kr/enterprise/using/admin-console.html) 내에서 수행됩니다. [!UICONTROL Cloud Manager]의 모든 사용자는 고객의 IMS 조직의 구성원이어야 하며 Adobe Managed Services 제품 컨텍스트가 있어야 합니다. 특정 역할 멤버십은 사용자를 Admin Console의 [!UICONTROL Cloud Manager] 제품 프로필에 추가하여 제공합니다.

역할 설정 방법에 대한 자세한 내용은 [사용자 및 역할 설정](setting-up-users-and-roles.md)을 참조하십시오.

다음 테이블 목록은 Admin Console에서 지정할 수 있는 역할을 정의합니다.

| **[!UICONTROL Cloud Manager]역할** | **설명** |
|---|---|
| 비즈니스 소유자 | 초기 [!UICONTROL Cloud Manager] 설정을 완료하는 기본 사용자입니다. KPI 정의, 프로덕션 배포 승인 및 중요한 3계층 실패 재정의에 책임이 있습니다. |
| 프로그램 관리자 | [!UICONTROL Cloud Manager] 을 사용하여 팀 설정, 상태 검토 및 KPI 보기를 수행합니다. 중요한 3계층 오류를 승인할 수 있습니다. |
| 배포 관리자 | 배포 작업을 관리합니다. [!UICONTROL Cloud Manager] 을 사용하여 스테이지 및 프로덕션 배포를 실행합니다. 중요한 3계층 오류를 승인할 수 있습니다. Git 리포지토리에 액세스할 수 있습니다. |
| 개발자 | 사용자 지정 응용 프로그램 코드를 개발하고 테스트합니다. 주로 [!UICONTROL Cloud Manager]을 사용하여 상태를 봅니다. Git 리포지토리에 대한 커밋 액세스 권한이 있습니다. |
| 고객 성공 엔지니어 | 일반적으로 AMS 고객에 대한 고객 성공을 지원합니다. CSE(Customer Success Engineer) 감독을 필요로 하는 배포를 실행하기 위해 는 [!UICONTROL Cloud Manager]과 상호 작용합니다. |
| 컨텐츠 작성자 | 일반적으로 는 [!UICONTROL Cloud Manager]과 상호 작용하지 않습니다. 이 사용자는 [!UICONTROL Cloud Manager] 프로그램 전환기([!UICONTROL Experience Cloud]에서 이동한)를 사용하여 Adobe Experience Manager(AEM)에 액세스할 수 있습니다. |

## 사용자 권한 {#user-permissions}

각 역할에는 특정 권한, 사전 구성된 작업 또는 각 역할에 연관된 권한이 있습니다. 이 표에는 사용 가능한 기능과 기능을 실행할 수 있는 역할이 나열됩니다.

사용자 설정 방법에 대한 자세한 내용은 [사용자 및 역할 설정](setting-up-users-and-roles.md)을 참조하십시오.

| 권한 | 설명 | 비즈니스 소유자 | 배포 관리자 | 프로그램 관리자 | 개발자 | CSE |
|--- |--- |--- |--- |--- |--- |--- |
| 응용 프로그램 읽기 | 프로그램 KPI 읽기 | x | x | x | x | x |
| 응용 프로그램 쓰기 | 프로그램 설정 또는 편집 | x |  |  |  |  |
| 프로그램 추가 | 새 프로그램 추가 | x |  |  |  |  |
| 읽기 환경 | 환경 세부 사항 을 참조하십시오. | x | x | x | x | x |
| 실행 만들기 | 파이프라인 시작. | x | x | x |  |  |
| 읽기 실행 | 실행 상태를 참조하십시오. | x | x | x | x | x |
| 실행 다시 시작 | 일시 중지되면 실행을 재개할 수 있습니다. | x | x | x |  | x |
| 실행 승인 프로덕션에 배포 | GoLive 승인을 제공합니다. | x | x | x |  |  |
| 실행 일정 프로덕션에 배포 | 프로덕션 배포를 예약합니다. | x | x | x |  | x |
| 프로덕션에 실행 배포 | CSE 관리를 위해 일시 중지되면 애플리케이션을 프로덕션에 배포합니다. |  |  |  |  | x |
| 실행 취소 | 현재 실행을 취소합니다. |  |  | x |  |  |
| 실행 대체 품질 게이트 실패 | 중요한 품질 게이트 실패를 승인합니다. | x | x | x |  |  |
| 파이프라인 만들기 | 파이프라인 설정/편집. |  | x |  |  |  |
| 파이프라인 읽기 | 파이프라인 세부 사항 을 참조하십시오. | x | x | x | x | x |
| 파이프라인 쓰기 | 파이프라인 설정/편집. |  | x |  |  |  |
| 파이프라인 수정 승인 | 비즈니스 소유자 옵션을 편집할 수 있습니다. |  | x |  |  |  |
| 파이프라인 관리 배포 수정 | CSE 감독 옵션을 편집할 수 있습니다. |  | x |  |  |  |
| 파이프라인 삭제 | 파이프라인 삭제를 허용합니다. |  | x |  |  |  |
| 단계 읽기 | 단계 품질 지표 결과를 참조하십시오. | x | x | x | x | x |
| 개인 액세스 토큰 생성 | Git에 액세스합니다. |  | x |  | x |  |
