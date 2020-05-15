---
title: 보안 및 개인 정보
seo-title: AEM Cloud Manager에 대한 보안 및 개인 정보
description: 자산(코드/객체)의 보안 및 개인 정보에 대해 알려면 이 페이지를 따르십시오.
seo-description: AEM Cloud Manager를 사용하는 자산(코드/가공물)의 보안 및 개인 정보에 대해 알려면 이 페이지를 따르십시오.
uuid: 68bc2330-a62c-4c2c-925c-daa6788b143a
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: introduction
discoiquuid: 67a54bae-99a9-4405-91e3-9a0a8b3ccc98
translation-type: tm+mt
source-git-commit: e2187565e7f06d64841eb2af9b4b1a56feb5ebe4
workflow-type: tm+mt
source-wordcount: '231'
ht-degree: 2%

---


# 보안 및 개인 정보 {#security-and-privacy}

[!UICONTROL Cloud Manager] 에 적절한 권한이 있는 사전 구성된 역할이 있습니다. 이 섹션에서는 AEM Cloud Manager를 사용하여 자산의 보안 및 개인 정보(코드/객체)를 집중적으로 설명합니다. 또한 적절한 권한이 있는 사전 구성된 역할이 [!UICONTROL Cloud Manager] 있습니다.

관리 콘솔에서 할당할 수 있는 역할 및 사용자 역할 권한에 대한 자세한 내용은 역할 기반 권한 [을 참조하십시오](/help/using/role-based-permissions.md).


## 리소스 격리 {#resource-isolation}

IMS 조직 [!UICONTROL Cloud Manager] 에 연결된 모든 권한이 구성되고 연결되어 있으므로 사용하는 고객은 IMS 자격 증명을 인증해야 [!UICONTROL Cloud Manager] 합니다. 가입 프로세스 동안 프로비저닝 팀은 리소스 격리 기능이 적용되도록 합니다 [!UICONTROL Cloud Manager].

## 데이터 보안 {#data-security}

코드 [!UICONTROL Cloud Manager] 가 전송 중에 암호화됩니다. Cloud Manager에서 빌드하는 바이너리는 전송 중에 암호화되어 저장될 때 암호화됩니다.

각 고객은 고유한 **Git 리포지토리를** 가지고 있으며 해당 코드는 안전하며 다른 **조직과 공유되지 않습니다**.

## 데이터 개인 정보 {#data-privacy}

[!UICONTROL Cloud Manager] adobe에서 정의한 개인정보 보호 원칙을 준수합니다. 개발자는 HTTPS를 통해 **Git 리포지토리로 코드를** 안전하게 푸시합니다.

UI(사용자 인터페이스) [!UICONTROL Cloud Manager] 는 Adobe에서 정의하는 일반적인 제어 프레임워크를 준수하는 서비스를 기반으로 구축됩니다. 여러 클라우드 제공업체의 보안 서비스를 [!UICONTROL Cloud Manager] 사용하는 사용자 인터페이스입니다.
