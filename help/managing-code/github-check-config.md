---
title: 비공개 저장소에 대한 GitHub 검사 구성
description: 비공개 저장소에 대한 각각의 가져오기 요청 유효성 검사를 위해 자동으로 생성되는 파이프라인 제어 방법에 대해 알아봅니다.
exl-id: 29c9e487-e196-411a-8cda-6751b0a56066
source-git-commit: 984269e5fe70913644d26e759fa21ccea0536bf4
workflow-type: tm+mt
source-wordcount: '236'
ht-degree: 39%

---

# 개인 저장소에 대한 GitHub 구성 확인 {#github-check-config}

비공개 저장소에 대한 각각의 가져오기 요청 유효성 검사를 위해 자동으로 생성되는 파이프라인 제어 방법에 대해 알아봅니다.

## GitHub 검사 구성 {#configuration}

[개인 저장소](private-repositories.md#using)를 사용하는 경우 [전체 스택 코드 품질 파이프라인](/help/overview/ci-cd-pipelines.md)이 자동으로 만들어집니다. 이 파이프라인은 가져오기 요청이 업데이트될 때마다 시작됩니다.

`.cloudmanager/pr_pipelines.yml`비공개 저장소의 기본 분기에 파일을 만들어 이러한 검사를 제어할 수 있습니다.

```yaml
github:
  shouldDeletePreviousComment: false
pipelines:
  - type: CI_CD
    template:
      programId: 1234
      pipelineId: 456
    namePrefix: Full Stack Code Quality Pipeline for PR 
    importantMetricsFailureBehavior: CONTINUE
```

| 매개변수 | 가능한 값 | 기본값 | 설명 |
| --- | --- | --- | --- |
| `shouldDeletePreviousComment` | `true` 또는 `false` | `false` | 이 GitHub 가져오기 요청에 대한 코드 스캔 결과를 사용하여 마지막 주석만 유지할지 또는 모두 유지할지 여부입니다. |
| `type` | `CI_CD` | 해당 사항 없음 | CI/CD 파이프라인의 동작을 정의합니다. |
| `template.programID` | 정수 | 재사용되는 파이프라인 변수가 없습니다. | 각 PR에서 자동으로 만드는 기존 파이프라인에 설정된 [파이프라인 변수](/help/getting-started/build-environment.md#pipeline-variables)을(를) 다시 사용할 수 있습니다. |
| `template.pipelineID` | 정수 | 재사용되는 파이프라인 변수가 없습니다. | 각 PR에서 자동으로 만드는 기존 파이프라인에 설정된 [파이프라인 변수](/help/getting-started/build-environment.md#pipeline-variables)을(를) 다시 사용할 수 있습니다. |
| `namePrefix` | 문자열 | `Full Stack Code Quality Pipeline for PR` | 자동으로 생성되는 파이프라인의 이름을 설정하는 데 사용됩니다. |
| `importantMetricsFailureBehavior` | `CONTINUE` 또는 `FAIL` 또는 `PAUSE` | `CONTINUE` | 파이프라인의 중요한 지표 동작을 설정합니다.<br>`CONTINUE` = 중요한 지표가 실패하면 파이프라인이 자동으로 앞으로 이동합니다.<br>`FAIL` = 중요한 지표가 실패하면 파이프라인이 FAILED 상태로 끝납니다.<br>`PAUSE` = 중요한 지표가 실패하면 코드 스캔 단계에서 WAITING 상태를 받으며 수동으로 다시 시작해야 합니다. |
