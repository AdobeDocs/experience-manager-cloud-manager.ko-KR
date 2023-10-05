---
title: 2023.10.0 릴리스 정보
description: 다음은 Cloud Manager 릴리스 2023.10.0의 릴리스 정보입니다.
feature: Release Information
exl-id: 2d38abb1-cfc7-44a9-b303-b555e2827eea
source-git-commit: 851364e74864c28b3bcd9285dfbe06ddb530eb10
workflow-type: tm+mt
source-wordcount: '226'
ht-degree: 49%

---


# Cloud Manager 릴리스 2023.10.0의 릴리스 정보 {#release-notes}

이 페이지는 [!UICONTROL Cloud Manager] 릴리스 2023.10.0에 대한 릴리스 정보를 설명합니다.

>[!NOTE]
>
>AEM as a Cloud Service에서 Cloud Manager에 대한 최신 릴리스 정보는 [AEM as a Cloud Service의 Cloud Manager 현재 릴리스 정보](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/release-notes-cloud-manager/release-notes-cm-current.html)를 참조하십시오.

## 릴리스 일자 {#release-date}

[!UICONTROL Cloud Manager] 릴리스 2023.10.0의 릴리스 날짜는 2023년 10월 5일입니다. 다음 릴리스는 2023년 11월 2일에 예정되어 있습니다.

## 새로운 기능 {#what-is-new}

* 다음 **배포 관리자** 역할 가능 [비프로덕션 파이프라인이 실행될 때 AEM Dispatcher 캐시에서 무효화되거나 플러시되는 콘텐츠 경로 집합을 구성합니다.](/help/using/non-production-pipelines.md)
   * 이러한 캐시 작업은 콘텐츠 패키지가 배포된 직후에 배포 파이프라인 단계의 일부로 수행됩니다.
   * 이러한 설정은 표준 AEM Dispatcher 비헤이비어를 사용합니다.
* Cloud Manager의 2023년 10월 릴리스부터 단계적 롤아웃을 통해 Java 버전이 업데이트됩니다.
   * Java 8 및 11과 Maven의 부 버전이 업데이트되었으며 향후 2개월에 걸쳐 단계적으로 출시될 예정입니다. 새 버전에는 여러 보안 수정 사항 및 버그 수정이 있습니다. 새 버전은 다음과 같습니다.
   * *Maven: 3.8.8*
   * *Java 8 버전: /usr/lib/jvm/jdk1.8.0_371*
   * *Java 11 버전: /usr/lib/jvm/jdk-11.0.20*
   * [OpenJDK 설명서를 참조하십시오](https://openjdk.org/groups/vulnerability/advisories/) 이러한 JDK 업데이트의 보안 및 버그 수정에 대한 자세한 내용을 확인하십시오.
