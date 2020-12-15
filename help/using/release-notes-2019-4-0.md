---
title: 2019.4.0 릴리스 노트
seo-title: 2019.4.0용 AEM Cloud Manager 릴리스 노트
description: Cloud Manager 릴리스 2019.4.0에 대한 정보를 얻으려면 이 페이지를 따르십시오.
seo-description: AEM Cloud Manager 릴리스 2019.4.0에 대한 정보를 얻으려면 이 페이지를 따르십시오.
translation-type: tm+mt
source-git-commit: b368c46c2a9f40d0c3867db6eb2a333bd71fe22a
workflow-type: tm+mt
source-wordcount: '220'
ht-degree: 6%

---


# 2019.4.0 릴리스 노트 {#release-notes-for}

[!UICONTROL Cloud Manager] 2019.4.0 릴리스에는 중요한 기능 변경 사항이 없습니다. 자세한 내용은 아래 섹션을 참조하십시오.

## 릴리스 날짜 {#release-date}

[!UICONTROL Cloud Manager] 버전 2019.4.0의 릴리스 날짜는 2019년 4월 18일입니다.

## 새로운 기능 {#whats-new}

* Cloud Manager UI는 이제 영어, 프랑스어, 독일어 및 일본어로 제공됩니다.
* 배포 단계에는 현재 실행 중인 프로세스가 포함되어 있습니다. 즉, 백업이 실행 중일 때 패키지가 설치되고 로드 밸런서가 재구성됩니다

## 버그 수정 {#bug-fixes}

* Dispatcher 변경에 사용되는 배포 방식이 개선되어 추가 사용 사례를 처리할 수 있습니다.
* 일부 인스턴스 크기 유형이 환경 페이지에 제대로 표시되지 않았습니다.
* 코드 품질 규칙 CQBP-84-dependencies는 WCM 핵심 구성 요소 및 에셋 공유 공유물과 같은 포함된 Adobe 라이브러리에 대한 잘못된 긍지를 만들었습니다.
* 세부 정보를 사용할 수 없을 때 코드 스캔 단계의 세부 사항 단추가 활성화되었습니다.
* 분당 페이지 보기에 대해 잘못된 값을 지정할 때의 오류 메시지 KPI에 잘못된 하한 경계선이 있습니다.
* 비프로덕션 파이프라인의 배포 카테고리가 대문자로 잘못 지정되었습니다.
* git 리포지토리가 제대로 구성되지 않은 경우 **개요** 페이지의 액션 카드 호출이 잘못된 텍스트를 포함했습니다.

## 알려진 문제 {#known-issues}

* SLA 값이 잘못 반올림될 수 있습니다.
