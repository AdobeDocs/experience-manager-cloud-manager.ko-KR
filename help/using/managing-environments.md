---
title: 환경 관리
description: Cloud Manager를 사용하여 환경을 관리하는 방법에 대해 알아봅니다.
exl-id: 700b0b4c-1e1a-4993-b366-426b14a98f8e
source-git-commit: 0b7c926120798e2fdb635752192f4ab2e12c1e24
workflow-type: ht
source-wordcount: '273'
ht-degree: 100%

---


# 환경 관리 {#managing-environments}

Cloud Manager를 사용하여 환경을 관리하는 방법에 대해 알아봅니다.

## 개요 페이지 {#overview-page}

Cloud Manager의 **개요** 페이지에는 관리되는 모든 AEM 환경이 나열된 **환경** 타일이 포함됩니다.

나열된 각 환경은 연결된 상태를 표시합니다.

![개요 페이지](/help/assets/Manage-Environ-Overview.png)

## 환경 타일 {#environments-tile}

**환경** 타일은 프로그램에서 프로비저닝된 프로덕션 및 스테이징 환경을 상태와 함께 표시합니다.

상태는 환경 내 노드에 걸쳐 롤업된 전원 상태를 다음 우선 순위 순서로 나타냅니다.

* 녹색 - 모든 노드가 실행 중입니다.
* 빨간색 - 하나 이상의 노드가 중지되었습니다.
* 파란색 - 하나 이상의 노드가 시작 중입니다.
* 노란색 - 하나 이상의 노드에서 전원 상태를 사용할 수 없습니다.

![환경 타일](/help/assets/Environments-card-new.png)

## 환경 관리 {#managing-environments-with-cloud-manager}

**환경** 타일에서 환경 행을 클릭하여 **환경** 화면을 표시합니다.

**환경** 화면은 프로그램에서 프로덕션 및 스테이징 환경(해당되는 경우)에 대해 각각 카드를 표시합니다. 환경 이름이 각 카드 위에 표시됩니다. 카드에는 CPU의 티셔츠 크기, 스토리지, 영역 및 상태와 함께 환경의 노드 테이블이 포함됩니다.

>[!NOTE]
>
>노드의 **상태**&#x200B;는 VM의 전원 상태를 나타내며 서버의 AEM 상태를 반영하지 않습니다. 상태는 다음과 같을 수 있습니다.

* 녹색 - 실행 중
* 빨간색 - 중지됨
* 파란색 - 시작 중
* 노란색 - 사용할 수 없음

![환경 탭](/help/assets/Environments-tab.png)

>[!NOTE]
>
>이름과 같은 환경 세부 정보는 프로비저닝되고 나면 변경할 수 없습니다.

>[!NOTE]
>
>고객 성공 엔지니어에게 환경 로그를 요청하십시오.

## 비디오 튜토리얼 {#video-tutorial}

이 비디오는 AEM 작성, 게시 및 Dispatcher 인스턴스로 구성된 Cloud Manager 환경에 대한 개요를 제공합니다.

>[!VIDEO](https://video.tv.adobe.com/v/34271?captions=kor)

*(3 분, 1 초)*
