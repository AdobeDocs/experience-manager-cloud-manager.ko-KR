---
title: 보안 및 개인 정보
seo-title: AEM 클라우드 관리자를 위한 보안 및 개인 정보 보호
description: 이 페이지에 따라 자산의 보안 및 개인 정보 (코드/가공물) 에 대해 알아보십시오.
seo-description: AEM 클라우드 관리자를 사용하여 자산 (코드/가공물) 의 보안 및 개인 정보에 대해 알려면 이 페이지를 따르십시오.
uuid: 68 BC 2330-A 62 C -4 C 2 C -925 C-DAA 6788 B 143 A
contentOwner: Jsyal
products: sg_ Experiencemanager/Cloudmanager
topic-tags: 소개
discoiquuid: 67 a 54 bae -99 a 9-4405-91 e 3-9 a 0 a 8 b 3 ccc 98
translation-type: tm+mt
source-git-commit: 1dfb065c09569f811e5a006d3d74825d3bd7cc8d

---


# 보안 및 개인 정보 {#security-and-privacy}

[!UICONTROL Cloud Manager] 적절한 권한이 있는 사전 구성된 역할이 있습니다. 예를 들어 개발자는 코드를 개발하고 **코드를 Git 리포지토리에 푸시할 수 있는 권한을 가집니다**. 또는 비즈니스 소유자에게 다른 권한이 있어 KPI (Key Performance Indicator) 를 정의하고 배포를 승인할 수 있습니다.

## 역할 기반 권한 {#role-based-permissions}

### 사용자 역할 {#user-roles}

