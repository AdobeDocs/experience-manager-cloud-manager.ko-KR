---
title: 환경 관리
seo-title: 환경 관리
description: 'null'
seo-description: 클라우드 관리자에서 CI/CD 파이프라인을 설정하고 실행하는 데 사용되는 프로덕션 및 비프로덕션 환경 목록을 보려면 이 페이지를 따르십시오.
uuid: 04 e 67572-11 db -4 d 5 d-acf 3-fd 7 f 644 a 95 f 0
contentOwner: Jsyal
products: sg_ Experiencemanager/Cloudmanager
topic-tags: using
discoiquuid: C 5 B 39 DE 2-3 A 9 B -437 F -98 E 8-E 6 E 8 E 6249 A 5 B 3 A
translation-type: tm+mt
source-git-commit: 1dfb065c09569f811e5a006d3d74825d3bd7cc8d

---


# 환경 관리 {#manage-your-environments}

클라우드 관리자의 **개요** 페이지에는 관리되는 모든 AEM 환경을 나열하는 **환경** 타일이 포함되어 있습니다.

나열된 각 환경에 연결된 상태가 표시됩니다.

![](assets/Manage_Environments1.png)

## 클라우드 관리자에서 환경 액세스 {#accessing-environments-in-cloud-manager}

**환경** 타일은 프로그램에서 프로비저닝된 프로덕션 및 스테이지 환경을 상태와 함께 표시합니다.

상태는 환경의 노드 전반에 걸쳐 롤업된 거듭제곱 상태입니다. 모든 노드가 실행 중이면 녹색이고, 한 노드가 중지되는 경우에는 빨간색으로 빨간색, 심지어 한 노드라도 올라오는 경우에는 파란색으로, 심지어 한 노드라도 사용할 수 없는 상태 (이 우선 순위의 순서대로) 가 있으면 노란색입니다.

![](assets/manage_environments-screen2.png)

### 환경 {#environments}

**관리를** 클릭하여 **환경** 화면을 표시합니다.

**환경** 화면에는 프로그램의 *프로덕션* 및 *스테이지* 환경 (해당되는 경우) 에 각각 카드가 표시됩니다. 각 카드 위에 환경의 이름이 표시됩니다. 이 카드에는 CPU, 저장소, 지역 및 상태와 함께 환경의 노드 표가 포함되어 있습니다.

>[!NOTE]
>
>노드의 **상태는** VM의 전력 상태를 나타내며 서버의 AEM 상태를 반영하지 않습니다. 상태는 **실행 (** 녹색 원), **중지됨** (빨간색 원), **증가 (** 파란색 원) 또는 **사용할 수 없음** (노란색 원) 이 될 수 있습니다.

![](assets/Manage_Environments2.png)
