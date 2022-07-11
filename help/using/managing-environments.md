---
title: 환경 관리
description: Cloud Manager를 사용하여 환경을 관리하는 방법을 알아봅니다.
exl-id: 700b0b4c-1e1a-4993-b366-426b14a98f8e
source-git-commit: 80f8707e00357f5a08dd835b846c9ee610f3e573
workflow-type: tm+mt
source-wordcount: '263'
ht-degree: 2%

---


# 환경 관리 {#managing-environments}

Cloud Manager를 사용하여 환경을 관리하는 방법을 알아봅니다.

## 개요 페이지 {#overview-page}

다음 **개요** Cloud Manager의 페이지에는 **환경** 관리되는 모든 AEM 환경을 나열하는 타일입니다.

나열된 각 환경에 연결된 상태가 표시됩니다.

![개요 페이지](/help/assets/Manage-Environ-Overview.png)

## 환경 타일 {#environments-tile}

다음 **환경** 타일은 프로그램에서 제공된 프로덕션 및 스테이징 환경을 상태와 함께 표시합니다.

상태는 다음과 같은 우선순위 순서로 환경의 노드에 걸쳐 롤업된 전원 상태입니다.

* 녹색 - 모든 노드가 실행 중입니다.
* 빨간색 - 하나 이상의 노드가 중지됩니다.
* 파란색 - 하나 이상의 노드가 표시됩니다.
* 노란색 - 하나 이상의 노드에 사용할 수 없는 전원 상태가 있습니다.

![환경 타일](/help/assets/Environments-card-new.png)

## 환경 관리 {#managing-environments-with-cloud-manager}

설정 **환경** 타일, **관리** 를 **환경** 화면.

다음 **환경** 화면에 프로덕션 및 스테이징 환경(해당하는 경우)에 대한 카드가 프로그램에 각각 표시됩니다. 환경 이름이 각 카드 위에 표시됩니다. 이 카드에는 CPU, 스토리지, 영역 및 상태와 함께 환경의 노드 테이블이 포함됩니다.

>[!NOTE]
>
>다음 **상태** 노드의 전원 상태는 VM의 전원 상태를 나타내며 서버의 AEM 상태를 반영하지 않습니다. 상태는 다음과 같습니다.

* 녹색 - 실행
* 빨간색 - 중지됨
* 파란색 - 준비 중
* 노란색 - 사용할 수 없음

![환경 탭](/help/assets/Environments-tab.png)

>[!NOTE]
>
>환경 로그가 필요한 경우 고객 성공 엔지니어를 통해 요청할 수 있습니다.

## 비디오 자습서 {#video-tutorial}

이 비디오에서는 AEM 작성, 게시 및 Dispatcher 인스턴스로 구성된 Cloud Manager 환경에 대한 개요를 제공합니다.

>[!VIDEO](https://video.tv.adobe.com/v/26318/)