역할 관리는 [!UICONTROL Cloud Manager][Adobe Admin Console에서 수행합니다](https://helpx.adobe.com/enterprise/using/admin-console.html). 모든 사용자는 [!UICONTROL Cloud Manager] 고객의 IMS 조직의 구성원이어야 하며 Adobe Managed Services 제품 컨텍스트를 가지고 있어야 합니다. 관리 콘솔에서 [!UICONTROL Cloud Manager] 사용자를 제품 프로필에 추가하면 특정 역할 멤버십이 제공됩니다.

역할을 설정하는 방법에 대한 자세한 내용은 사용자 및 역할 [설정을](setting-up-users-and-roles.md)참조하십시오.

다음 표 목록은 관리 콘솔에서 지정할 수 있는 가능한 역할을 정의합니다.

| **[!UICONTROL Cloud Manager]역할** | **설명** |
|---|---|
| 비즈니스 담당자 | 초기 [!UICONTROL Cloud Manager] 설정을 완료하는 기본 사용자. KPI 정의, 프로덕션 배포 승인, 중요한 3 계층 오류 무시를 책임지고 있습니다. |
| 프로그램 관리자 | 팀 설정 수행, 상태 검토 및 KPI 보기를 [!UICONTROL Cloud Manager] 수행하는 데 사용합니다. 중요한 3 계층 오류를 승인할 수 있습니다. |
| 배포 관리자 | 배포 작업을 관리합니다. 단계 및 프로덕션 배포를 실행하는 [!UICONTROL Cloud Manager] 데 사용합니다. 중요한 3 계층 오류를 승인할 수 있습니다. Git 리포지토리에 액세스할 수 있습니다. |
| 개발자 | 사용자 지정 애플리케이션 코드를 개발하고 테스트합니다. 상태를 확인하는 데 주로 사용됩니다 [!UICONTROL Cloud Manager] . Git 리포지토리에 대한 액세스 권한 부여 |
| Customer Success Engineer | 일반적으로 AMS 고객을 위한 고객 성공을 지원합니다. Customer Success [!UICONTROL Cloud Manager] Engineer (CSE) Manager가 필요한 배포를 실행하는 목적을 위해 상호 작용합니다. |
| 컨텐츠 작성자 | 는 일반적으로 상호 작용하지 [!UICONTROL Cloud Manager]않습니다. 이 사용자는 [!UICONTROL Cloud Manager] 프로그램 전환기 (탐색) 를 사용하여 Adobe [!UICONTROL Experience Cloud]Experience Manager (AEM) 에 액세스할 수 있습니다. |

### 사용자 권한 {#user-permissions}

각 역할에는 각 역할과 연관된 특정 권한, 미리 구성된 작업 또는 권한이 있습니다. 다음 표에는 사용할 수 있는 함수와 함수를 실행할 수 있는 역할이 나와 있습니다.

사용자를 설정하는 방법에 대한 자세한 내용은 사용자 및 역할 [설정을](setting-up-users-and-roles.md)참조하십시오.

| 권한 | 설명 | 비즈니스 담당자 | 배포 관리자 | 프로그램 관리자 | 개발자 | CSE |
|--- |--- |--- |--- |--- |--- |--- |
| 애플리케이션 읽기 | 프로그램 세부 정보를 참조하십시오. | x | x | x | x | x |
| 애플리케이션 작성 | 프로그램 (KPI 포함) 를 구성합니다. | x |
| 환경 보기 | 환경 세부 정보를 참조하십시오. | x | x | x | x | x |
| 실행 만들기 | 파이프라인을 시작합니다. | x | x | x |
| 실행 읽기 | 실행 상태를 참조하십시오. | x | x | x | x | x |
| 실행 재개 | 일시 중지할 때 실행을 다시 시작할 수 있습니다. | x | x | x | x |
| 프로덕션에 배포 승인 승인 | Golive 승인 제공 | x | x | x |
| 프로덕션에 배포 예약 배포 | 프로덕션 배포를 예약합니다. | x | x | x | x |
| 프로덕션에 배포 배포 | CSE Manager를 위해 일시 중지되면 프로덕션에 애플리케이션을 배포합니다. | x |
| 실행 취소 | 현재 실행을 취소합니다. | x | x | x |
| 실행 재정의 품질 게이트 실패 | 중요한 품질의 게이트 오류를 승인합니다. | x | x | x |
| Pipeline Create | 설정/편집 | x |
| Pipeline read | 파이프라인 세부 사항을 참조하십시오. | x | x | x | x | x |
| 파이프라인 쓰기 | 설정/편집 | x |
| 파이프라인 수정 승인 | 비즈니스 소유자 옵션을 편집할 수 있습니다. | x |
| 파이프라인 관리 배포 수정 | CSE 감독 옵션 편집을 허용합니다. | x |
| 솔루션 읽기 | 프로그램 KPI를 참조하십시오. | x | x | x | x | x |
| 솔루션 쓰기 | 프로그램 (KPI 포함) 설정/편집 파이프라인 구성 | x |
| Read read | 단계 품질 지표 결과를 참조하십시오. | x | x | x | x | x |

## 리소스 분리 {#resource-isolation}

연계된 [!UICONTROL Cloud Manager] 모든 권한이 구성되고 IMS 조직에 연결되어 있으므로 사용 [!UICONTROL Cloud Manager] 중인 고객은 IMS 자격 증명을 받아야 합니다. 온보딩 프로세스 중에 프로비저닝 팀은 리소스 분리가 적용되도록 보장합니다 [!UICONTROL Cloud Manager].

## 데이터 보안 {#data-security}

의 [!UICONTROL Cloud Manager] 코드는 전송 중에 암호화됩니다. 또한 Coud Manager에서 구축한 이진 파일은 전송 중에 암호화되어 저장될 때 암호화됩니다.

각 고객은 **고유한 Git 리포지토리를** 사용하고 있으며 코드가 안전하며 다른 **조직과도**공유되지 않습니다.

## 데이터 개인 정보 보호 {#data-privacy}

[!UICONTROL Cloud Manager] Adobe가 정의한 개인정보 보호 원칙을 준수합니다. 개발자는 HTTPS를 통해 코드를 **Git 리포지토리로** 안전하게 푸시합니다.

the [! 의 DNL 유저 인터페이스 (UI) [!UICONTROL Cloud Manager]는 Adobe가 정의하는 공통 제어 프레임워크를 준수하는 서비스 위에 구축됩니다. [! DNL 사용자 인터페이스 (UI) [!UICONTROL Cloud Manager]는 여러 클라우드 제공업체의 보안 서비스를 사용합니다.
