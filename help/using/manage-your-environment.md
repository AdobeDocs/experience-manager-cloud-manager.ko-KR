---
title: 환경 관리
seo-title: Manage your Environments
description: Cloud Manager 환경에 대해 알아보기
seo-description: Follow this page to view the list of production and non-production environments that are used for setting up and running the CI/CD pipeline in Cloud Manager.
uuid: 04e67572-11db-4d5d-acf3-fd7f644a95f0
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: using
discoiquuid: c5b39de2-3a9b-437f-98e8-e6e6249a5b3a
feature: Environments
exl-id: 700b0b4c-1e1a-4993-b366-426b14a98f8e
source-git-commit: 6ff704ec11dd4a5f73d5b5df5721c4fee649527b
workflow-type: tm+mt
source-wordcount: '280'
ht-degree: 6%

---

# 환경 관리 {#manage-your-environments}

>[!NOTE]
>AEM as a Cloud Service에서 Cloud Manager의 환경 관리에 대해 알아보려면 다음을 참조하십시오 [여기](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/manage-environments.html?lang=ko-kr#using-cloud-manager).

다음 **개요** Cloud Manager의 페이지에는 **환경** 관리되는 모든 AEM 환경을 나열하는 타일입니다.

나열된 각 환경에 연결된 상태가 표시됩니다.

![](assets/Manage-Environ-Overview.png)

## 비디오 자습서 {#video-tutorial}

### Cloud Manager 환경 개요 {#environ-video}

다음 비디오에서는 AEM 작성자, AEM 게시 및 Dispatcher 인스턴스로 구성된 Cloud Manager 환경에 대한 개요를 제공합니다.

>[!VIDEO](https://video.tv.adobe.com/v/26318/)

## Cloud Manager에서 환경 액세스 {#accessing-environments-in-cloud-manager}

다음 **환경** 타일은 프로그램에서 제공된 프로덕션 및 스테이지 환경과 상태를 표시합니다.

상태는 환경의 노드에 걸쳐 롤업된 전원 상태입니다. 모든 노드가 실행 중이면 녹색이고, 한 노드가 중지되더라도 빨간색, 한 노드가 작동 중이면 파란색으로 표시되고, 한 노드가 작동 가능하지 않으면 노랑으로 표시됩니다(이 우선 순위 순서로).

![](assets/Environments-card-new.png)

### 환경 {#environments}

클릭 **관리** 를 **환경** 화면.

다음 **환경** 화면에는 다음에 대한 카드가 각각 표시됩니다 *프로덕션* 및 *단계* 환경(해당하는 경우)을 사용하십시오. 환경 이름이 각 카드 위에 표시됩니다. 이 카드에는 CPU, 스토리지, 영역 및 상태와 함께 환경의 노드 테이블이 포함됩니다.

>[!NOTE]
>
>다음 **상태** 노드의 전원 상태는 VM의 전원 상태를 나타내며 서버의 AEM 상태를 반영하지 않습니다. 상태는 **실행 중** (녹색 원), **중지됨** (빨간색 원), **준비 중** (파란색 원) 또는 **사용할 수 없음** (노란색 원)

![](assets/Environments-tab.png)

>[!NOTE]
>
>환경 로그가 필요한 경우 고객 성공 엔지니어를 통해 요청할 수 있습니다.
