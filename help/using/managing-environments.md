---
title: 환경 관리
description: Cloud Manager를 사용하여 환경을 관리하는 방법에 대해 알아봅니다.
exl-id: 700b0b4c-1e1a-4993-b366-426b14a98f8e
TQID: https://experienceleague.adobe.com/Dz3Z5i-gSNSorc7Na74RKgm3e0P9b-3vjVRdJvu6a0c
product_v2: id: c68cd75e-5bca-4bc3-a60e-9e183f816441id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2: id: cd2426f1-5719-4006-b8c2-738e5969754b
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
topic_v2: id: bce87dde-a4ab-44c9-8a18-ad66e4ddb377
source-git-commit: 0dde660205ad28bc5924a5cc14404c48a0533ceb
workflow-type: tm+mt
source-wordcount: 261
ht-degree: 57%

---

# 환경 관리 {#managing-environments}

Cloud Manager를 사용하여 환경을 관리하는 방법에 대해 알아봅니다.

## 개요 페이지 {#overview-page}

Cloud Manager의 **개요** 페이지에는 관리되는 모든 AEM 환경이 나열된 **환경** 타일이 포함됩니다.

나열된 각 환경은 연결된 상태를 표시합니다.

![개요 페이지](/help/assets/Manage-Environ-Overview.png)

## 환경 타일 {#environments-tile}

**환경** 타일은 프로그램에서 프로비저닝된 프로덕션 및 스테이징 환경을 상태와 함께 표시합니다.

상태는 순서대로 나열된 환경 노드에 대한 집계 전원 상태입니다.

* 녹색 - 모든 노드가 실행 중입니다.
* 빨간색 - 하나 이상의 노드가 중지되었습니다.
* 파란색 - 하나 이상의 노드가 시작되고 있습니다.
* 노란색 - 하나 이상의 노드에서 전원 상태를 사용할 수 없습니다.

![환경 타일](/help/assets/Environments-card-new.png)

## 환경 관리 {#managing-environments-with-cloud-manager}

**환경** 타일에서 환경 행을 클릭하여 **환경** 화면을 표시합니다.

**환경** 화면에 프로그램의 각 프로덕션 및 스테이징 환경이 표시됩니다. 환경 이름이 각 카드 위에 나타납니다. 카드에는 CPU 크기, 스토리지, 영역 및 상태와 함께 환경의 노드 테이블이 포함됩니다.

>[!NOTE]
>
>노드의 **상태**&#x200B;는 VM의 전원 상태를 나타내며 서버의 AEM 상태를 반영하지 않습니다. 상태는 다음과 같을 수 있습니다.

* 녹색 - 실행 중
* 빨간색 - 중지됨
* 파랑 - 시작
* 노란색 - 사용할 수 없음

![환경 탭](/help/assets/Environments-tab.png)

>[!NOTE]
>
>이름과 같은 환경 세부 정보는 프로비저닝되고 나면 변경할 수 없습니다.

>[!NOTE]
>
>고객 성공 담당자를 통해 환경 로그를 요청합니다.

## 비디오 튜토리얼 {#video-tutorial}

이 비디오는 AEM 작성, 게시 및 Dispatcher 인스턴스로 구성된 Cloud Manager 환경에 대해 소개합니다.

>[!VIDEO](https://video.tv.adobe.com/v/26318/)

*(3 분, 1 초)*
