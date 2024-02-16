---
title: 2024.2.0 릴리스 정보
description: 다음은 Cloud Manager 릴리스 2024.2.0의 릴리스 정보입니다.
feature: Release Information
exl-id: 2d38abb1-cfc7-44a9-b303-b555e2827eea
source-git-commit: 524471a87217c15dae96c3e6aee57426b43dcccb
workflow-type: tm+mt
source-wordcount: '299'
ht-degree: 50%

---


# Cloud Manager 릴리스 2024.2.0의 릴리스 정보 {#release-notes}

이 페이지는 다음에 대한 릴리스 정보를 설명합니다. [!UICONTROL Cloud Manager] 릴리스 2024.2.0.

>[!NOTE]
>
>AEM as a Cloud Service에서 Cloud Manager에 대한 최신 릴리스 정보는 [AEM as a Cloud Service의 Cloud Manager 현재 릴리스 정보](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/release-notes-cloud-manager/release-notes-cm-current.html)를 참조하십시오.

## 릴리스 일자 {#release-date}

의 릴리스 날짜 [!UICONTROL Cloud Manager] 릴리스 2024.2.0은 2024년 2월 16일입니다. 다음 릴리스는 2024년 3월 16일에 예정되어 있습니다.

## 새로운 기능 {#what-is-new}

* 의 일부로 [배포,](/help/using/code-deployment.md) 에서 Dispatcher 캐시를 플러시했습니다. **Dispatcher 첨부** 단계. 응용 프로그램 로드 밸런서에 첨부하기 전에 각 노드에서 변경 사항을 테스트할 수 있도록 특정 게시자에게 코드를 배포한 후 해당 Dispatcher를 로드 밸런서에 첨부하기 전에 연결된 Dispatcher에서 직접 변경 사항을 테스트할 수 있습니다.
* [빌드 환경](/help/getting-started/build-environment.md) 는 Maven 버전 3.9.4 및 JDK 버전 jdk-11.0.22 및 jdk1.8.0_401로 업데이트되었습니다.

## 조기 채택 프로그램 {#early-adoption}

조기 채택 프로그램에 참여하여 향후 기능을 테스트할 기회를 얻으십시오

### 자체 GitHub 가져오기 {#byo-github}

GitHub를 사용하여 저장소를 관리하는 경우, [이제 Cloud Manager를 통해 GitHub 저장소 내에서 직접 코드의 유효성을 검사할 수 있습니다.](/help/managing-code/byo-github.md) 이 통합을 통해 코드를 Adobe 저장소와 지속적으로 동기화할 필요가 없으며, 기본 분기에 병합하기 전에 가져오기 요청을 확인할 수 있습니다. 이 기능은 공개 GitHub 전용입니다. 자체 호스팅 GitHub에 대해서는 지원되지 않습니다.

이러한 새 기능을 테스트하고 피드백을 공유하는 데 관심이 있으시면 Adobe ID와 연결된 이메일 주소로 `Grp-CloudManager_BYOG@adobe.com`에 이메일을 보내주십시오.

## 버그 수정 {#bug-fixes}

* 빌드 컨테이너의 JDK가 다음 문제를 해결하는 버전으로 업데이트되었습니다 [8313765.](https://bugs.openjdk.org/browse/JDK-8313765)
