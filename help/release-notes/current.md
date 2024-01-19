---
title: 2024.1.0 릴리스 정보
description: 다음은 Cloud Manager 릴리스 2024.1.0의 릴리스 정보입니다.
feature: Release Information
exl-id: 2d38abb1-cfc7-44a9-b303-b555e2827eea
source-git-commit: b235e398b42e9da3dd2efacdc0ef38b6803bd213
workflow-type: tm+mt
source-wordcount: '243'
ht-degree: 55%

---


# Cloud Manager 릴리스 2024.1.0의 릴리스 정보 {#release-notes}

이 페이지는 다음에 대한 릴리스 정보를 설명합니다. [!UICONTROL Cloud Manager] 릴리스 2024.1.0.

>[!NOTE]
>
>AEM as a Cloud Service에서 Cloud Manager에 대한 최신 릴리스 정보는 [AEM as a Cloud Service의 Cloud Manager 현재 릴리스 정보](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/release-notes-cloud-manager/release-notes-cm-current.html)를 참조하십시오.

## 릴리스 일자 {#release-date}

의 릴리스 날짜 [!UICONTROL Cloud Manager] 릴리스 2024.1.0은 2024년 1월 17일입니다. 다음 릴리스는 2024년 2월 16일에 예정되어 있습니다.

## 조기 채택 프로그램 {#early-adoption}

조기 채택 프로그램에 참여하여 향후 기능을 테스트할 기회를 얻으십시오

### 자체 GitHub 가져오기 {#byo-github}

GitHub를 사용하여 저장소를 관리하는 경우, [이제 Cloud Manager를 통해 GitHub 저장소 내에서 직접 코드의 유효성을 검사할 수 있습니다.](/help/managing-code/byo-github.md) 이 통합을 통해 코드를 Adobe 저장소와 지속적으로 동기화할 필요가 없으며, 기본 분기에 병합하기 전에 가져오기 요청을 확인할 수 있습니다.

이러한 새 기능을 테스트하고 피드백을 공유하는 데 관심이 있으시면 Adobe ID와 연결된 이메일 주소로 `Grp-CloudManager_BYOG@adobe.com`에 이메일을 보내주십시오.

## 버그 수정 {#bug-fixes}

* 테스트 애플리케이션에서 데이터를 해석하는 방식으로 인해 다운로드에 실패하여 총 오류 비율이 테스트에 실패하는 일부 코너 사례에 대한 오류가 수정되었습니다.
* 빌드 단계가 상태로 완료되는 경우 `FAILED` 으로 인해 `BUILD_MAVEN_TRANSFER_ARTIFACT_ERROR`이제 대상 분기와 병합 충돌로 인한 오류로 제대로 설명되어 있습니다.
