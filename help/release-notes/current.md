---
title: 2023.8.0 릴리스 정보
description: 다음은 Cloud Manager 릴리스 2023.8.0의 릴리스 정보입니다.
feature: Release Information
exl-id: 2d38abb1-cfc7-44a9-b303-b555e2827eea
source-git-commit: f930f12b5f50dd96a1677ff7a56cf0e92a400556
workflow-type: tm+mt
source-wordcount: '216'
ht-degree: 39%

---


# Cloud Manager 릴리스 2023.8.0의 릴리스 정보 {#release-notes}

이 페이지는 [!UICONTROL Cloud Manager] 릴리스 2023.8.0에 대한 릴리스 정보를 설명합니다.

>[!NOTE]
>
>AEM as a Cloud Service에서 Cloud Manager에 대한 최신 릴리스 정보는 [AEM as a Cloud Service의 Cloud Manager 현재 릴리스 정보](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/release-notes-cloud-manager/release-notes-cm-current.html)를 참조하십시오.

## 릴리스 일자 {#release-date}

[!UICONTROL Cloud Manager] 릴리스 2023.8.0의 릴리스 날짜는 2023년 8월 10일입니다. 다음 릴리스는 2023년 7월 9일에 예정되어 있습니다.

## 새로운 기능 {#what-is-new}

* Cloud Manager UI에서 오류 메시지의 이해도와 노출을 개선했습니다.

## 버그 수정 {#bug-fixes}

* 드문 사례 [콘텐츠 복사](/help/using/content-copy.md) 중지 프로세스가 해결되었습니다.
* New Relic One을 사용하지 않는 고객의 일시적인 테스트 문제가 해결되었습니다.
* [사용자 지정 코드 품질 규칙](/help/using/custom-code-quality-rules.md) `SupportedRunmode` 및 `ImmutableMutableMixedPackage` AEM as a Cloud Service에만 적용되므로 SonarQube에서 제거되었습니다.
* 사용자에게 더 이상 실행 중인 것처럼 보이는 중단된 파이프라인이 발생하지 않습니다.
* 다음 **환경** 이제 를 트리거한 후 메뉴가 닫힙니다. **[콘텐츠 복사](/help/using/content-copy.md)** 모달
* [파이프라인 재실행](/help/using/code-deployment.md#reexecute-deployment) 이전 실행에 가 없는 경우 이 더 이상 허용되지 않습니다. `commitId` 빌드 단계 상태를 설정합니다.
* 이제 사용자가 의 파이프라인을 클릭하면 드물게 발생하는 오류에 대해 보다 이해하기 쉬운 메시지가 표시됩니다. **활동** 또는 **파이프라인** screens.
