---
title: 환경 일관성을 유지하기 위한 콘텐츠 복사
description: Cloud Manager의 콘텐츠 복사를 사용하면 사용자가 테스트를 위해 Adobe Managed Services에서 호스팅하는 Adobe Experience Manager 6.x 프로덕션 환경으로 주문형 변경 가능한 콘텐츠를 복사할 수 있습니다.
exl-id: 97915e58-a1d3-453f-b5ce-cad55ed73262
source-git-commit: e3a656605ac59ca1f95985426932fddf2b53b7c9
workflow-type: ht
source-wordcount: '1321'
ht-degree: 100%

---


# 환경 일관성을 유지하기 위한 콘텐츠 복사 {#content-copy}

Cloud Manager의 콘텐츠 복사를 사용하면 사용자가 테스트를 위해 Adobe Managed Services에서 호스팅하는 Adobe Experience Manager 6.x 프로덕션 환경으로 주문형 변경 가능한 콘텐츠를 복사할 수 있습니다.

## 콘텐츠 복사 정보 {#introduction}

현재의 실제 데이터는 테스트, 검증 및 사용자 승인 목적에 유용합니다. 콘텐츠 복사를 사용하면 프로덕션 AMS 호스팅된 AEM 6.x 환경에서 스테이징 환경 또는 개발 환경으로 콘텐츠를 복사할 수 있습니다. 이 워크플로는 다양한 테스트 시나리오를 지원합니다.

콘텐츠 세트가 복사할 콘텐츠를 정의합니다. 콘텐츠 세트에는 복사할 변경 가능한 콘텐츠가 있는 JCR 경로 목록이 포함됩니다. 콘텐츠는 소스 환경에서 대상 환경으로 이동합니다. 모든 작업은 동일한 Cloud Manager 프로그램 내에서 수행됩니다.

콘텐츠 세트에서 허용되는 경로는 다음과 같습니다.

```text
/content/**
/conf/**
/etc/**
/var/workflow/models/**
/var/commerce/**
```

콘텐츠를 복사할 때 소스 환경은 신뢰할 수 있는 소스입니다.

대상 환경에서 콘텐츠를 편집하는 경우 경로가 일치하면 소스 콘텐츠가 해당 콘텐츠를 덮어씁니다.

경로가 다른 경우 소스의 콘텐츠가 대상의 콘텐츠와 병합됩니다.

### 권한 {#permissions}

콘텐츠 복사 기능을 사용하려면 사용자는 소스 및 대상 환경에서 **배포 관리자** 역할에 할당되어야 합니다.

## 콘텐츠 세트 만들기 {#create-content-set}

콘텐츠를 복사하려면 먼저 콘텐츠 세트를 정의해야 합니다. 정의되면 콘텐츠 세트를 재사용하여 콘텐츠를 복사할 수 있습니다. 콘텐츠 세트를 만들려면 다음 단계를 따르십시오.

**콘텐츠 세트를 만들려면 다음 작업을 수행하십시오.**

1. [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/)에서 Cloud Manager에 로그인한 다음 적절한 조직과 프로그램을 선택합니다.

1. 페이지의 왼쪽 상단에서 ![Show menu icon](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg)를 클릭하여 왼쪽 사이드 메뉴를 엽니다.

1. 왼쪽 메뉴의 **서비스** 페이지 아래에서 ![상자 아이콘](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Box_18_N.svg) **콘텐츠 세트**&#x200B;를 클릭합니다.

1. 페이지의 오른쪽 상단 근처에서 **콘텐츠 세트 추가**&#x200B;를 클릭합니다.

   ![콘텐츠 세트](/help/assets/content-sets.png)

1. **세부 정보** 탭의 **`Add Content Set`** 대화 상자에 있는 **이름** 및 **설명** 필드에서 콘텐츠 세트의 이름과 필요한 경우 설명을 입력한 다음 **계속**&#x200B;을 클릭합니다.

   ![콘텐츠 세트 세부 정보](/help/assets/add-content-set-details.png)

1. **경로** 텍스트 필드의 **콘텐츠 경로** 탭에서 변경될 수 있고 콘텐츠 세트에 포함되어야 하는 콘텐츠의 경로를 지정합니다.

   `/content`, `/conf`, `/etc`, `/var/workflow/models` 또는 `/var/commerce`로 시작되는 경로만 포함될 수 있습니다.

