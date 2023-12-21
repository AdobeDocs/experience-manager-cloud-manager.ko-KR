---
title: 2023.12.0 릴리스 정보
description: 다음은 Cloud Manager 릴리스 2023.12.0에 대한 릴리스 정보입니다.
feature: Release Information
exl-id: 2d38abb1-cfc7-44a9-b303-b555e2827eea
source-git-commit: 2ac254508e4015fea21c4fcd087703ac5fbeeec6
workflow-type: tm+mt
source-wordcount: '305'
ht-degree: 81%

---


# Cloud Manager 릴리스 2023.12.0에 대한 릴리스 정보 {#release-notes}

이 페이지는 [!UICONTROL Cloud Manager] 릴리스 2023.12.0에 대한 릴리스 정보를 설명합니다.

>[!NOTE]
>
>AEM as a Cloud Service에서 Cloud Manager에 대한 최신 릴리스 정보는 [AEM as a Cloud Service의 Cloud Manager 현재 릴리스 정보](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/release-notes-cloud-manager/release-notes-cm-current.html)를 참조하십시오.

## 릴리스 일자 {#release-date}

[!UICONTROL Cloud Manager] 릴리스 2023.12.0의 릴리스 일자는 2023년 12월 14일입니다. 다음 릴리스는 2024년 1월 18일에 예정되어 있습니다.

## 새로운 기능 {#what-is-new}

* [Cloud Manager 사용자 정의 권한](/help/using/custom-permissions.md)을 사용하여 Cloud Manager 사용자의 프로그램, 파이프라인 및 환경에 대한 액세스를 제한하는 구성 가능한 권한으로 새 사용자 정의 권한 프로필을 생성할 수 있습니다.
* 에 대한 업데이트 롤아웃 [빌드 환경](/help/getting-started/build-environment.md) 다음 작업: [Cloud Manager의 10월 릴리스에서 발표 및 시작](/help/release-notes/2023/2023-10-0.md) 완료되었습니다.
   * 에 대해 노드 18에 대한 지원이 추가되었습니다. [프론트엔드 및 전체 스택 파이프라인](/help/overview/ci-cd-pipelines.md)
   * Java 8 보조 버전이 `jdk1.8.0_371`로 업데이트되었습니다.
   * Java 11 보조 버전이 `jdk-11.0.20`로 업데이트되었습니다.
   * Maven이 3.8.8 버전으로 업데이트되었습니다.
      * 이제 Maven이 모든 비보안 기능을 비활성화합니다. `http://*` 미러는 기본적으로 사용됩니다.
      * [Adobe 추천](/help/getting-started/build-environment.md#https-maven) 사용자는 HTTP 대신 HTTPS를 사용하도록 Maven 저장소를 업데이트합니다.
* 빌드 컨테이너 기본 이미지가 Ubuntu 22.04로 업데이트되었습니다.

## 조기 채택 프로그램 {#early-adoption}

조기 채택 프로그램에 참여하여 향후 기능을 테스트할 기회를 얻으십시오

### 자체 GitHub 가져오기 {#byo-github}

GitHub를 사용하여 저장소를 관리하는 경우, [이제 Cloud Manager를 통해 GitHub 저장소 내에서 직접 코드의 유효성을 검사할 수 있습니다.](/help/managing-code/byo-github.md) 이 통합을 통해 코드를 Adobe 저장소와 지속적으로 동기화할 필요가 없으며, 기본 분기에 병합하기 전에 가져오기 요청을 확인할 수 있습니다.

이러한 새 기능을 테스트하고 피드백을 공유하는 데 관심이 있으시면 Adobe ID와 연결된 이메일 주소로 `Grp-CloudManager_BYOG@adobe.com`에 이메일을 보내주십시오.
