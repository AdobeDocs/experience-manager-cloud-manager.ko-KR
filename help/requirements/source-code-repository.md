---
title: 소스 코드 저장소
description: Cloud Manager에서 보유하고 있는 각 프로그램에 대해 프로비저닝된 Git 저장소에 대해 알아보십시오.
exl-id: af551e33-3623-4fcd-8d25-4362d8871411
TQID: https://experienceleague.adobe.com/hdEpqKW0NluPs-w37SeLzpd-EHJNqb2nfSAMQ35man8
product_v2: id: c68cd75e-5bca-4bc3-a60e-9e183f816441id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
source-git-commit: b24e9550f11486e7ed8da31d5da27f85ad5acaf2
workflow-type: tm+mt
source-wordcount: 236
ht-degree: 44%

---

# 소스 코드 저장소 {#source-code-repository}

Cloud Manager에서 보유하고 있는 각 프로그램에 대해 프로비저닝된 Git 저장소에 대해 알아보십시오.

## Cloud Manager 저장소 {#cloud-manager-repository}

[!UICONTROL AEM Managed Services] 구독에는 Adobe에서 프로비저닝하고 관리하는 소스 코드 저장소가 포함되어 있습니다. 각 프로그램에는 연결된 코드가 저장되고 보호되는 고유한 Git 저장소가 할당됩니다.

가장 좋은 방법은 분기 구성이나 샘플 프로젝트 없이 항상 빈 상태로 제공되는 Cloud Manager Git 저장소를 사용하는 것입니다. Cloud Manager는 Git 저장소에 대한 개인 액세스 토큰을 제공하여 Git 클라이언트를 사용한 분기를 만들고 코드를 관리하고 커밋 기록을 검색하는 등의 작업을 수행할 수 있습니다.

Git에서 분기를 설정하는 방법에 대한 자세한 내용은 [릴리스 분기 구성](/help/getting-started/configuring-branches.md)을 참조하십시오.

CI/CD 파이프라인과 함께 Cloud Manager Git 저장소를 사용하는 방법에 대한 자세한 내용은 [프로덕션 파이프라인 구성](/help/using/production-pipelines.md) 및 [비프로덕션 파이프라인 구성](/help/using/non-production-pipelines.md)을 참조하십시오.

## 온-프레미스 저장소 {#on-premise-repository}

기존 Git 저장소가 있고 계속 사용하려면 여러 원격 저장소에 Git 기능을 사용하십시오. 개발은 Git 저장소에서 계속됩니다. 릴리스 분기를 프로덕션에 배포할 준비가 되면 최신 코드를 Cloud Manager Git 저장소에 푸시하고 Cloud Manager CI/CD 파이프라인을 트리거할 수 있습니다.

일반적인 Git 명령을 보려면 [Git 참조 안내서](https://education.github.com/git-cheat-sheet-education.pdf)를 참조하십시오.
