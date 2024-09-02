---
title: 역할 기반 권한
description: 클라우드 리소스에 대한 액세스를 관리하기 위해 Cloud Manager가 미리 구성한 역할 기반 사용 권한에 대해 알아보십시오.
exl-id: b66533fb-db93-40e8-919d-581261fdbf24
source-git-commit: 984269e5fe70913644d26e759fa21ccea0536bf4
workflow-type: tm+mt
source-wordcount: '616'
ht-degree: 100%

---


# 역할 기반 권한 {#role-based-permissions}

[!UICONTROL Cloud Manager]에는 적절한 권한으로 미리 구성된 역할이 있습니다. 예를 들어 개발자는 코드를 개발하고 Git 저장소에 코드를 푸시할 수 있는 권한을 가지고 있습니다. 비즈니스 소유자는 KPI(주요 성과 지표)를 정의하고 배포를 승인할 수 있는 다양한 권한을 가지고 있습니다.

>[!NOTE]
>
>이 설명서에서는 Adobe Managed Services(AMS)용 Cloud Manager의 역할 기반 권한에 대해 설명합니다.
>
>AEM as a Cloud Service에 대한 동등한 설명서는 AEM as a Cloud Service 설명서의 [Cloud Manager 소개](https://experienceleague.adobe.com/ko/docs/ experience-manager-cloud-service/content/onboarding/concepts/cloud-manager-introduction#role-based-permissions) 문서에서 찾을 수 있습니다.

## 사용자 역할 {#user-roles}

[!UICONTROL Cloud Manager]의 역할 관리는 [Admin Console](https://helpx.adobe.com/kr/enterprise/using/admin-console.html)을 사용하여 수행됩니다. [!UICONTROL Cloud Manager]의 모든 사용자는 고객의 IMS 조직 멤버여야 하며 Adobe Managed Services 제품 컨텍스트를 가지고 있어야 합니다. Admin Console에서 [!UICONTROL Cloud Manager] 제품 프로필에 사용자를 추가하여 특정 역할 멤버십을 제공합니다.

역할을 설정하는 방법에 대한 자세한 내용은 [사용자 및 역할 설정](/help/requirements/users-and-roles.md)을 참조하십시오.

다음 표에는 Admin Console에서 할당할 수 있는 역할이 나열되어 있습니다.

| [!UICONTROL Cloud Manager] 역할 | 설명 |
|---|---|
| 비즈니스 소유자 | 초기 [!UICONTROL Cloud Manager] 설정을 완료하고 KPI를 정의하고, 프로덕션 배포를 승인하며, 필요할 때 중요한 3계층 오류를 재정의하는 역할을 하는 주요 사용자. |
| 콘텐츠 작성자 | 일반적으로 Cloud Manager와 상호 작용하지 않지만 Cloud Manager 프로그램 스위처(Experience Cloud에서 탐색)를 사용하여 Adobe Experience Manager(AEM)에 액세스할 수 있는 사용자. |
| 고객 성공 엔지니어 | 주로 AMS 고객 성공을 지원하고 [!UICONTROL Cloud Manager]를 사용하여 배포를 실행하는 사용자. 이러한 배포에는 Adobe 고객 성공 엔지니어(CSE)의 감독이 필요합니다. |
| 배포 관리자 | [!UICONTROL Cloud Manager]를 사용하여 배포 작업을 관리하여 스테이징 및 프로덕션 배포를 실행하고, 필요한 경우 중요한 3계층 오류를 승인하며, Git 저장소에 액세스할 수 있는 사용자. |
| 개발자 | 사용자 정의 애플리케이션 코드를 개발 및 테스트하고 주로 [!UICONTROL Cloud Manager]를 사용하여 배포 상태를 보고 Git 저장소에 대한 커밋 액세스 권한이 있는 사용자. |
| 프로그램 관리자 | [!UICONTROL Cloud Manager]를 사용하여 팀 설정, 상태 검토, KPI 보기를 수행하고 필요한 경우 중요한 3계층 오류를 승인할 수 있는 사용자. |

## 사용자 권한 {#user-permissions}

각 역할에는 사전 구성된 특정 권한이 있습니다. 다음 표에는 사용 가능한 권한과 해당 권한을 실행할 수 있는 역할이 나열되어 있습니다.

| 권한 | 설명 | 비즈니스 소유자 | 배포 관리자 | 프로그램 관리자 | 개발자 | CSE |
| --- | --- | --- | --- | --- | --- | --- |
| 애플리케이션 읽기 | 프로그램 KPI 읽기 | x | x | x | x | x |
| 애플리케이션 쓰기 | 프로그램 설정 또는 편집 | x | | | | |
| 프로그램 추가 | 새 프로그램 추가 | x | | | | |
| 환경 읽기 | 환경 세부 정보 보기 | x | x | x | x | x |
| 실행 생성 | 파이프라인 시작 | x | x | x | | |
| 실행 읽기 | 실행 상태 보기 | x | x | x | x | x |
| 실행 다시 시작 | 일시 정지 시 실행을 재개할 수 있는 기능 | x | x | x | | x |
| 실행 승인을 프로덕션에 배포 | Go-Live 승인 제공 | x | x | x | | |
| 실행 예약을 프로덕션에 배포 | 프로덕션 배포 예약 | x | x | x | | x |
| 실행을 프로덕션에 배포 | CSE 감독을 위해 일시 중지된 경우 프로덕션 환경에 애플리케이션 배포 | | | | | x |
| 실행 취소 | 현재 실행 취소 | | | x | | |
| 실행 오버라이드 품질 게이트 오류 | 중요한 품질 게이트 실패 승인 | x | x | x | | |
| 파이프라인 만들기 | 파이프라인 설정/편집 | | x | | | |
| 파이프라인 읽기 | 파이프라인 세부 정보 보기 | x | x | x | x | x |
| 파이프라인 쓰기 | 파이프라인 설정/편집 | | x | | | |
| 파이프라인 수정 승인 | 비즈니스 소유자 옵션 편집 허용 | | x | | | |
| 파이프라인 수정 관리 배포 | CSE 감독 옵션 편집 허용 | | x | | | |
| 파이프라인 삭제 | 파이프라인 삭제 허용 | | x | | | |
| 단계 읽기 | 단계 품질 지표 결과 확인 | x | x | x | x | x |
| 개인 액세스 토큰 생성 | 액세스 Git | | x | | x | |

사용자를 설정하는 방법에 대한 자세한 내용은 [사용자 및 역할 설정](/help/requirements/users-and-roles.md)을 참조하십시오.

>[!TIP]
>
>구성 가능한 권한이 있는 사용자 정의 권한 프로필도 사용할 수 있습니다. 자세한 내용은 [사용자 정의 권한](/help/using/custom-permissions.md)을 참조하십시오.
