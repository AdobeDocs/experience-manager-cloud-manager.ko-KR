---
title: 보안 및 개인정보 보호
description: Cloud Manager에서 코드 및 아티팩트 에셋의 보안 및 개인정보 보호에 대해 알아보십시오.
exl-id: 67df1987-8db7-40bd-9717-1bf194e957f7
source-git-commit: 200366e5db92b7ffc79b7a47ce8e7825b29b7969
workflow-type: tm+mt
source-wordcount: '202'
ht-degree: 90%

---


# 보안 및 개인정보 보호 {#security-and-privacy}

Cloud Manager에서 코드 및 아티팩트 에셋의 보안 및 개인정보 보호에 대해 알아보십시오.

## 역할 및 권한 {#roles}

[!UICONTROL Cloud Manager]에는 적절한 권한으로 미리 구성된 역할이 있습니다.

Admin Console 및 사용자 역할 권한에서 할당할 수 있는 가능한 역할에 대한 자세한 내용은 [역할 기반 권한](/help/requirements/role-based-permissions.md)을 참조하세요.

## 리소스 격리 {#resource-isolation}

[!UICONTROL Cloud Manager]에 연결된 모든 권한이 IMS 조직에 연결되므로 [!UICONTROL Cloud Manager] 고객은 인증을 위해 IMS 자격 증명이 필요합니다. 온보딩 프로세스 동안 프로비저닝 팀은 [!UICONTROL Cloud Manager]에서 리소스 격리가 수행되도록 보장합니다.

## 데이터 보안 {#data-security}

[!UICONTROL Cloud Manager]의 코드는 전송 중 암호화됩니다. Cloud Manager가 빌드하는 바이너리도 전송 중에 암호화되고 저장될 때 암호화됩니다.

각 고객은 자체 git 저장소를 갖게 되며 코드는 안전하고 다른 조직과 공유되지 않습니다.

## 데이터 개인정보 보호 {#data-privacy}

[!UICONTROL Cloud Manager]는 Adobe에서 정의한 개인정보 보호 원칙을 준수합니다. 개발자는 HTTPS를 통해 코드를 git 저장소에 안전하게 푸시합니다.

[!UICONTROL Cloud Manager]의 사용자 인터페이스는 다음과 같은 Adobe 공통 제어 프레임워크를 준수하는 서비스 위에 구축됩니다. [!UICONTROL Cloud Manager]의 사용자 인터페이스는 여러 클라우드 공급자의 보안 서비스를 사용합니다.
