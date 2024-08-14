---
title: 프로그램 설정
description: 온보딩 후 비즈니스 소유자는 프로그램의 일부 초기 설정을 수행해야 합니다.
exl-id: 795c7112-d564-4fbf-96a1-152a6c286bf2
source-git-commit: f855fa91656e4b3806a617d61ea313a51fae13b4
workflow-type: tm+mt
source-wordcount: '582'
ht-degree: 86%

---


# 프로그램 설정 {#program-setup}

비즈니스 소유자는 온보딩 후 성능 테스트에 사용되는 프로그램 설명을 설정하고 주요 성과 지표(KPI) 정의 등 프로그램의 초기 설정을 완료합니다.

## [!UICONTROL Cloud Manager](으)로 프로그램 설정 {#program-setup-cloud-manager}

다음 단계에 따라 프로그램을 설정하고 KPI를 정의합니다.

1. [`https://my.cloudmanager.adobe.com`](https://my.cloudmanager.adobe.com)에서 Cloud Manager에 로그인한 다음 적절한 조직을 선택합니다.

1. **프로그램 설정**&#x200B;을 클릭하여 설정 프로세스를 시작합니다.

   ![프로그램 설정](/help/assets/set-up-program/setup1.png)

1. **프로그램 설정** 대화 상자에서 다음 세 가지 탭에 걸쳐 프로그램 정보를 입력할 수 있습니다.

   * **일반**
   * **KPI**
   * **프로비저닝**

1. **일반** 탭에서 **사진 변경**&#x200B;을 클릭하여 프로그램에 대한 설명을 추가하고 선택적으로 축소 이미지를 업로드합니다.

   ![일반 탭](/help/assets/Setup_Program-General.png)

1. **KPI** 탭에서 KPI를 정의합니다. 이 예에서는 별도의 KPI가 **AEM Sites** 및 **AEM Assets**&#x200B;에 대해 정의됩니다. 라이선스를 받은 제품의 KPI를 지정할 수 있습니다.

   * Cloud Manager에서 KPI를 측정하는 방법에 대한 자세한 내용은 [KPI](#kpis) 섹션을 참조하십시오.

   ![KPI 정의](/help/assets/Setup_Program-KPIs.png)

1. 프로그램에 대해 자동 크기 조정이 활성화된 경우 **프로비저닝** 탭에서 환경에 대한 주문형 크기 조정 옵션을 정의할 수 있습니다.

   * 자동 크기 조정은 프로덕션 환경에만 적용되며 일부 고객 프로그램에는 적용되지 않을 수 있습니다.

   ![프로비저닝 옵션](/help/assets/Setup_Program-Provisioning.png)

1. **저장**&#x200B;을 클릭하여 설치 마법사를 완료합니다.

프로그램이 생성됩니다. 프로그램을 사용할 준비가 되기 전에 리소스를 프로비저닝하는 데 몇 분이 걸릴 수 있습니다.

## 프로그램 편집 {#editing-program}

프로그램을 설정한 후 편집할 수 있습니다. 프로그램을 편집하려면 다음 단계를 따르십시오.

1. [`https://my.cloudmanager.adobe.com`](https://my.cloudmanager.adobe.com)에서 Cloud Manager에 로그인한 다음 적절한 조직을 선택합니다.

1. Cloud Manager 홈 화면에서 프로그램으로 이동합니다.

1. **개요** 페이지에서 프로그램을 업데이트하거나 수정하려면 **프로그램 편집**&#x200B;을 클릭하세요.

   ![프로그램 편집 옵션](/help/assets/set-up-program/edit-program1.png)

1. **프로그램 편집** 대화 상자가 표시되면 프로그램을 업데이트할 수 없습니다 사용 가능한 필드에 대한 자세한 내용은 [Cloud Manager로 프로그램 설정](#program-setup-cloud-manager) 섹션을 참조하십시오.

   ![프로그램 편집 대화 상자](/help/assets/set-up-program/edit-program-general.png)

1. 변경 내용을 저장하려면 **업데이트**&#x200B;를 클릭하세요.

변경 사항은 Cloud Manager에 즉시 저장되지만 다음 파이프라인이 실행될 때까지 사용자 환경에 반영되지 않습니다.

파이프라인을 아직 만들지 않은 경우 [프로덕션 파이프라인 구성](/help/using/production-pipelines.md) 및 [비프로덕션 파이프라인 구성](/help/using/non-production-pipelines.md) 문서를 참조하십시오.

## 프로그램 간 전환 {#swithing-programs}

프로그램에서 작업할 때 Cloud Manager 개요 페이지로 돌아가지 않고 다른 프로그램으로 빠르게 전환할 수 있습니다.

작업 표시줄을 사용하여 다른 프로그램으로 전환하거나 현재 프로그램을 편집하거나 새 프로그램을 추가합니다.

![프로그램 전환기](/help/assets/set-up-program/setup2.png)

## KPI {#kpis}

사이트 KPI는 스테이징 환경에서 실행되는 테스트에서 측정됩니다. 일반적으로 이러한 KPI는 스테이징 환경의 기능에 맞게 축소됩니다.

예를 들어 프로덕션 환경에서 분당 평균 1000페이지 뷰를 예상하고 프로덕션에 4개의 Dispatcher/퍼블리싱 서버가 있는 사용자는 이를 분당 250페이지 뷰로 확장해야 합니다. 이는 스테이징 환경이 단일 Dispatcher/퍼블리싱 서버 쌍으로만 구성된다고 가정합니다.

Assets 성능 테스트는 30분간의 테스트 기간 동안 에셋을 반복적으로 업로드하고 각 에셋과 다양한 시스템 수준 지표에 대한 처리 시간을 측정하는 방식으로 수행됩니다.

프로덕션 환경 앞에 Akamai 또는 CloudFront와 같은 콘텐츠 전송 네트워크(CDN)가 있을 수 있습니다. [!UICONTROL Cloud Manager]는 스테이징 환경에 대해 직접 테스트하므로 KPI는 CDN을 통과할 것으로 예상되는 트래픽, 즉 캐시 누락만 반영해야 합니다. 일반적으로 이는 총 생산 트래픽의 비교적 작은 부분 집합입니다.

## 비디오 개요 {#video}

>[!VIDEO](https://video.tv.adobe.com/v/26313/)
