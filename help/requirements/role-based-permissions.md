---
title: 역할 기반 권한
description: 클라우드 리소스에 대한 액세스를 관리하기 위해 미리 구성된 Cloud Manager의 역할 기반 권한에 대해 알아보십시오.
exl-id: b66533fb-db93-40e8-919d-581261fdbf24
source-git-commit: 522e5fbc650a8159602eb1aeaf42d64f4e23e8b4
workflow-type: tm+mt
source-wordcount: '539'
ht-degree: 13%

---


# 역할 기반 권한 {#role-based-permissions}

[!UICONTROL Cloud Manager] 에는 적절한 권한이 있는 미리 구성된 역할이 있습니다. 예를 들어 개발자는 코드를 개발하고 코드를 Git 리포지토리에 푸시할 수 있는 권한이 있습니다. 비즈니스 소유자에게는 KPI(주요 성과 지표)를 정의하고 배포를 승인할 수 있는 다양한 권한이 있습니다.

## 사용자 역할 {#user-roles}

역할 관리 대상 [!UICONTROL Cloud Manager] 은 [Admin Console.](https://helpx.adobe.com/enterprise/using/admin-console.html) 모든 사용자 [!UICONTROL Cloud Manager] 는 고객의 IMS 조직의 구성원이며 Adobe Managed Services 제품 컨텍스트가 있어야 합니다. 특정 역할 멤버십은 사용자를 [!UICONTROL Cloud Manager] 제품 프로필의 Admin Console을 참조하십시오.

역할을 설정하는 방법에 대한 자세한 내용은 문서를 참조하십시오 [사용자 및 역할 설정.](/help/requirements/users-and-roles.md)

이 표에는 Admin Console에서 할당할 수 있는 역할이 나열되어 있습니다.

| [!UICONTROL Cloud Manager] 역할 | 설명 |
|---|---|
| 비즈니스 소유자 | 초기 작업을 완료한 기본 사용자입니다 [!UICONTROL Cloud Manager] 설정 및 책임자는 KPI를 정의하고, 프로덕션 배포를 승인하고, 필요한 경우 중요한 3계층 오류를 재정의합니다. |
| 프로그램 관리자 | 이 사용자는 [!UICONTROL Cloud Manager] 팀 설정을 수행하려면 상태를 검토하고 KPI를 확인하고 필요한 경우 중요한 3계층 실패를 승인할 수 있습니다. |
| 배포 관리자 | 이 사용자는 [!UICONTROL Cloud Manager] 단계 및 프로덕션 배포를 실행하려면 필요한 경우 중요한 3계층 오류를 승인하고 git 리포지토리에 액세스할 수 있습니다. |
| 개발자 | 이 사용자는 주로 를 사용하는 사용자 지정 애플리케이션 코드를 개발하고 테스트합니다 [!UICONTROL Cloud Manager] 배포 상태를 확인하고 git 리포지토리에 대한 커밋 액세스 권한을 갖습니다. |
| 고객 성공 엔지니어 | 이 사용자는 일반적으로 AMS 고객에 대한 고객 성공을 지원하고 [!UICONTROL Cloud Manager] CSE(Customer Success Engineer) 감독을 필요로 하는 배포를 실행하기 위한 목적입니다. |
| 콘텐츠 작성자 | 일반적으로 이 사용자는 [!UICONTROL Cloud Manager], 그러나 는 [!UICONTROL Cloud Manager] 프로그램 마법사(탐색 [!UICONTROL Experience Cloud])을 클릭하여 Adobe Experience Manager (AEM)에 액세스합니다. |

## 사용자 권한 {#user-permissions}

각 역할에는 연관된 특정 사전 구성된 권한이 있습니다. 이 표에는 사용 가능한 사용 권한 및 이 권한을 실행할 수 있는 역할이 나와 있습니다.


| 권한 | 설명 | 비즈니스 소유자 | 배포 관리자 | 프로그램 관리자 | 개발자 | CSE |
|--- |--- |--- |--- |--- |--- |--- |
| 응용 프로그램 읽기 | 프로그램 KPI 읽기 | x | x | x | x | x |
| 응용 프로그램 쓰기 | 프로그램 설정 또는 편집 | x |  |  |  |  |
| 프로그램 추가 | 새 프로그램 추가 | x |  |  |  |  |
| 읽기 환경 | 환경 세부 사항 을 참조하십시오 | x | x | x | x | x |
| 실행 만들기 | 파이프라인 시작 | x | x | x |  |  |
| 읽기 실행 | 실행 상태 를 참조하십시오 | x | x | x | x | x |
| 실행 다시 시작 | 일시 중지되면 실행을 다시 시작할 수 있습니다 | x | x | x |  | x |
| 실행 승인 프로덕션에 배포 | Go-Live 승인 제공 | x | x | x |  |  |
| 실행 일정 프로덕션에 배포 | 프로덕션 배포 예약 | x | x | x |  | x |
| 프로덕션에 실행 배포 | CSE 감독을 위해 일시 중지되면 애플리케이션을 프로덕션에 배포 |  |  |  |  | x |
| 실행 취소 | 현재 실행 취소 |  |  | x |  |  |
| 실행 대체 품질 게이트 실패 | 중요한 품질 게이트 실패 승인 | x | x | x |  |  |
| 파이프라인 만들기 | 파이프라인 설정/편집 |  | x |  |  |  |
| 파이프라인 읽기 | 파이프라인 세부 사항 참조 | x | x | x | x | x |
| 파이프라인 쓰기 | 파이프라인 설정/편집. |  | x |  |  |  |
| 파이프라인 수정 승인 | 비즈니스 소유자 옵션 편집을 허용합니다. |  | x |  |  |  |
| 파이프라인 관리 배포 수정 | CSE 감독 옵션 편집 허용 |  | x |  |  |  |
| 파이프라인 삭제 | 파이프라인 삭제 허용 |  | x |  |  |  |
| 단계 읽기 | 단계 품질 지표 결과를 참조하십시오 | x | x | x | x | x |
| 개인 액세스 토큰 생성 | Git 액세스 |  | x |  | x |  |

사용자를 설정하는 방법에 대한 자세한 내용은 문서를 참조하십시오 [사용자 및 역할 설정.](/help/requirements/users-and-roles.md)
