---
title: 2021.3.0 릴리스 정보
description: Cloud Manager 릴리스 2021.3.0에 대한 정보를 보려면 이 페이지를 따르십시오
feature: Release Information
exl-id: e05b22fe-f071-4b69-9db1-e3d7ee4cfbcc
source-git-commit: 71d44c7e3673ca62fcd2203ecc0bc4ed9fa22002
workflow-type: tm+mt
source-wordcount: '231'
ht-degree: 5%

---

# 2021.3.0 릴리스 정보 {#release-notes-for}

다음 섹션에서는 다음에 대한 일반 릴리스 노트를 간략하게 설명합니다 [!UICONTROL Cloud Manager] 릴리스 2021.3.0.

## 릴리스 날짜 {#release-date}

에 대한 릴리스 날짜 [!UICONTROL Cloud Manager] 버전 2021.3.0은 2021년 3월 11일입니다.
다음 릴리스는 2021년 4월 8일에 예정되어 있습니다.

## 새로운 기능 {#whats-new}

* 새로운 코드 품질 도구 [Dispatcher 최적화 도구](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/how-to-use/custom-code-quality-rules.html?lang=en#dispatcher-optimization-tool-rules) 고객 dispatcher 구성을 확인하기 위해 가 도입되었습니다.

* 이제 사용자는 **Cloud Manager 역할 보기** 통합 셸의 사용자 프로필 아이콘(오른쪽 상단)으로 이동한 후 옵션.

* 레이블 **승인 신청** 의 레이블이 **프로덕션 승인** 더 명확해지려고

* 다음 **버전** 레이블의 레이블이 **Git 태그** 를 클릭합니다.

* 중요한 지표가 정의된 임계값을 충족하지 못할 때 동작을 정의하는 레이블을 실제 동작을 반영하도록 레이블을 재지정했습니다. **즉시 취소** 및 **즉시 승인**. 문서를 참조하십시오 [프로덕션 파이프라인 구성](configuring-production-pipelines.md) 자세한 내용

* 클래스 및 메서드 사용 중단 목록이 버전을 기준으로 업데이트되었습니다 `2021.3.4997.20210303T022849Z-210225` AEM Cloud Service SDK의 구성 요소 중 하나를 선택합니다.

## 버그 수정 {#bug-fixes}

* 패키지가 다른 패키지에 포함된 경우 일부 품질 문제가 제대로 검색되지 않았습니다.

* 경우에 따라 사용자가 파이프라인을 시작한 후 바로 파이프라인 실행 페이지에서 나가는 경우 실행이 실제로 시작되지만 작업이 실패했음을 나타내는 오류 메시지가 표시됩니다.
