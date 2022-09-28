---
title: 코드 배포
description: 코드를 배포하는 방법과 배포 시 Cloud Manager에서 어떤 일이 발생하는지 알아보십시오.
exl-id: 3d6610e5-24c2-4431-ad54-903d37f4cdb6
source-git-commit: 6572c16aea2c5d2d1032ca5b0f5d75ade65c3a19
workflow-type: ht
source-wordcount: '1609'
ht-degree: 100%

---


# 코드 배포 {#code-deployment}

코드를 배포하는 방법과 배포 시 Cloud Manager에서 어떤 일이 발생하는지 알아보십시오.

## Cloud Manager로 코드 배포 {#deploying-code-with-cloud-manager}

필요한 저장소 및 환경을 포함하여 프로덕션 파이프라인을 구성했으면 코드를 배포할 준비가 된 것입니다.

1. Cloud Manager에서 **배포**&#x200B;를 클릭하여 배포 프로세스를 시작합니다.

   ![배포 버튼](/help/assets/Deploy1.png)

1. **파이프라인 실행** 화면이 표시됩니다. **빌드**&#x200B;를 클릭하여 프로세스를 시작합니다.

   ![빌드 버튼](/help/assets/Deploy2.png)

빌드 프로세스는 다음 단계를 포함하여 코드 배포 프로세스를 시작합니다.

* 스테이지 배포
* 스테이지 테스트
* 프로덕션 배포

테스트 기준에 대한 로그를 보거나 결과를 검토하여 다양한 배포 프로세스의 단계를 검토할 수 있습니다.

## 배포 단계 {#deployment-steps}

