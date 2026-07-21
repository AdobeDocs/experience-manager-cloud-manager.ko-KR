---
title: 보안 및 개인정보 보호
description: Adobe Cloud Manager에서 코드 및 아티팩트 에셋의 보안 및 개인 정보에 대해 알아봅니다.
exl-id: 67df1987-8db7-40bd-9717-1bf194e957f7
TQID: https://experienceleague.adobe.com/mtWOzJnzV8k403LlyD9Fn9WSE5XTgjHzyVuA4j62MMg
product_v2: id: c68cd75e-5bca-4bc3-a60e-9e183f816441id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
topic_v2: id: d095671a-1355-40aa-8b5f-06c33c68080bid: f4e6943a-c91a-4134-a2c7-f4f20cfff2f0
source-git-commit: d5a34a9f6d050eaff241c0f42c9cf023cbc8036a
workflow-type: tm+mt
source-wordcount: 201
ht-degree: 26%

---

# 보안 및 개인정보 보호 {#security-and-privacy}

Adobe Cloud Manager에서 코드 및 아티팩트 에셋의 보안 및 개인 정보에 대해 알아봅니다.

## 역할 및 권한 {#roles}

Cloud Manager에는 적절한 권한이 있는 미리 구성된 역할이 있습니다.

Admin Console에서 할당할 수 있는 가능한 역할과 사용자 역할 권한에 대한 자세한 내용은 [역할 기반 권한](/help/requirements/role-based-permissions.md)을 참조하십시오.

## 리소스 격리 {#resource-isolation}

Cloud Manager에 연결된 모든 권한이 IMS 조직에 연결되므로 Cloud Manager 고객은 인증을 위해 IMS 자격 증명이 필요합니다. 온보딩 프로세스 동안 프로비저닝 팀은 Cloud Manager에서 리소스 격리가 수행되도록 보장합니다.

## 데이터 보안 {#data-security}

Cloud Manager 코드는 전송 중 암호화됩니다. Cloud Manager은 전송 중에도 암호화되고 암호화된 형식으로 저장되는 바이너리를 빌드합니다.

각 고객은 자체 Git 저장소를 갖게 되며 코드는 보호되고 다른 조직과 공유되지 않습니다.

## 데이터 개인정보 보호 {#data-privacy}

Cloud Manager은 Adobe에서 정의한 개인정보 보호 원칙을 준수합니다. 개발자는 HTTPS를 통해 코드를 Git 저장소에 안전하게 푸시합니다.

Cloud Manager의 사용자 인터페이스는 Adobe 공통 제어 프레임워크를 준수하는 서비스를 사용합니다. Cloud Manager의 사용자 인터페이스는 여러 클라우드 공급자의 보안 서비스를 사용합니다.
