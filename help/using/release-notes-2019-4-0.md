---
title: 2019.4.0 릴리스 노트
seo-title: 2019.4.0 용 AEM Cloud Manager 릴리스 노트
description: Cloud Manager 릴리스 2019.4.0에 대한 정보를 얻으려면 이 페이지를 따르십시오.
seo-description: AEM Cloud Manager 릴리스 2019.4.0에 대한 정보를 얻으려면 이 페이지를 따르십시오.
translation-type: tm+mt
source-git-commit: 8031df1c1ce9d7fee4ef33de289c6952370b7589

---


# 2019.4.0 릴리스 노트 {#release-notes-for}

[!UICONTROL Cloud Manager] 2019.4.0 릴리스에는 중요한 기능 변경 사항이 포함되지 않습니다. 자세한 내용은 아래 섹션을 참조하십시오.

## 릴리스 날짜 {#release-date}

버전 2019.4.0 릴리스 [!UICONTROL Cloud Manager] 날짜는 2019 년 4 월 18 일입니다.

## 새로운 기능 {#whats-new}

* 이제 클라우드 관리자 UI를 영어, 프랑스어, 독일어 및 일본어로 사용할 수 있습니다.
* 이제 배포 단계에 실행 중인 프로세스가 포함됩니다. 즉, 백업이 실행 중인 경우 패키지가 설치되고 로드 밸런서가 재구성됩니다.

## 버그 수정 {#bug-fixes}

* Dispatcher 변경에 사용된 배포 접근 방식이 추가 사용 사례를 처리하도록 향상되었습니다.
* 일부 인스턴스 크기 유형이 환경 페이지에 제대로 표시되지 않았습니다.
* 코드 품질 규칙 CQBP -84-dependencies는 WCM 핵심 구성 요소 및 자산 공유 Commons와 같은 포함된 Adobe 라이브러리에 대한 잘못된 양을 만들었습니다.
* 세부 사항을 사용할 수 없을 때 코드 스캐닝 단계에 대한 세부 사항 단추가 활성화되었습니다.
* 분당 페이지 뷰 수 KPI에 대해 잘못된 값을 지정할 때 오류 메시지에 잘못된 경계가 있었습니다.
* 비프로덕션 파이프라인의 배포 카테고리가 잘못 대문자 설정되었습니다.
* Git 리포지토리를 제대로 구성하지 않은 **경우 개요** 페이지의 작업 카드 호출에 텍스트가 잘못 표시되었습니다.

## 알려진 문제 {#known-issues}

* SLA 값이 잘못 반올림될 수 있습니다.