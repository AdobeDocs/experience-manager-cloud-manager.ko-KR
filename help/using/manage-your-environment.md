---
title: 환경 관리
seo-title: 환경 관리
description: Cloud Manager 환경에 대해 알아보기
seo-description: Cloud Manager에서 CI/CD 파이프라인을 설정하고 실행하는 데 사용되는 프로덕션 및 비프로덕션 환경 목록을 보려면 이 페이지를 따르십시오.
uuid: 04e67572-11db-4d5d-acf3-fd7f644a95f0
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: using
discoiquuid: c5b39de2-3a9b-437f-98e8-e6e6249a5b3a
feature: 환경
exl-id: 700b0b4c-1e1a-4993-b366-426b14a98f8e
source-git-commit: df2f598f91201d362f54b17e4092ff6bd6a72cec
workflow-type: tm+mt
source-wordcount: '296'
ht-degree: 3%

---

# 환경 관리 {#manage-your-environments}

>[!NOTE]
>AEM as a Cloud Service으로 Cloud Manager에 대한 환경 관리에 대해 알려면 [여기](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/manage-environments.html?lang=en#using-cloud-manager)를 참조하십시오.

Cloud Manager의 **개요** 페이지에는 관리되는 모든 AEM 환경을 나열하는 **환경** 타일이 포함되어 있습니다.

나열된 각 환경에 연결된 상태가 표시됩니다.

![](assets/Manage-Environ-Overview.png)

## 비디오 자습서 {#video-tutorial}

### Cloud Manager 환경 개요 {#environ-video}

다음 비디오에서는 AEM 작성자, AEM 게시 및 Dispatcher 인스턴스로 구성된 Cloud Manager 환경에 대한 개요를 제공합니다.

>[!VIDEO](https://video.tv.adobe.com/v/26318/)

## Cloud Manager {#accessing-environments-in-cloud-manager} 의 환경에 액세스

**환경** 타일에는 프로그램에서 제공된 프로덕션 및 스테이지 환경이 상태와 함께 표시됩니다.

상태는 환경의 노드에 걸쳐 롤업된 전원 상태입니다. 모든 노드가 실행 중이면 녹색이고, 한 노드가 중지되더라도 빨간색, 한 노드가 작동 중이면 파란색으로 표시되고, 한 노드가 작동 가능하지 않으면 노랑으로 표시됩니다(이 우선 순위 순서로).

![](assets/Environments-card-new.png)

### 환경 {#environments}

**관리** 를 클릭하여 **환경** 화면을 표시합니다.

**환경** 화면에는 프로그램에서 *프로덕션* 및 *스테이지* 환경(해당하는 경우)에 대해 각각 카드가 표시됩니다. 환경 이름이 각 카드 위에 표시됩니다. 이 카드에는 CPU, 스토리지, 영역 및 상태와 함께 환경의 노드 테이블이 포함됩니다.

>[!NOTE]
>
>노드의 **STATUS**&#x200B;는 VM의 전원 상태를 나타내며 서버의 AEM 상태를 반영하지 않습니다. 상태는 **실행**(녹색 원), **중지됨**(빨간색 원), **다가오기**(파란색 원) 또는 **사용할 수 없음**(노란색 원)일 수 있습니다.

![](assets/Environments-tab.png)
