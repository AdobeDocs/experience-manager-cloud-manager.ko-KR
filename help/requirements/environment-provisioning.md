---
title: 환경 프로비저닝
description: Cloud Manager 온보딩 프로세스의 일부로 환경을 프로비저닝하는 방법에 대해 알아보십시오.
exl-id: eade4255-89b5-4c65-a498-1c6d4e8c73ff
source-git-commit: d033b7cf53d4d9faf074f1dc09e2958eb91afe3b
workflow-type: tm+mt
source-wordcount: '314'
ht-degree: 100%

---


# 환경 프로비저닝 {#environments-provisioning}

Cloud Manager 온보딩 프로세스의 일부로 환경을 프로비저닝하는 방법에 대해 알아보십시오.

## 프로비저닝 {#provisioning}

온보딩 프로세스 중에 구입한 모든 AEM 클라우드 환경은 Adobe에 의해 자동으로 프로비저닝되고 [!UICONTROL Cloud Manager]에서 해당 프로그램에 다시 연결됩니다. 이러한 AEM 클라우드 환경은 모든 Adobe Managed Services 구독으로 포함되며 일반적으로 하나 이상의 프로덕션 환경, 하나의 스테이징 환경, 선택적으로 하나 이상의 개발 또는 테스트 환경으로 구성됩니다.

## 시작 이메일 {#welcome-email}

환경 프로비저닝 프로세스가 완료되면 지정된 시스템 관리자에게 [!UICONTROL Experience Cloud]에 대한 액세스 권한이 부여되었음을 확인하는 시작 이메일이 전송됩니다. 시작 이메일에는 [!UICONTROL Experience Cloud] 서비스, [!UICONTROL AEM Managed Services] 클라우드 환경 및 [!UICONTROL Cloud Manager] 셀프서비스 포털을 시작하는 방법에 대한 자세한 정보가 포함되어 있습니다. 또한 이메일에는 고객 성공 엔지니어(CSE) 연락처 정보, 지원 리소스, 포럼, FAQ 등을 볼 수 있는 위치와 같은 중요한 정보가 포함되어 있습니다. 이메일에 제공된 리소스 목록에서 [!UICONTROL Cloud Manager]가 AEM 클라우드 환경에 액세스하는 방법에 대한 세부 정보도 얻을 수 있습니다.

## 다음 단계 {#next-steps}

시작 이메일을 수신하면 Adobe IMS 자격 증명을 사용하여 [!UICONTROL Cloud Manager]에 시스템 관리자로 로그인할 수 있습니다. 로그인하면 AEM 클라우드 프로덕션 및 비프로덕션 환경을 사용할 수 있고 성공적으로 실행 중인지 확인할 수 있습니다.

이러한 AEM 클라우드 환경은 [!UICONTROL Cloud Manager]의 git 저장소를 시작으로 스테이징 환경을 거쳐 AEM 프로덕션 환경까지 코드를 배포할 때 [!UICONTROL Cloud Manager]에서 CI/CD 파이프라인을 실행하는 데 사용됩니다. 또한 웹 속성에 대한 디지털 환경을 만들 준비가 되면 [!UICONTROL Cloud Manager]에서 직접 AEM 클라우드 환경에 액세스할 수도 있습니다.
