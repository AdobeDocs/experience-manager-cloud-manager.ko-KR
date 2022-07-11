---
title: 보안 및 개인 정보
description: Cloud Manager에서 코드 및 아티팩트 자산의 보안 및 개인 정보에 대해 알아봅니다.
exl-id: 67df1987-8db7-40bd-9717-1bf194e957f7
source-git-commit: d7751757c1d3bda3d60406a1d39cb41c61f5c863
workflow-type: tm+mt
source-wordcount: '189'
ht-degree: 3%

---


# 보안 및 개인 정보 {#security-and-privacy}

Cloud Manager에서 코드 및 아티팩트 자산의 보안 및 개인 정보에 대해 알아봅니다.

## 역할 및 권한 {#roles}

[!UICONTROL Cloud Manager] 에는 적절한 권한이 있는 미리 구성된 역할이 있습니다.

Admin Console 및 사용자 역할 권한에 지정할 수 있는 역할에 대해 알아보려면 문서를 참조하십시오 [역할 기반 권한.](/help/requirements/role-based-permissions.md)

## 리소스 격리 {#resource-isolation}

[!UICONTROL Cloud Manager] 고객은 에 연결된 모든 권한으로 인증하려면 IMS 자격 증명이 필요합니다 [!UICONTROL Cloud Manager] 는 IMS 조직에 연결되어 있습니다. 온보딩 프로세스 중에 프로비저닝 팀이 자원 격리를 [!UICONTROL Cloud Manager].

## 데이터 보안 {#data-security}

코드 입력 [!UICONTROL Cloud Manager] 는 전송 중에 암호화됩니다. Cloud Manager가 빌드하는 바이너리도 전송 시 암호화되며 저장 시 암호화됩니다.

각 고객은 고유한 Git 리포지토리를 가져오고 코드가 안전하며 다른 조직과 공유되지 않습니다.

## 데이터 개인 정보 {#data-privacy}

[!UICONTROL Cloud Manager] Adobe에 정의된 개인 정보 보호 원칙을 준수합니다. 개발자는 HTTPS를 통해 코드를 Git 저장소에 안전하게 푸시합니다.

[!UICONTROL Cloud Manager]의 사용자 인터페이스는 해당 Adobe 공통 제어 프레임워크를 준수하는 서비스 위에 구축되었습니다. [!UICONTROL Cloud Manager]의 사용자 인터페이스는 여러 클라우드 공급자의 보안 서비스를 사용합니다.
