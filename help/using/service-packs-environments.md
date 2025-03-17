---
title: 개발 환경용 서비스 팩 업데이트 - 얼리 어답터
description: Cloud Manager 사용자 인터페이스를 통해 개발 환경에 대한 서비스 팩 업데이트를 시작하는 방법을 알아봅니다.
source-git-commit: 8da0e6cb4587bc7dfc79bec415ff3aeef2d12e3e
workflow-type: tm+mt
source-wordcount: '453'
ht-degree: 3%

---

# 개발 환경에 대한 서비스 팩 업데이트(얼리 어답터) {#stage-prod-only}

Cloud Manager 사용자 인터페이스를 통해 개발 환경에 대한 서비스 팩 업데이트를 시작하는 방법을 알아봅니다.

>[!NOTE]
>
>이 기능은 [얼리 어답터 프로그램](/help/release-notes/current.md)에만 사용할 수 있습니다.

## 개요 {#service-pack-updates-overview}

Cloud Manager 사용자 인터페이스를 통해 개발 환경에 대한 서비스 팩 업데이트를 시작할 수 있습니다. 이 기능을 사용하면 사용 가능한 서비스 팩 업데이트를 확인하고 설치 프로세스를 독립적으로 관리할 수 있습니다.

**주요 이점**

* Cloud Manager 서비스 팩 업데이트를 보다 세밀하게 제어할 수 있습니다.
* 업데이트를 시작하는 Adobe CSE(Customer Success Engineers)에 대한 종속성을 줄입니다.
* Cloud Manager을 통한 전체 업데이트 프로세스를 추적합니다.

**현재 제한 사항**

* 셀프서비스 업데이트 옵션은 개발 환경에만 사용할 수 있습니다.
* 실패한 업데이트에 대해 제한된 오류 보고를 사용할 수 있습니다.
* 문제가 발생하면 Adobe CSE에 연락하여 추가 조사를 해야 합니다.

## 서비스 팩 업데이트 시작

1. 배포 관리자 권한으로 Cloud Manager에 로그인합니다.
1. 프로그램 개요 페이지로 이동합니다.
1. 환경 섹션에서 ![추가 아이콘, 줄임표](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg)를 클릭합니다.

   ![드롭다운 메뉴에서 서비스 팩 업데이트 확인](/help/using/assets/service-pack-check-for-updates.png)

1. 드롭다운 메뉴에서 ![가볍게 열기 아이콘](https://spectrum.adobe.com/static/icons/workflow_18/Smock_OpenInLight_18_N.svg) **업데이트 확인**&#x200B;을 클릭하여 사용 가능한 서비스 팩 업데이트를 검색합니다.

   ![사용 가능한 업데이트 목록이 표시됩니다](/help/using/assets/service-pack-versions.png)

1. 목록에서 원하는 서비스 팩 버전을 클릭합니다.
1. 업데이트 프로세스를 시작하려면 **서비스 팩 업데이트**&#x200B;를 클릭하십시오.
1. 확인 대화 상자에서 세부 사항을 검토하고 업데이트를 확인합니다.

   확인되면 설치 프로세스가 시작되며 진행 상황은 Cloud Manager에서 추적할 수 있습니다.

## 서비스 팩 업데이트 추적

업데이트를 시작하면 Cloud Manager의 활동 페이지에서 진행 상황을 모니터링할 수 있습니다.

**서비스 팩 업데이트를 추적하려면:**

1. Cloud Manager 대시보드에서 활동 페이지로 이동합니다.
1. 서비스 팩 설치 항목을 찾습니다.

   ![서비스 팩 설치](/help/using/assets/service-pack-installation.png)

1. 항목을 클릭하면 다음과 유사한 세부 진행 상황 및 상태 업데이트가 표시됩니다.

   ![서비스 팩 설치 진행 중](/help/using/assets/service-pack-progression.png)

### 설치 오류 문제 해결

* 설치에 실패하면 Cloud Manager에서 자동으로 이전 상태로 롤백을 트리거합니다.
* 문제가 지속되면 **로그 다운로드**&#x200B;를 클릭하여 오류 로그를 수집한 다음 Adobe 지원 센터에 문의하여 문제를 해결하십시오.

## 서비스 팩 실행 승인 또는 거부

설치가 완료되면 업데이트를 완료하기 위해 승인 또는 거부가 필요합니다.

**서비스 팩 실행을 승인하거나 거부하려면:**

1. Cloud Manager에서 활동 페이지를 엽니다.
1. 서비스 팩 업데이트에 대해 보류 중인 승인 요청을 찾습니다.

   ![서비스 팩 업데이트 거부 또는 승인](/help/using/assets/service-pack-reject-approve.png)

1. 다음 중 하나를 수행합니다.

   * 업데이트를 완료하려면 **승인**&#x200B;을 클릭하세요.

   ![서비스 팩 승인](/help/using/assets/service-pack-approve.png)

   * 업데이트를 취소하려면 **거부**를 클릭하십시오.
서비스 팩 설치가 취소되고 변경 사항이 적용되지 않습니다.

   ![서비스 팩 거부](/help/using/assets/service-pack-reject.png)


