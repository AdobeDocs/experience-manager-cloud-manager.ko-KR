---
title: 2022.4.0 릴리스 정보
description: 다음은 Cloud Manager 릴리스 2022.4.0의 릴리스 노트입니다.
feature: Release Information
source-git-commit: dd7f22e378cdb0b0e2d1c7d318a970e1f719f47b
workflow-type: tm+mt
source-wordcount: '277'
ht-degree: 2%

---


# Cloud Manager 릴리스 2022.4.0의 릴리스 노트 {#release-notes}

이 페이지에서는 다음에 대한 릴리스 노트를 문서화합니다 [!UICONTROL Cloud Manager] 릴리스 2022.4.0.

>[!NOTE]
>
>AEM as a Cloud Service의 Cloud Manager 최신 릴리스 노트는 을 참조하십시오 [AEM as a Cloud Service의 현재 릴리스 노트에 있는 Cloud Manager.](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/release-notes-cloud-manager/release-notes-cm-current.html)

## 릴리스 날짜 {#release-date}

에 대한 릴리스 날짜 [!UICONTROL Cloud Manager] 릴리스 2022.4.0은 2022년 4월 7일입니다. 다음 릴리스는 2022년 5월 5일에 예정되어 있습니다.

## 새로운 기능 {#what-is-new}

* 파이프라인 빌드 단계의 지속 시간 및 성공률에 대한 개선 사항이 구현되었으며 4월 말까지 모든 고객에게 점진적으로 출시됩니다.
* 이제 파이프라인 추가 및 편집 마법사의 입력 필드에 이름의 처음 몇 개의 문자를 입력하고 제안된 일치 항목 중에서 선택하여 git 분기를 쉽게 찾을 수 있습니다.
* 다음 **파이프라인** 이제 페이지에 많은 파이프라인이 있는 프로그램에 대한 유용성을 개선하기 위해 페이지 매김이 있습니다.
   * 페이지당 50개의 행이 테이블에 표시됩니다.
* 버전 [AEM 프로젝트 원형](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html) cloud Manager에서 사용하는 버전이 버전 36으로 업데이트되었습니다.
* Oracle JDK는 이제 AEM 애플리케이션 개발 및 작업을 위한 기본 JDK입니다. Maven 도구 체인에서 대체 옵션을 명시적으로 선택한 경우에도 Cloud Manager 빌드 프로세스는 Oracle JDK를 사용하여 자동으로 로 전환됩니다.
   * oracle JDK로 전환하는 방법에 대한 자세한 내용은 [빌드 환경 설명서입니다.](/help/using/build-environment-details.md#using-java-support)
   * 자세한 내용은 [Adobe Experience Manager에 대한 Java 지원 정책 FAQ](https://experienceleague.adobe.com/docs/experience-manager-65/assets/Java_Policy_for_Adobe_Experience_Manager.pdf) 이 변경에 대한 일반적인 질문에 답하기 위해