1. **![폴더 추가 아이콘](https://spectrum.adobe.com/static/icons/workflow_18/Smock_FolderAdd_18_N.svg) 경로 추가**&#x200B;를 클릭하여 경로를 콘텐츠 세트에 추가(또는 포함)합니다.

1. (선택 사항) 필요한 경우 이전 두 단계를 반복하여 추가 경로(최대 50개)를 추가합니다. 그렇지 않으면 다음 단계를 계속 진행합니다.

   ![콘텐츠 세트에 경로 추가](/help/assets/add-content-set-paths.png)

1. (선택 사항) 콘텐츠 세트를 좁히려면 포함된 콘텐츠 경로에서 제외해야 할 하위 경로를 선택적으로 지정할 수 있습니다.

   1. 제한하려는 포함된 콘텐츠 경로 오른쪽에 있는 ![폴더 삭제 아이콘](https://spectrum.adobe.com/static/icons/workflow_18/Smock_FolderDelete_18_N.svg)을 클릭합니다.
   1. 텍스트 필드에서 대화 상자에 표시된 루트 경로의 상대 경로를 입력합니다.
   1. ![폴더 삭제 아이콘](https://spectrum.adobe.com/static/icons/workflow_18/Smock_FolderDelete_18_N.svg) **경로 제외**&#x200B;를 클릭합니다.
   1. 필요한 경우 1~3단계를 반복합니다. 위에서 더 많은 제외 경로를 추가할 수 있습니다. 제한 사항이 없습니다. 그렇지 않으면 다음 단계를 계속 진행합니다.

   ![경로 제외](/help/assets/add-content-set-paths-excluded.png)

1. (선택 사항) 다음 중 하나를 수행합니다.

   1. 제외된 하위 경로 오른쪽에 있는 ![크로스 크기 500 아이콘](https://spectrum.adobe.com/static/icons/ui_18/CrossSize500.svg)을 클릭하여 삭제합니다.
   1. 포함된 콘텐츠 경로 오른쪽에 있는 ![기타 아이콘](https://spectrum.adobe.com/static/icons/ui_18/More.svg)을 클릭한 다음 **편집** 또는 **삭제**&#x200B;를 클릭합니다.

   ![경로 목록 편집](/help/assets/add-content-set-excluded-paths.png)

1. **만들기**&#x200B;를 클릭합니다. 이제 콘텐츠 세트를 사용하여 환경 간에 콘텐츠를 복사할 수 있습니다.

## 콘텐츠 세트 편집 또는 삭제 {#edit-content-set}

콘텐츠 세트를 편집할 때 구성된 경로를 확장하여 제외된 하위 경로를 표시해야 하는 경우가 있습니다.

**콘텐츠 세트 편집 또는 삭제하려면 다음 작업을 수행하십시오.**

1. [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/)에서 Cloud Manager에 로그인한 다음 적절한 조직과 프로그램을 선택합니다.

1. 페이지의 왼쪽 상단에서 ![Show menu icon](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg)를 클릭하여 왼쪽 사이드 메뉴를 엽니다.

1. 왼쪽 메뉴의 **서비스** 아래에서 ![상자 아이콘](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Box_18_N.svg) **콘텐츠 세트**&#x200B;를 클릭합니다.

1. **콘텐츠 세트** 페이지의 테이블에서 포함된 콘텐츠 경로 오른쪽에 있는 ![기타 아이콘](https://spectrum.adobe.com/static/icons/ui_18/More.svg)을 클릭한 다음 **편집** 또는 **삭제**&#x200B;를 클릭합니다.

![콘텐츠 세트 편집](/help/assets/edit-content-set.png)

## 콘텐츠 복사 {#copy-content}

콘텐츠 세트가 생성되면 이를 사용하여 콘텐츠를 복사할 수 있습니다.

다음 조건 중 하나라도 적용되는 경우 환경을 선택할 수 없습니다.

* 사용자에게 필요한 권한이 없습니다.
* 환경에서 파이프라인 또는 콘텐츠 복사 작업이 현재 실행 중입니다.

**콘텐츠를 복사하려면 다음 작업을 수행하십시오.**

1. [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/)에서 Cloud Manager에 로그인한 다음 적절한 조직과 프로그램을 선택합니다.

1. 페이지의 왼쪽 상단에서 ![Show menu icon](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg)를 클릭하여 왼쪽 사이드 메뉴를 엽니다.

1. 왼쪽 메뉴의 **서비스** 아래에서 ![상자 아이콘](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Box_18_N.svg) **콘텐츠 세트**&#x200B;를 클릭합니다.

1. 복사하려는 포함된 콘텐츠 경로 오른쪽에 있는 **콘텐츠 세트** 페이지의 테이블에서 ![기타 아이콘](https://spectrum.adobe.com/static/icons/ui_18/More.svg)을 클릭한 다음 **콘텐츠 복사**&#x200B;를 클릭합니다.

   ![콘텐츠 복사](/help/assets/copy-content.png)

1. **콘텐츠 복사** 대화 상자에서 콘텐츠 복사 액션의 **소스** 환경 및 **대상** 환경을 선택합니다.

   * 대상 환경의 지역은 소스 환경 지역의 하위 집합이어야 합니다.
   * 콘텐츠 복사 액션을 실행하기 전에 호환성 문제를 확인합니다. **대상** 환경을 선택하면 시스템이 소스 및 대상 환경의 유효성을 자동으로 검사합니다. 유효성 검사가 실패하면 프로세스가 중지되고 대화 상자에 실패 이유를 설명하는 오류 메시지가 표시됩니다.

     ![콘텐츠 복사](/help/assets/copying-content.png)

1. (선택 사항) 다음 중 하나를 수행합니다.

   1. 대상 환경에서 제외된 경로를 *유지*&#x200B;하려면 **`Do not delete exclude paths from destination`**&#x200B;을 선택합니다. 이 설정으로 콘텐츠 세트에 지정된 제외 경로가 그대로 유지됩니다.
   1. 대상 환경에서 제외된 경로를 *제거*&#x200B;하려면 **`Do not delete exclude paths from destination`**&#x200B;의 선택을 취소합니다. 이 설정으로 콘텐츠 세트에 지정된 제외된 경로가 삭제됩니다.
   1. 소스 환경에서 대상 환경으로 경로의 버전 기록을 복사하려면 **버전 복사**&#x200B;를 선택합니다. 버전 기록이 복사되지 *않으면* 콘텐츠 복사 프로세스가 훨씬 더 빨라집니다.

1. **복사**&#x200B;를 클릭합니다. 복사 프로세스의 상태는 선택한 콘텐츠 세트의 콘솔에 반영됩니다.

## 콘텐츠 복사 상태 확인 {#copy-activity}

**콘텐츠 복사 활동** 페이지에서 복사 프로세스의 상태를 모니터링할 수 있습니다.

**콘텐츠 복사 상태를 확인하려면:**

1. [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/)에서 Cloud Manager에 로그인한 다음 적절한 조직과 프로그램을 선택합니다.

1. 페이지의 왼쪽 상단에서 ![Show menu icon](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg)를 클릭하여 왼쪽 사이드 메뉴를 엽니다.

1. 왼쪽 메뉴의 **서비스** 아래에서 ![내역 아이콘](https://spectrum.adobe.com/static/icons/workflow_18/Smock_History_18_N.svg) **콘텐츠 복사 활동**&#x200B;을 클릭합니다.

   ![콘텐츠 복사 활동](/help/assets/copy-content-activity.png)

   콘텐츠 복사 프로세스는 다음 중 하나의 상태가 됩니다.

   | 상태 | 설명 |
   | --- | --- |
   | 진행 중 | 콘텐츠 복사 프로세스가 진행 중입니다. |
   | 완료됨 | 콘텐츠 복사 프로세스가 정상적으로 완료되었습니다. |
   | 실패 | 콘텐츠 복사 프로세스가 실패했습니다. |

## 콘텐츠 복사의 제한 사항 {#limitations}

* 하위 환경에서 상위 환경으로 콘텐츠 복사를 수행할 수 없습니다.
* 콘텐츠 복사는 동일한 계층 내에서만 수행할 수 있습니다. 즉, 작성자-작성자 또는 게시-게시에서 가능합니다.
* 프로그램 간 및 영역 간 콘텐츠 복사는 불가능합니다.
* 클라우드 데이터 스토어 기반 토폴로지에 대한 콘텐츠 복사는 소스 및 대상 환경이 동일한 클라우드 공급자 및 동일한 지역에 있는 경우에만 수행할 수 있습니다.
* 동일한 환경에서 동시에 콘텐츠 복사 작업을 실행할 수 없습니다.
* 대상 또는 소스 환경(예: CI/CD 파이프라인)에서 실행 중인 활성 작업이 있는 경우 콘텐츠 복사를 수행할 수 없습니다.
* 콘텐츠 복사는 소스에서 이동되거나 삭제된 콘텐츠를 추적할 수 없으므로 복제 또는 미러링 도구로 사용해서는 안 됩니다.
* 콘텐츠 복사는 시작되고 나면 일시 중지하거나 취소할 수 없습니다.
* 콘텐츠 복사는 상위 환경에서 선택한 하위 환경으로 Dynamic Media 메타데이터와 자산을 복제합니다. 이후 각각의 Dynamic Media 구성을 사용하기 위해 하위 환경에서 [DAM 프로세스 자산 워크플로](https://experienceleague.adobe.com/ko/docs/experience-manager-65/content/assets/using/assets-workflow)를 사용하여 복사된 자산을 재처리해야 합니다.
* [2GB보다 큰 크기의 자산을 사용하는 Dynamic Media 구성](https://experienceleague.adobe.com/ko/docs/experience-manager-65/content/assets/dynamic/config-dms7#optional-config-dms7-assets-larger-than-2gb)은 지원되지 않습니다.
* 대상 환경의 지역은 소스 환경 지역과 동일하거나 하위 집합이어야 합니다.

## 콘텐츠 복사의 알려진 문제 {#known-issues}

{{content-copy-known-issues}}