배포의 각 단계 동안 여러 가지 작업이 수행되며, 이러한 작업은 이 섹션에서 설명합니다. 코드 자체가 백그라운드에서 어떻게 배포되는지에 대한 자세한 내용은 [배포 프로세스 세부 정보](#deployment-process) 섹션을 참조하십시오.

### 스테이지 배포 단계 {#stage-deployment}

**스테이지 배포** 단계에는 다음 작업이 포함됩니다.

* **유효성 검사**: 이 단계에서는 구성된 분기가 존재하며 환경을 사용할 수 있는지 등 현재 사용 가능한 리소스를 사용하도록 파이프라인이 구성되어 있는지 확인합니다.
* **빌드 및 단위 테스트**: 이 단계는 컨테이너화된 빌드 프로세스를 실행합니다. 자세한 내용은 [빌드 환경](/help/getting-started/build-environment.md)을 참조하십시오.
* **코드 스캔**: 이 단계에서는 애플리케이션 코드의 품질을 평가합니다. 테스트 프로세스에 대한 자세한 내용은 [테스트 결과 이해](/help/using/code-quality-testing.md) 문서를 참조하십시오.
* **스테이지 배포**

![스테이지 배포](/help/assets/Stage_Deployment1.png)

### 스테이지 테스트 단계 {#stage-testing}

**스테이지 테스트** 단계에는 다음 작업이 포함됩니다.

* **보안 테스트**: 이 단계에서는 코드가 AEM 환경에 미치는 보안 영향을 평가합니다. 테스트 프로세스에 대한 자세한 내용은 [테스트 결과 이해](/help/using/code-quality-testing.md) 문서를 참조하십시오.
   * **성능 테스트**: 이 단계에서는 코드의 성능을 평가합니다. 테스트 프로세스에 대한 자세한 내용은 [테스트 결과 이해](/help/using/code-quality-testing.md)를 참조하십시오.

   ![스테이지 테스트](/help/assets/Stage_Testing1.png)

### 프로덕션 배포 단계 {#production-deployment}

**프로덕션 배포** 단계에는 다음 작업이 포함됩니다.

* **승인 신청**
   * 이 옵션은 파이프라인을 구성하는 동안 활성화됩니다.
   * 이 옵션을 사용하면 프로덕션 배포를 예약하거나 **지금**&#x200B;을 클릭하여 프로덕션 배포를 즉시 실행할 수 있습니다.
* **프로덕션 배포 예약**
   * 이 옵션은 파이프라인을 구성하는 동안 활성화됩니다.
   * 예약된 날짜 및 시간은 사용자의 표준 시간대로 지정됩니다.
      ![배포 예약](/help/assets/Production_Deployment1.png)
* **CSE 지원**(활성화된 경우)
* **프로덕션에 배포**

![프로덕션 배포](/help/assets/Prod_Deployment1.png)

배포가 완료되면 코드가 대상 환경에 있으며 로그를 볼 수 있습니다.

![배포 완료](/help/assets/Production_Deployment2.png)

## 시간 초과 {#timeouts}

다음 단계는 사용자 피드백을 기다리는 동안 시간이 초과됩니다.

| 단계 | 시간 초과 |
|--- |--- |
| 코드 품질 테스트 | 14일 |
| 보안 테스트 | 14일 |
| 성능 테스트 | 14일 |
| 승인 신청 | 14일 |
| 프로덕션 배포 예약 | 14일 |
| CSE 지원 | 14일 |

## 배포 프로세스 세부 정보 {#deployment-process}

Cloud Manager는 빌드 프로세스에서 생성된 모든 대상/*.zip 파일을 스토리지 위치에 업로드합니다. 이러한 아티팩트는 파이프라인의 배포 단계 동안 이 위치에서 검색됩니다.

Cloud Manager가 비프로덕션 토폴로지에 배포하는 경우 가능한 한 빨리 배포를 완료하는 것이 목표이므로 다음과 같이 아티팩트가 모든 노드에 동시에 배포됩니다.

1. Cloud Manager는 각 아티팩트가 AEM 패키지인지 또는 Dispatcher 패키지인지 결정합니다.
1. Cloud Manager는 배포 중에 환경을 격리하기 위해 로드 밸런서에서 모든 Dispatcher를 제거합니다.

   * 달리 구성되지 않은 경우 개발 및 스테이징 배포에서 로드 밸런서 변경 사항(예: 개발 환경, 비프로덕션 파이프라인의 분리 및 연결 단계, 프로덕션 파이프라인 스테이징 환경)을 건너뛸 수 있습니다.

   ![로드 밸런서 건너뛰기](/help/assets/load_balancer.png)

   >[!NOTE]
   >
   >이 기능은 1-1-1 고객이 주로 사용할 것으로 예상됩니다.

1. 각 AEM 아티팩트는 Package Manager API를 통해 각 AEM 인스턴스에 배포되며, 패키지 종속성이 배포 순서를 결정합니다.

   * 패키지를 사용하여 새 기능을 설치하고 인스턴스 간에 콘텐츠를 전송하고 저장소 콘텐츠를 백업하는 방법에 대한 자세한 내용은 [패키지 관리자](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developer-tools/package-manager.html) 문서를 참조하십시오.
   >[!NOTE]
   >
   >모든 AEM 아티팩트는 작성자와 게시자 모두에게 배포됩니다. 노드별 구성이 필요한 경우 실행 모드를 활용해야 합니다. 실행 모드를 사용하여 특정 목적을 위해 AEM 인스턴스를 조정하는 방법에 대한 자세한 내용은 [AEM as a Cloud Service로 배포 문서의 실행 모드](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/deploying/overview.html#runmodes) 섹션을 참조하십시오.

1. Dispatcher 아티팩트는 다음과 같이 각 Dispatcher에 배포됩니다.

   1. 현재 구성이 백업되고 임시 위치에 복사됩니다.
   1. 변경 불가능한 파일을 제외한 모든 구성이 삭제됩니다. 자세한 내용은 [Dispatcher 구성](/help/getting-started/dispatcher-configurations.md) 문서를 참조하십시오. 이렇게 하면 디렉터리가 지워져 고립된 파일이 남지 않습니다.
   1. 아티팩트가 `httpd` 디렉터리로 추출됩니다. 변경할 수 없는 파일은 덮어쓰지 않습니다. git 저장소의 변경할 수 없는 파일에 대해 변경한 내용은 배포 시 무시됩니다. 이러한 파일은 AMS Dispatcher 프레임워크의 핵심이며 변경할 수 없습니다.
   1. Apache는 구성 테스트를 수행합니다. 오류가 발견되지 않으면 서비스가 다시 로드됩니다. 오류가 발생하는 경우 구성이 백업에서 복원되고 서비스가 다시 로드되며 오류가 Cloud Manager에 다시 보고됩니다.
   1. 파이프라인 구성에 지정된 각 경로가 무효화되거나 Dispatcher 캐시에서 플러시됩니다.

   >[!NOTE]
   >
   >Cloud Manager는 Dispatcher 아티팩트에 전체 파일 세트가 포함될 것으로 예상합니다. 모든 Dispatcher 구성 파일이 git 저장소에 있어야 합니다. 파일 또는 폴더가 없으면 배포가 실패합니다.

1. 모든 AEM 및 Dispatcher 패키지를 모든 노드에 성공적으로 배포한 후 Dispatcher가 로드 밸런서에 다시 추가되고 배포가 완료됩니다.

   >[!NOTE]
   >
   >개발 및 스테이징 배포에서 로드 밸런서 변경 사항(예: 개발 환경, 비프로덕션 파이프라인의 분리 및 연결 단계, 프로덕션 파이프라인 스테이징 환경)을 건너뛸 수 있습니다.

### 프로덕션에 배포 단계 {#deployment-production-phase}

프로덕션 토폴로지에 배포하는 프로세스는 AEM 사이트 방문자에 미치는 영향을 최소화하기 위해 약간 달라집니다.

프로덕션 배포는 일반적으로 위와 동일한 단계를 따르지만 롤링 방식으로 수행됩니다.

1. AEM 패키지를 작성자에게 배포합니다.
1. 로드 밸런서에서 dispatcher1을 분리합니다.
1. AEM 패키지를 publish1에 배포하고 동시에 Dispatcher 패키지를 dispatcher1에 배포하고 Dispatcher 캐시를 플러시합니다.
1. dispatcher1을 로드 밸런서에 다시 넣습니다.
1. dispatcher1이 다시 작동하면 로드 밸런서에서 dispatcher2를 분리합니다.
1. AEM 패키지를 publish2에 배포하고 동시에 Dispatcher 패키지를 dispatcher2에 배포하고 Dispatcher 캐시를 플러시합니다.
1. dispatcher2를 로드 밸런서에 다시 넣습니다.

이 프로세스는 배포가 토폴로지의 모든 게시자 및 dispatcher에 도달할 때까지 계속됩니다.

## 긴급 파이프라인 실행 모드 {#emergency-pipeline}

중요한 상황에서 Adobe 관리 서비스 고객은 전체 Cloud Manager 테스트 주기가 실행되기를 기다리지 않고 자신의 단계 및 프로덕션 환경에 코드 변경 사항을 배포해야 할 수 있습니다.

이러한 상황을 해결하기 위해 Cloud Manager 프로덕션 파이프라인을 긴급 모드로 실행할 수 있습니다. 이 모드를 사용하면 보안 및 성능 테스트 단계가 실행되지 않습니다. 구성된 승인 단계를 포함한 다른 모든 단계는 일반 파이프라인 실행 모드와 마찬가지로 실행됩니다.

>[!NOTE]
>
>긴급 파이프라인 실행 모드 기능은 고객 성공 엔지니어가 프로그램별로 활성화합니다.

### 긴급 파이프라인 실행 모드 사용 {#using-emergency-pipeline}

프로덕션 파이프라인 실행을 시작할 때 프로그램에 대해 긴급 파이프라인 실행 모드 기능이 활성화된 경우 대화 상자에서 일반 모드 또는 긴급 모드로 실행을 시작할 수 있습니다.

![파이프라인 옵션 실행](/help/assets/execution-emergency1.png)

긴급 모드에서 실행하는 경우 파이프라인 실행 세부 정보 페이지를 볼 때 화면 상단의 경로에는 파이프라인이 긴급 모드에서 실행 중이라는 표시기가 나타납니다.

![긴급 모드 경로](/help/assets/execution-emergency2.png)

긴급 모드에서 파이프라인을 실행하는 것은 Cloud Manager API 또는 CLI를 통해서도 가능합니다. 긴급 모드에서 실행을 시작하려면 쿼리 매개변수 `?pipelineExecutionMode=EMERGENCY` 또는 CLI를 사용하여 파이프라인의 실행 끝점에 `PUT` 요청을 제출합니다.

```
$ aio cloudmanager:pipeline:create-execution PIPELINE_ID --emergency
```

## 프로덕션 배포 재실행 {#re-execute-deployment}

프로덕션 배포 단계가 완료된 실행에 대해 프로덕션 배포 단계의 재실행을 사용할 수 있습니다. 완료 유형은 중요하지 않습니다. 배포가 성공(AMS 프로그램에만 해당), 취소 또는 실패할 수 있습니다. 주요 사용 사례는 일시적인 이유로 프로덕션 배포 단계가 실패한 경우입니다. 재실행은 동일한 파이프라인을 사용하여 새 실행을 만듭니다. 이 새로운 실행은 세 단계로 구성됩니다.

1. **유효성 검사 단계** – 기본적으로 일반 파이프라인 실행 중에 발생하는 유효성 검사와 동일합니다.
1. **빌드 단계** – 재실행의 맥락에서 빌드 단계는 실제로 새 빌드 프로세스를 실행하는 것이 아니라 아티팩트를 복사하는 것입니다.
1. **프로덕션 배포 단계** – 일반 파이프라인 실행에서 프로덕션 배포 단계와 동일한 구성 및 옵션을 사용합니다.

빌드 단계는 재빌드가 아니라 아티팩트를 복사하는 것임을 나타내기 위해 UI에 다른 레이블이 지정될 수 있습니다.

![재실행](/help/assets/Re-deploy.png)

### 제한 사항 {#limitations}

* 프로덕션 배포 단계를 재실행하는 것은 마지막 실행에서만 사용할 수 있습니다.
* 롤백 실행 또는 푸시 업데이트 실행은 재실행이 불가능합니다.
* 프로덕션 배포 단계 이전의 어느 시점에서 마지막 실행이 실패한 경우 재실행이 불가능합니다.

### 재실행 식별 {#identifying}

실행이 재실행인지 식별하기 위해 `trigger` 필드를 검사할 수 있습니다. 이 값은 `RE_EXECUTE`가 됩니다.

### 재실행 트리거 {#triggering}

재실행을 트리거하려면 프로덕션 배포 단계 상태에서 HAL 링크 `http://ns.adobe.com/adobecloud/rel/pipeline/reExecute`에 대해 `PUT` 요청을 수행해야 합니다. 이 링크가 있으면 해당 단계에서 재실행할 수 있습니다. 이 링크가 없으면 해당 단계에서 재실행할 수 없습니다. 이 링크는 프로덕션 배포 단계에만 표시됩니다.

```Javascript
 {
  "_links": {
    "http://ns.adobe.com/adobecloud/rel/pipeline/logs": {
      "href": "/api/program/4/pipeline/1/execution/953671/phase/1575676/step/2983530/logs",
      "templated": false
    },
    "http://ns.adobe.com/adobecloud/rel/pipeline/reExecute": {
      "href": "/api/program/4/pipeline/1/execution?stepId=2983530",
      "templated": false
    },
    "http://ns.adobe.com/adobecloud/rel/pipeline/metrics": {
      "href": "/api/program/4/pipeline/1/execution/953671/phase/1575676/step/2983530/metrics",
      "templated": false
    },
    "self": {
      "href": "/api/program/4/pipeline/1/execution/953671/phase/1575676/step/2983530",
      "templated": false
    }
  },
  "id": "6187842",
  "stepId": "2983530",
  "phaseId": "1575676",
  "action": "deploy",
  "environment": "weretail-global-b75-prod",
  "environmentType": "prod",
  "environmentId": "59254",
  "startedAt": "2022-01-20T14:47:41.247+0000",
  "finishedAt": "2022-01-20T15:06:19.885+0000",
  "updatedAt": "2022-01-20T15:06:20.803+0000",
  "details": {
  },
  "status": "FINISHED"
```

HAL 링크의 `href` 값 구문은 참조 지점으로 사용하기 위한 것이 아닙니다. 실제 값은 항상 HAL 링크에서 읽어야 하며 생성되지 않아야 합니다.

이 끝점에 `PUT` 요청을 제출하면 성공 시 `201` 응답이 발생하고 응답 본문은 새 실행을 나타냅니다. 이는 API를 통해 일반 실행을 시작하는 것과 유사합니다.
