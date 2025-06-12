---
title: 개발 환경의 서비스 팩 업데이트 - 비공개 베타
description: Cloud Manager 사용자 인터페이스를 통해 개발 환경에 대한 서비스 팩 업데이트를 시작하는 방법을 알아봅니다.
hide: true
hidefromtoc: true
exl-id: 996a8eee-843f-45a6-8f7a-31ea405c2b32
source-git-commit: b2a14280e84bb934053968b0e93e33d30fb6086a
workflow-type: tm+mt
source-wordcount: '453'
ht-degree: 94%

---

# 개발 환경에 대한 서비스 팩 업데이트(비공개 베타) {#stage-prod-only}

Cloud Manager 사용자 인터페이스를 통해 개발 환경에 대한 서비스 팩 업데이트를 시작하는 방법을 알아봅니다.

>[!NOTE]
>
>이 기능은 [비공개 베타 프로그램](/help/release-notes/current.md#beta-program)에서만 사용할 수 있습니다.

## 개요 {#service-pack-updates-overview}

Cloud Manager 사용자 인터페이스를 통해 개발 환경에 대한 서비스 팩 업데이트를 시작할 수 있습니다. 이 기능을 사용하면 사용 가능한 서비스 팩 업데이트를 확인하고 설치 프로세스를 독립적으로 관리할 수 있습니다.

**주요 이점**

* Cloud Manager 서비스 팩 업데이트에 대한 제어를 강화합니다.
* Adobe 고객 성공 엔지니어(CSE)에게 업데이트 시작을 의존하는 것을 줄여 줍니다.
* Cloud Manager를 통해 전체 업데이트 프로세스를 추적합니다.

**현재 제한 사항**

* 셀프서비스 업데이트 옵션은 개발 환경에서만 사용할 수 있습니다.
* 업데이트 실패에 대한 오류 보고는 제한적으로 제공됩니다.
* 문제가 발생하면 자세한 조사를 위해 Adobe CSE에 문의해야 합니다.

## 서비스 팩 업데이트 시작

1. 배포 관리자 권한으로 Cloud Manager에 로그인합니다.
1. 프로그램 개요 페이지로 이동합니다.
1. 환경 섹션에서 ![기타 아이콘(줄임표)](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg)을 클릭합니다.

   ![드롭다운 메뉴에서 서비스 팩 업데이트 확인](/help/using/assets/service-pack-check-for-updates.png)

1. 드롭다운 메뉴에서 ![라이트 모드로 열기 아이콘](https://spectrum.adobe.com/static/icons/workflow_18/Smock_OpenInLight_18_N.svg) **업데이트 확인**&#x200B;을 클릭하여 사용 가능한 서비스 팩 업데이트를 스캔합니다.

   ![사용 가능한 업데이트 목록이 나타납니다.](/help/using/assets/service-pack-versions.png)

1. 목록에서 원하는 서비스 팩 버전을 클릭합니다.
1. **서비스 팩 업데이트**&#x200B;를 클릭하여 업데이트 프로세스를 시작합니다.
1. 확인 대화 상자에서 세부 정보를 검토하고 업데이트를 확인합니다.

   확인이 완료되면 설치 프로세스가 시작되고 Cloud Manager에서 진행 상황을 추적할 수 있습니다.

## 서비스 팩 업데이트 추적

업데이트를 시작한 후 Cloud Manager의 활동 페이지에서 진행 상황을 모니터링할 수 있습니다.

**서비스 팩 업데이트를 추적하는 방법은 다음과 같습니다.**

1. Cloud Manager 대시보드에서 활동 페이지로 이동합니다.
1. 서비스 팩 설치 항목을 찾습니다.

   ![서비스 팩 설치](/help/using/assets/service-pack-installation.png)

1. 해당 항목을 클릭하면 다음과 유사한 자세한 진행 상황과 상태 업데이트를 볼 수 있습니다.

   ![서비스 팩 설치 진행 상황](/help/using/assets/service-pack-progression.png)

### 설치 실패 문제 해결

* 설치에 실패하면 Cloud Manager는 자동으로 이전 상태로의 롤백을 트리거합니다.
* 문제가 지속되면 **로그 다운로드**&#x200B;를 클릭하여 오류 로그를 수집한 다음 Adobe 지원 팀에 문의하여 문제 해결을 요청하십시오.

## 서비스 팩 실행 승인 또는 거부

설치 완료 후 업데이트를 마무리하려면 사용자의 승인(또는 거부)이 필요합니다.

**서비스 팩 실행을 승인 또는 거부하는 방법은 다음과 같습니다.**

1. Cloud Manager에서 활동 페이지를 엽니다.
1. 서비스 팩 업데이트에 대한 보류 중인 승인 요청을 찾습니다.

   ![서비스 팩 업데이트 거부 또는 승인](/help/using/assets/service-pack-reject-approve.png)

1. 다음 중 하나를 수행합니다.

   * 업데이트를 완료하려면 **승인**&#x200B;을 클릭합니다.

   ![서비스 팩 승인](/help/using/assets/service-pack-approve.png)

   * 업데이트를 취소하려면 **거부**&#x200B;를 클릭합니다.
서비스 팩 설치가 취소되며 변경 사항이 적용되지 않습니다.

   ![서비스 팩 거부](/help/using/assets/service-pack-reject.png)
