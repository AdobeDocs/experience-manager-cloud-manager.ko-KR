---
title: 2022.3.0 릴리스 정보
description: 다음은 Cloud Manager 릴리스 2022.3.0의 릴리스 노트입니다.
feature: Release Information
exl-id: 2d38abb1-cfc7-44a9-b303-b555e2827eea
source-git-commit: 4a5ddf3144ec50f1a7a4ac367b5c99bc9b486752
workflow-type: tm+mt
source-wordcount: '210'
ht-degree: 4%

---


# Cloud Manager 릴리스 2022.3.0의 릴리스 노트 {#release-notes}

This page documents the release notes for [!UICONTROL Cloud Manager] release 2022.3.0.

>[!NOTE]
>
>For the latest release notes for Cloud Manager in AEM as a Cloud Service, refer to [Cloud Manager in AEM as a Cloud Service&#39;s current release notes.](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/release-notes-cloud-manager/release-notes-cm-current.html)

## 릴리스 날짜 {#release-date}

The release date for [!UICONTROL Cloud Manager] release 2022.3.0 is 10 March 2022. The next release is planned for 7 April 2022.

## 새로운 기능 {#what-is-new}

* Outbounds HTTP requests from asset tests will now come from a Fixed IP range.


## 버그 수정 {#bug-fixes}

* 다음 **로드 밸런서 변경 건너뛰기** 옵션을 사용하지 않도록 설정할 수 없습니다.
* 다음 **로드 밸런서 변경 건너뛰기** AMS 개발 배포에 옵션이 표시되지 않았습니다. **파이프라인 편집 워크플로우**.
* A subset of git repositories created manually had an incorrect name value which prevented the build artifact reuse feature from being effective. The names of those repositories have been changed and users will see the corrected name in the Cloud Manager API/UI.
* Build artifacts from non-production pipelines were inappropriately reused on production full stack pipelines.
* 코드 품질 파이프라인을 추가하거나 편집할 때 지표 오류를 처리하는 옵션이 더 이상 표시되지 않습니다.
* Some unexpected pipeline variable configurations could cause in the build step.
