---
title: 보안 및 개인 정보
seo-title: AEM Cloud Manager에 대한 보안 및 개인 정보
description: 자산의 보안 및 개인 정보(코드/객체)에 대해 알아보려면 이 페이지를 따르십시오.
seo-description: AEM Cloud Manager를 사용하는 자산(코드/객체)의 보안 및 개인 정보에 대해 알려면 이 페이지를 따르십시오.
uuid: 68bc2330-a62c-4c2c-925c-daa6788b143a
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: introduction
discoiquuid: 67a54bae-99a9-4405-91e3-9a0a8b3ccc98
feature: 시작하기
exl-id: 67df1987-8db7-40bd-9717-1bf194e957f7
source-git-commit: 43bb3c477ef9c1ce178509b8180479d7616edc66
workflow-type: tm+mt
source-wordcount: '233'
ht-degree: 3%

---

# 보안 및 개인 정보 {#security-and-privacy}

[!UICONTROL Cloud Manager] 에는 적절한 권한이 있는 미리 구성된 역할이 있습니다. 이 섹션에서는 AEM Cloud Manager를 사용하는 자산(코드/객체)의 보안 및 개인 정보 보호 기능을 중점적으로 설명합니다. 또한 [!UICONTROL Cloud Manager]에는 적절한 권한이 있는 미리 구성된 역할이 있습니다.

Admin Console 및 사용자 역할 권한에 지정할 수 있는 역할에 대해 알려면 [역할 기반 권한](/help/using/role-based-permissions.md)을 참조하십시오.


## 리소스 격리 {#resource-isolation}

[!UICONTROL Cloud Manager] 을 사용하는 고객은 [!UICONTROL Cloud Manager]에 연결된 모든 권한이 구성되고 IMS 조직에 연결되므로 인증하기 위해 IMS 자격 증명이 필요합니다. 온보딩 프로세스 중에 프로비저닝 팀은 [!UICONTROL Cloud Manager]에서 리소스 격리가 적용되도록 합니다.

## 데이터 보안 {#data-security}

[!UICONTROL Cloud Manager]의 코드가 전송 중에 암호화되어 있습니다. Cloud Manager가 빌드하는 바이너리도 전송 시 암호화되며 저장 시 암호화됩니다.

각 고객은 고유한 **Git 리포지토리**&#x200B;를 가지며 해당 코드가 안전하며 다른 **조직**&#x200B;과 공유되지 않습니다.

## 데이터 개인 정보 보호 {#data-privacy}

[!UICONTROL Cloud Manager] Adobe에 정의된 개인 정보 보호 원칙을 준수합니다. 개발자가 HTTPS를 통해 **Git 리포지토리**&#x200B;에 코드를 안전하게 푸시합니다.

[!UICONTROL Cloud Manager]에 대한 UI(사용자 인터페이스)는 Adobe에 의해 정의된 공통 제어 프레임워크를 준수하는 서비스 위에 구축됩니다. [!UICONTROL Cloud Manager]용 사용자 인터페이스는 여러 클라우드 공급자의 보안 서비스를 사용합니다.
