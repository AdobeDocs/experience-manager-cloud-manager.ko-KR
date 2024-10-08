---
title: Git 하위 모듈 지원
description: Git 하위 모듈을 사용하여 빌드 시 Git 저장소에 있는 여러 분기의 콘텐츠를 병합할 수 있는 방법을 알아봅니다.
exl-id: f946d7e7-114a-4e33-bb82-2625d37bba2f
source-git-commit: 984269e5fe70913644d26e759fa21ccea0536bf4
workflow-type: ht
source-wordcount: '412'
ht-degree: 100%

---

# Adobe 저장소에 대한 Git 하위 모듈 지원 {#git-submodule-support}

Git 하위 모듈을 사용하여 빌드 시 Git 저장소에 있는 여러 분기의 콘텐츠를 병합할 수 있습니다.

Cloud Manager의 빌드 프로세스가 실행되면 먼저 파이프라인의 저장소를 복제하고 구성된 분기를 체크아웃합니다. 분기의 루트 디렉터리에 `.gitmodules` 파일이 있으면 명령을 실행합니다.

```
$ git submodule update --init
```

이 프로세스는 각 하위 모듈을 적절한 디렉터리로 체크아웃합니다. 이 기술은 [다중 소스 Git 저장소를 사용하여 작업](/help/managing-code/multiple-git-repos.md)에 대한 잠재적인 대안으로서 Git 하위 모듈 사용에 익숙하고 외부 병합 프로세스를 관리하고 싶지 않은 조직에 적합합니다.

예를 들어 각각 `main`이라는 단일 분기를 포함하는 3개의 저장소가 있다고 가정해 보겠습니다. “기본” 저장소, 즉 파이프라인에 구성된 저장소에서 `main` 분기에는 다른 두 저장소에 포함된 프로젝트를 선언하는 `pom.xml` 파일이 있습니다.

```xml
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
    xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/maven-v4_0_0.xsd">
    <modelVersion>4.0.0</modelVersion>
   
    <groupId>customer.group.id</groupId>
    <artifactId>customer-reactor</artifactId>
    <version>0.0.1-SNAPSHOT</version>
    <packaging>pom</packaging>
   
    <modules>
        <module>project-a</module>
        <module>project-b</module>
    </modules>
   
</project>
```

그런 다음 다른 두 저장소에 대한 하위 모듈을 추가합니다.

```shell
$ git submodule add -b main https://git.cloudmanager.adobe.com/ProgramName/projectA/ project-a
$ git submodule add -b main https://git.cloudmanager.adobe.com/ProgramName/projectB/ project-b
```

`.gitmodules` 파일의 결과는 다음과 같습니다.

```text
[submodule "project-a"]
    path = project-a
    url = https://git.cloudmanager.adobe.com/ProgramName/projectA/
    branch = main
[submodule "project-b"]
    path = project-b
    url = https://git.cloudmanager.adobe.com/ProgramName/projectB/
    branch = main
```

Git 하위 모듈에 대한 자세한 내용은 [Git 참조 설명서](https://git-scm.com/book/en/v2/Git-Tools-Submodules)에서 확인할 수 있습니다.

## 제한 사항 {#limitations}

Git 하위 모듈을 사용할 때는 다음 사항에 유의하십시오.

* Git URL은 위에서 설명한 구문과 정확히 일치해야 합니다.
* 보안상의 이유로 이러한 URL에 자격 증명을 임베드하지 마십시오.
* 분기의 루트에 있는 하위 모듈만 지원됩니다.
* Git 하위 모듈 참조는 특정 Git 커밋에 저장됩니다. 결과적으로 하위 모듈 저장소가 변경되면 참조된 커밋을 업데이트해야 합니다. 예를 들어 `git submodule update --remote`를 사용합니다.
* 달리 필요하지 않은 경우 각 하위 모듈에 대해 `git config -f .gitmodules submodule.<submodule path>.shallow true`를 실행하여 “낮은” 하위 모듈을 사용하는 것이 좋습니다.


## 비공개 저장소에 대한 Git 하위 모듈 지원 {#private-repositories}

[비공개 저장소](private-repositories.md)를 사용할 때 Git 하위 모듈에 대한 지원은 Adobe 저장소를 사용할 때와 대부분 동일합니다.

그러나 `pom.xml` 파일을 설정하고 `git submodule` 명령을 실행한 후에는 `.gitmodules` 파일을 Cloud Manager용 집계기 저장소의 루트 디렉터리에 추가하여 하위 모듈 설정을 감지해야 합니다.

![.gitmodules 파일](assets/gitmodules.png)

![집계기](assets/aggregator.png)

### 제한 사항 및 권장 사항 {#limitations-recommendations-private-repos}

비공개 저장소에 Git 하위 모듈을 사용할 때는 다음 제한 사항에 유의하십시오.

* 하위 모듈의 Git URL은 HTTPS 또는 SSH 포맷일 수 있지만 Github.com 저장소에 연결해야 합니다. Adobe 저장소 하위 모듈을 GitHub 집계기 저장소에 추가하거나 그 반대로 추가하는 것은 작동하지 않습니다.
* GitHub 하위 모듈은 Adobe GitHub 애플리케이션에 액세스할 수 있어야 합니다.
* [Adobe 관리 저장소의 Git 하위 모듈 사용 시 제한 사항](#limitations-recommendations)도 적용됩니다.
